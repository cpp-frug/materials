C++17 court-circuite le constructeur de recopie
===============================================

Auteurs | [Oliver H](https://linuxfr.org/users/oliver_h), [Adrien Jeser](https://linuxfr.org/users/jeser), [lmg HS](http://linuxfr.org/users/isyfur), [Guillaume Dua](https://github.com/GuillaumeDua), [olibre](https://github.com/olibre), [Julien HENRY](https://github.com/henryju), [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [Xavier Claude](http://linuxfr.org/users/claudex), [ZeroHeure](http://linuxfr.org/users/andrianarivony), [Bruno Michel](http://linuxfr.org/users/nono) et [Nils Ratusznik](http://linuxfr.org/users/nils--2).
--------|------------------------------
License | [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)
URL     | http://linuxfr.org/news/c-17-eclipse-court-circuite-outrepasse-elide-elude-le-constructeur-par-copie
Date    | 2016-12-09
Tags    | c++17 et c++
Score   | 0

Chaque jour de décembre a droit à sa surprise. Après le [littéral hexadécimal de la virgule flottante](http://linuxfr.org/news/c-17-exprime-la-virgule-flottante-en-hexadecimal), aujourd’hui, le calendrier de l’Avent du C++ présente la spécification technique [P0135](http://wg21.link/p0135) concernant le court-circuitage par copie.



[![Une Nerdette s'électrocute en touchant la nouvelle tour C++17 de sa voisine avec garantie de court-circuitage par copie](https://cpp-frug.github.io/materials/images/nerdettes_cpp17-courtcircuite-constructeur-copie_copyright-oliverh-cc-by-sa-3.png)](https://github.com/cpp-frug/materials/blob/gh-pages/images/nerdettes_cpp17-courtcircuite-constructeur-copie_copyright-oliverh-cc-by-sa-3.png)

----

* [1ᵉʳ décembre « C++17 fixe l’ordre d’évaluation des expressions »](http://linuxfr.org/news/cpp17-fixe-l-ordre-d-evaluation-des-expressions)
* [2 décembre « C++17 indique la disponibilité des entêtes »](http://linuxfr.org/news/cpp17-indique-la-disponibilite-des-entetes-header)
* [5 décembre « C++17 branche à la compilation »](http://linuxfr.org/news/cpp17-branche-a-la-compilation-if-constexpr)
* [7 décembre « C++17 exprime la virgule flottante en hexadécimal »](http://linuxfr.org/news/c-17-exprime-la-virgule-flottante-en-hexadecimal)

----

Éclipser le constructeur par copie
==================================


La copie d’un objet peut s'avérer particulièrement coûteuse en ressources et inutile dans certains cas. C'est ainsi que depuis C++98, le standard autorise le compilateur à ne pas appeler le constructeur par copie. Cette fonctionnalité s'appelle en anglais le [*copy elision*](https://en.wikipedia.org/wiki/Copy_elision) qui en français donne l'**[élision](https://fr.wiktionary.org/wiki/%C3%A9lision) de la copie**, ou encore le **court-circuitage de la copie**.

L'[exemple suivant](http://coliru.stacked-crooked.com/a/41b0860154aa3044) construit un objet `a` par une succession de six constructeurs par copie.
GCC et Clang n'exécutent pas le constructeur par copie. Ces deux compilateurs optimisent le code même avec `-O0`. On peut forcer sa désactivation avec `-fno-elide-constructors`.
    

```cpp
#include <iostream>

struct A
{
  int i; // incrémenté à chaque copie
  A()           { i = 0; }
  A(A const& a) { i = a.i + 1; }
};

A f() { return A(A()); }

int main()
{
  A a = A( A( A( f() ) ) );
  std::cout << "a.i = " << a.i << std::endl;
}
``` 
    
Option de compilation     |&emsp;| GCC-6.2   |&emsp;| Clang-3.8
--------------------------|------|-----------|------|----------
`-std=c++98 -O0`          |&emsp;| `a.i = 0` |&emsp;| `a.i = 0`
`-fno-elide-constructors` |&emsp;| `a.i = 6` |&emsp;| `a.i = 6`
   
Le standard C++ privilégie cette optimisation quitte à ne pas respecter les opérations réalisées dans le constructeur par copie.


Cas autorisés 
=============
    
Le C++03 définit les trois cas :
     
1. Un objet temporaire utilisé pour initialiser un autre objet
--------------------------------------------------------------
     
Ci-dessous, l'objet temporaire `A()` n'est pas copié.
    
```cpp
void f (A a) {}
    
int main()
{
  f( A() );
}
``` 
    
2. Retour par valeur pour une variable sur le point de sortir de sa portée
--------------------------------------------------------------------------
    
Ce sont les fameux [_Return Value Optimization_](https://en.wikipedia.org/wiki/Return_value_optimization) (RVO) et _Named Return Value Optimization_ (NRVO) que nous pourrions traduire par :
    
* Optimisation du retour par valeur

    ```cpp
    A rvo()
    {
      return A();
    }
    
    int main()
    {
      A a = rvo();
    }
    ```
    
* Optimisation du retour par valeur à partir d'une variable nommée
    
    ```cpp
    A nrvo()
    {
      A a;
      return a;
    }
    
    int main()
    {
      A a = nrvo();
    }
    ```
    
3. Levée ou capture d'une exception par valeur
----------------------------------------------
    
_Avertissement_ : Dans ce cas, GCC ne réalise pas l'élision.
    
```cpp
void f()
{
  A a;
  throw a;
}
    
int main()
{
  try {
    f();
  } catch (A a) {
    //...
  }
}
```




Problèmatiques
==============
    
Mais ces optimisations laissées à la discrétion des compilateurs posent quelques problèmes ennuyeux. Le TS [P0135r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0135r0.html) indique que le fil de discussion sur [**ISO C++ Standard - Future Proposals**](https://groups.google.com/a/isocpp.org/forum/#!topic/std-proposals/LEzTGnc4FZo) a produit une longue liste de problématiques, dont voici les plus pertinentes.
    
TODO: Vérifier le titre de cette section :
--------------------
Le compilateur n'élide pas si l'objet n'est pas déplaçable *(movable)*
-------------------------------------------------------------------------------------------
    
Il est très difficile (voire impossible) d’écrire une [fabrique](https://fr.wikipedia.org/wiki/Fabrique_(patron_de_conception)) ou un [« constructeur nommé »](cpp.developpez.com/faq/cpp/?page=Les-constructeurs#Qu-est-ce-que-l-idiome-du-constructeur-nomme-Named-Constructor) pour les types non déplaçables.
    
```cpp
struct NonDeplacable {
    NonDeplacable()                 = default;
    NonDeplacable(NonDeplacable &&) = delete;
};

NonDeplacable make() { return /* Comment faire sans copie ? */ }
``` 
    
Un code portable est moins performant que l'élision
---------------------------------------------------
    
L'écriture d'un code portable ne peut pas se baser sur une hypothétique optimisation.
Par exemple, un développeur pourrait hésiter entre ces deux approches ci-dessous.

1. **Retour par valeur**  
   Si le compilateur n'élide pas, l'appel du constructeur par copie peut devenir pénalisante donc ce n'est pas portable.
    
    ```cpp
    A f1()
    {
      A a;
      a.data = 42;
      return a;
    }
      
    int main()
    {
      A a = f1();
    }
    ```
    
2. **Paramètre de sortie**
   Le compilateur utilise le constructeur par déplacement *(move constructor)* qui permet de limiter la casse si le compilateur n'élide pas, mais cela peut être moins performant que l'élision.
   
    ```cpp
    void f2 (A& a)
    {
      a.data = 42;
    }
    
    int main()
    {
      A a;
      f2(a);
    }
    ```
    
    
Un code portable est moins naturel
----------------------------------
    
Coder avec le retour par valeur `A f() { return A(); }` permet de porter la [sématique d'éxecution du logiciel](http://www.ulb.ac.be/di/verif/tmassart/Prog/html/chapitre14.html#definition-de-la-semantique-d-un-langage-de-programmation) et donc de mieux comprendre et maintenir ce code, mais cela nuit à la portabilité.
    
L’initialisation par inférence d'un type non déplaçable produit une erreur
--------------------------------------------------------------------------
    
Le mot-clé `auto` permet l’initialisation par inférence.
    
```cpp
struct NonDeplacable
{
  NonDeplacable()                 = default;
  NonDeplacable(NonDeplacable &&) = delete;
};
    
NonDeplacable make() { return NonDeplacable(); }
    
int main()
{
  auto x = make(); // Erreur
  return 0;
}
```




Simplifier la taxonomie pour garantir le court-circuitage
=========================================================



Afin de classer les expressions, la norme décrit une [taxonomie](https://fr.wikipedia.org/wiki/Taxonomie). Elle a connu des modifications successives. Sa simplification permet de garantir le court-circuitage, lorsque un objet temporaire est utilisé pour initialiser un autre.



```cpp
int n = 0; // compte le nombre d’appel du constructeur de copie

struct A
{
  explicit A(int) {}
  A(const A&) { ++n; }
};

int main()
{
  A a = A( A( A( A(42) ) ) );
  return n; // toujours 0 avec C++17
}           // pas de garantie avant C++17
```




Les modifications de la taxonomie
=================================



La taxonomie historique (C++98)
-------------------------------



La taxonomie de C++98 est la connue. Chaque taxon a des caractéristiques intrinsèque.



                Lvalue               |               Rvalue
-------------------------------------|------------------------------------
Objet cible de l’affectation         | Résultat des opérateurs innées (_built-in_)
Référencement                        | Beaucoup de conversion standard (qualification, type primitif…)
…                                  | …



![Taxonomie C++98](https://cpp-frug.github.io/materials/schemas/taxnomie-des-expressions/cpp98.png)
**Nota bene** : La norme définie un objet comme une zone mémoire pouvant contenir des données.



### Ajout des xvalues (C++11)
![Taxonomie C++98](https://cpp-frug.github.io/materials/schemas/taxnomie-des-expressions/cpp11.png)



TODO: Expliquer la section class.copy du C++11



Sources
=======



- [Brouillon de travail C++98.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1905.pdf)
- [Brouillon de travail C++11.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3376.pdf)
- [C++, "copy elision" et copy-initialization](http://lefauxplat.blogspot.fr/2014/01/c-copy-elision-et-copy-initialization.html) 
- [Guaranteed Copy Elision](https://jonasdevlieghere.com/guaranteed-copy-elision/)



Réutilisation
=============
    
Le texte de cette dépêche est protégé par ~~le [droit d’auteur](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diﬀusion)~~ la [gauche d’auteur](https://fr.wikipedia.org/wiki/Gauche_d'auteur) et réutilisable sous licence [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr). Les images utilisées sont aussi sous licence libre (cliquer sur l’image pour plus de détails).
    
Donc n’hésitez pas à réutiliser ce contenu libre pour créer, par exemple, des supports de formation, des présentations _(Meetups)_, des publications sur d’autres blogs, des articles pour des magazines, et aussi un article C++17 sur Wikipédia dès que [Wikipédia utilisera la licence CC BY-SA-4.0](https://meta.wikimedia.org/wiki/Terms_of_use/Creative_Commons_4.0). &emsp; **٩(•‿•)۶**
    

Les auteurs
===========
    
Par respect de la licence, merci de [créditer](https://fr.wiktionary.org/wiki/cr%C3%A9diter#Verbe) les nombreux auteurs :
    
* Les principaux auteurs sont [Adrien Jeser](https://linuxfr.org/users/jeser), [lmg HS](http://linuxfr.org/users/isyfur) et [Oliver H](https://linuxfr.org/users/oliver_h) ;
* Les nombreux autres contributeurs ayant contribué sur l'ancêtre de cette dépêche ou sur le [dépôt Git](https://github.com/cpp-frug/materials) sont [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [olibre](https://github.com/olibre) et [Guss](https://github.com/GuillaumeDua).
    


Continuer à améliorer ce document
=================================
    
Malgré tout le soin apporté, il reste certainement des oublis, des ambiguïtés, des fôtes… Bien que cette dépêche restera figée sur le site *LinuxFr.org*, il est possible de continuer à l’enrichir sur le [dépôt Git](https://github.com/cpp-frug/materials/blob/gh-pages/news/README.md) du [**Groupe des Utilisateurs C++ Francophone**](http://linuxfr.org/news/douzieme-rencontre-parisienne-c-mercredi-27-avril-2016#historique-des-rencontres-c-francophones) (C++FRUG). C’est donc sur ce dépôt que se trouve les versions les plus à jour. &emsp; **(ღ˘⌣˘ღ)**

Appel à contribution
====================
    
Nous nous efforçons de vous fournir une dépêche de qualité chaque jour ouvré. Et en plus, avec une illustration sympathique. Mais cela demande beaucoup de travail, et tenir les délais n’est pas toujours simple.
    
Merci de nous donner un coup de main, que ce soit sur la correction orthographique, le dessin, la lecture des spécifications techniques, la rédaction d’une nouvelle dépêche à intégrer au calendrier de l’Avent du C++. Tu peux aussi apporter ta contribution à la dépêche [*« Faut-il continuer à apprendre le C++ ? »*](https://linuxfr.org/news/faut-il-continuer-a-apprendre-le-c).
    
Rejoins-nous sur la [page du groupe de travail C++](https://linuxfr.org/redaction/news/groupe-de-travail-depeches-c-17) sur _LinuxFr.org_ (un [compte](https://linuxfr.org/compte/inscription) est nécessaire pour y accéder).
    
À suivre…
