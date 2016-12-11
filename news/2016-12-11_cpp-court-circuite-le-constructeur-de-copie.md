C++ se court-circuite le constructeur de copie
==============================================

Auteurs | [Oliver H](https://linuxfr.org/users/oliver_h), [Adrien Jeser](https://linuxfr.org/users/jeser), [lmg HS](http://linuxfr.org/users/isyfur), [Guillaume Dua](https://github.com/GuillaumeDua), [olibre](https://github.com/olibre), [Julien HENRY](https://github.com/henryju), [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [Xavier Claude](http://linuxfr.org/users/claudex), [ZeroHeure](http://linuxfr.org/users/andrianarivony), [Bruno Michel](http://linuxfr.org/users/nono) et [Nils Ratusznik](http://linuxfr.org/users/nils--2).
--------|------------------------------
License | [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)
URL     | http://linuxfr.org/news/cpp-se-court-circuite-le-constructeur-de-copie
Date    | 2016-12-11
Tags    | c++17 et c++
Score   | 20


Le calendrier de l’Avent du C++ continue. Après quelques trous dans le calendrier, aujourd’hui une nouvelle surprise : le **court-circuit du constructeur de copie**.



Cette fonctionnalité est présente dans le C++ depuis la nuit des temps et pourtant peu connue, alors que ses effets de bords peuvent être redoutables. Cette dépêche très pédagogique explique tous les détails d’une optimisation ultime.


[![Une nerd s’électrocute en touchant la vieille tour C++ de sa voisine à cause des effets de bords du court-circuit du constructeur de copie (C++98 copy elision)](https://cpp-frug.github.io/materials/images/nerd_cpp98_court-circuit_ctor_copie.gif)](https://github.com/cpp-frug/materials/blob/gh-pages/images/nerd_cpp98_court-circuit_ctor_copie.gif)

----

* [1ᵉʳ décembre « C++17 fixe l’ordre d’évaluation des expressions »](http://linuxfr.org/news/cpp17-fixe-l-ordre-d-evaluation-des-expressions)
* [2 décembre « C++17 indique la disponibilité des entêtes »](http://linuxfr.org/news/cpp17-indique-la-disponibilite-des-entetes-header)
* [5 décembre « C++17 branche à la compilation »](http://linuxfr.org/news/cpp17-branche-a-la-compilation-if-constexpr)
* [7 décembre « C++17 exprime la virgule flottante en hexadécimal »](http://linuxfr.org/news/cpp17-exprime-la-virgule-flottante-en-hexadecimal)

----

Terminologie
============
 


Cette dépêche contient des mots français peu utilisées au quotidien. Ces mots sont le résultat de la traduction des termes du standard C++. Pour ne pas être trop perdu, un petit tour de la signification spécifique à cette dépêche.



Élision
-------
 


* **« [élision](https://fr.wiktionary.org/wiki/élision) du constructeur de copie »** : traduction de l’anglais **« copy [elision](https://en.wiktionary.org/wiki/elision) »** qui est une optimisation évitant de passer par le constructeur de copie ;
* [**“élider”**](https://fr.wiktionary.org/wiki/élider) : en anglais [***“elide”***](https://en.wiktionary.org/wiki/elide#English), supprimer le constructeur de copie ;
* [**“éluder”**](https://fr.wiktionary.org/wiki/éluder) : éviter avec adresse le constructeur de copie, éclipser, court-circuiter, outrepasser, contourner.


Cette dépêche n’utilise pas **“éluder”**, mais **“élider”** car l’orthographe est proche du terme anglais **“elide”**.


Constructeur de copie
---------------------
    
Cette dépêche utilise la traduction **« constructeur de copie »** pour l’expression anglaise **« copy constructor »**. D’autres documents en français utilisent des traductions sensiblement différentes :
    
* « constructeur **par copie** » ;
* « constructeur **de recopie** » ;
* « constructeur **par recopie** ».
    
Les auteurs de cette dépêche ont opté pour l’expression **« constructeur de copie »** car sémantiquement le mot **“de”** *identifie*, alors que le mot **“par”** *décrit*. Et car l’orthographe de **“copie”** est plus proche de l’anglais **“copy”** (un peu comme choisir [**“paquet”**](https://fr.wiktionary.org/wiki/paquet) au lieu de [**“paquetage”**](https://fr.wiktionary.org/wiki/paquetage) pour traduire [**“package”**](https://en.wiktionary.org/wiki/package) en [informatique](https://fr.wikipedia.org/wiki/Paquet_(logiciel))). Il en est de même pour **« constructeur de déplacement »**.


Si vous souhaitez apporter vos idées sur la traduction, merci de vos commentaires constructifs (par copie) ;-)


Le constructeur de copie peut être coûteux
==========================================


Lors des appels et retours de fonctions, il arrive qu’un objet temporaire soit créé, avant d’être copié à son emplacement mémoire définitif. Cette approche consomme inutilement des ressources (mémoire, temps d’exécution).


```cpp
struct GrosseStructure
{
  // ... des attributs volumineux
  // et des références vers d'autres objets
};
    
GrosseStructure f()
{
  GrosseStructure immense;
  // ...
    
  // Copie de l'objet immense
  // par retour de fonction
  return immense;
}
    
void g (GrosseStructure arg)
{
  // ...
}
    
int main()
{
  // Copie d'un objet temporaire
  // dans l'appel de fonction g()
  g( f() );
}
```



Élider le constructeur de copie
==================================
    
Dans certains cas, il est possible d’éviter la copie, en créant directement l’objet à son emplacement de destination final. Le C++98 autorise le compilateur à faire une telle optimisation.


L’[exemple suivant](http://coliru.stacked-crooked.com/a/41b0860154aa3044) construit un objet `a` par une succession de six constructeurs de copie.
GCC et Clang n’exécutent pas le constructeur de copie. Ces deux compilateurs optimisent le code, même avec l’option `-O0` (qui signifie pourtant [« pas d’optimisation »](http://clang.llvm.org/docs/CommandGuide/clang.html)). Cette optimisation est quand même désactivée avec `-fno-elide-constructors`.


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



Explications
============
    
Dans l’exemple précédent, la fonction `f()` crée un objet temporaire `A`. Le compilateur élide le constructeur de copie et crée cet objet `A` directement dans la [pile d’appel](https://fr.wikipedia.org/wiki/Pile_d%27exécution) *(call stack)* de la fonction appelante `main()`.
    
Le compilateur court-circuite autant de fois que nécessaire. Cette optimisation s’applique aussi à l’initialisation de copie [*(copy initialization)*](http://en.cppreference.com/w/cpp/language/copy_initialization). Ainsi l’objet temporaire retourné par la fonction `f()` est directement construit dans `a`. Et cela indépendamment de l’[extension inline](https://fr.wikipedia.org/wiki/Extension_inline). C’est-à-dire que le corps de la fonction `f()` aurait pu se trouver dans une bibliothèque à part.
    
Plus généralement, et contrairement au langage C, le standard C++ autorise le compilateur à effectuer toutes les optimisations possibles du moment que le résultat soit conforme à celui attendu par le code source. Et l’élision du constructeur de copie va plus loin, car le standard C++ part du principe que les développeur code le constructeur de copie pour faire la même chose que les autres constructeurs, le résultat des constructeurs se valent. Le compilateur ne vérifie pas si le corps des différents constructeurs font la même chose (se serait trop compliqué).
    
**Avertissement :** Le standard C++ privilégie cette optimisation, quitte à ne pas exécuter les instructions du constructeur de copie. Si ton constructeur de copie réalise des opérations particulières parce que tu es certain qu’il sera forcément appelé avec `A(A())`, alors le compilateur risque de te faire tourner en bourrique !

Et le constructeur de déplacement ?
===================================
        
Le compilateur remplace le **constructeur de copie** par le **constructeur de déplacement** quand cela est possible. Par contre, généralement, le compilateur préfère élider le constructeur de copie quand cela est possible, donc ne pas utiliser le constructeur par déplacement.
    
Nous pouvons nous poser la même question pour les opérateurs d’affectation de copie et de déplacement. Donc, expérimentons un peu plus en [généralisant le précédent exemple](http://coliru.stacked-crooked.com/a/1e4d3eb384f10982) :

```cpp
#include <iostream>
    
int t[6] = { 0, 0, 0, 0, 0, 0 };
    
struct A
{
  A()                    { ++t[0]; }
  A(A const&)            { ++t[1]; }
  A& operator=(A const&) { ++t[2]; return *this; }
#if __cplusplus > 201100
  A(A &&)                { ++t[3]; }
  A& operator=(A &&)     { ++t[4]; return *this; }
#endif
  ~A()                   { ++t[5]; }
};
    
A f() { return A( A() ); }
    
int main()
{
  { A a = A( A( A( f() ) ) ); }
    
  std::cout << "Dflt = " << t[0] << "\n"
               "Copy = " << t[1] << "\n"
               "CpAs = " << t[2] << "\n"
#if __cplusplus > 201100
               "Move = " << t[3] << "\n"
               "MvAs = " << t[4] << "\n"
#endif
               "Dtor = " << t[5] << '\n';
}
```



Quatre tests produisent le résultat **Élision** :
    
    g++ -std=c++98  ; clang++ -std=c++98
    g++ -std=c++11  ; clang++ -std=c++11
    
Deux tests produisent le résultat **C++98** :
    
    g++     -std=c++98 -fno-elide-constructors
    clang++ -std=c++98 -fno-elide-constructors
    
Deux tests produisent le résultat **C++11** :
    
    g++     -std=c++11 -fno-elide-constructors
    clang++ -std=c++11 -fno-elide-constructors
    
Résultats                                     | Élision | C++98 | C++11
----------------------------------------------|---------|-------|---
`Dflt` Constructeur par défaut                |   1     | 1     | 1
`Copy` Constructeur de copie                  |   -     | 6     | -
`CpAs` Opérateur d'affectation de copie       |   -     | -     | -
`Move` Constructeur de déplacement            |   -     | -     | 6
`MvAs` Opérateur d'affectation de déplacement |   -     | -     | -
`Dtor` Destructeur                            |   1     | 7     | 7


Cas autorisés 
=============
    
Le standard C++11 définit les trois cas suivants pour lesquels le compilateur peut élider le constructeur de copie.


Cas 1 – Un objet temporaire utilisé pour initialiser un autre objet
--------------------------------------------------------------
     
Ci-dessous, l’objet temporaire `A()` peut bénéficier de l’élision. Dans ce cas, le constructeur par défaut `A()` crée l’argument `a` directement sur la pile d’appel de la fonction `f()`.
    
```cpp
void f (A a) {}
    
int main()
{
  f( A() );
} // ^--- objet temporaire
``` 
    
Donc l’objet temporaire n’est pas copié, mais directement créé à l’emplacement mémoire de destination, comme si le constructeur de copie avait été appelé.

Cas 2 – Retour par valeur pour une variable sur le point de sortir de sa portée
--------------------------------------------------------------------------
    
Ce sont les fameux [__« Return Value Optimization »__](https://en.wikipedia.org/wiki/Return_value_optimization) (RVO) et __« Named Return Value Optimization »__ (NRVO) que nous pourrions traduire par :
    
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
    
* Optimisation du retour par valeur à partir d’une variable nommée
    
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

Cas 3 – Levée ou capture d’une exception par valeur
----------------------------------------------
    
__Note :__ Dans ce cas, GCC ne réalise pas l’élision. Ce n’est pas parce que le standard l’autorise que les compilateurs doivent l’implémenter. Et ce n’est pas parce que le standard C++98 a normalisé cette pratique que les compilateurs le faisaient depuis les années 90. Les compilateurs les plus populaires ont progressivement implémenté ces optimisations au fur des années.
    
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
    //…
  }
}
```



Problématiques
==============
    
Ces optimisations laissées à la discrétion des compilateurs posent quelques problèmes ennuyeux. Le TS [P0135r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0135r0.html) indique que le [fil de discussion sur **ISO C++ Future Proposals**](https://groups.google.com/a/isocpp.org/forum/#!topic/std-proposals/LEzTGnc4FZo) a produit une longue liste des inconvénients. Ces inconvénients découlent de la formulation actuelle du standard C++ à propos de cette élision. Les améliorations effectuées entre C++98 et C++14 n’ont pas supprimés ces inconvénients. Voici trois inconvénients parmi les plus notables :


Inconvénient 1 - Type indéplaçable
----------------------------------
    
Le code qui exploite l’élision se heurte aux types indéplaçables. Dans l’[exemple suivant](https://godbolt.org/g/DmSuhn), la fonction `f()` retourne un objet par valeur. Le compilateur sait qu’il peut élider le constructeur de copie, et que le constructeur de déplacement ne lui est pas utile. Le développeur sait que le compilateur peut le faire. Tous, humains et logiciels sont d’accord pour dire que ce code est possible.
**Mais pas le standard !**


```cpp
struct NonDeplacable
{
  NonDeplacable()                     = default;
  NonDeplacable(NonDeplacable const&) = default;
  NonDeplacable(NonDeplacable &&)     = delete;
};  // ^-- pas de constructeur de déplacement
    
NonDeplacable f()
{
  return NonDeplacable();
  // Clang-3.9 error: call to deleted constructor of 'NonDeplacable'
  // GCC-7     error: use of deleted function 'NonDeplacable::NonDeplacable(NonDeplacable&&)'
}
    
int main()
{
  NonDeplacable x = f();
}
```



Pour rappel, cette optimisation est optionnelle. Et donc, le standard C++ en interdisant l’élision dans ce cas, évite du code C++ “valide” qui ne puisse pas être compilé par les compilateurs ne sachant pas élider.  
    
Cette situation rend très difficile (voire impossible) l’implémentation d’une [fabrique](https://fr.wikipedia.org/wiki/Fabrique_(patron_de_conception)) ou d’un [constructeur nommé](cpp.developpez.com/faq/cpp/?page=Les-constructeurs#Qu-est-ce-que-l-idiome-du-constructeur-nomme-Named-Constructor) pour les types non déplaçables.
    
De plus, le standard ne permet pas non plus l’[initialisation par inférence](https://fr.wikipedia.org/wiki/C%2B%2B11#Inf.C3.A9rence_de_types) des objets non déplaçables, c’est-à-dire avec le mot-clé `auto`. Alors que Herb Sutter, [animateur en chef](https://isocpp.org/std/the-committee "Convener") du comité de standardisation du C++, préconise de recourir, le plus souvent, au mot-clé `auto`.

```cpp
int main()
{
  auto x = f(); // Erreur
}
``` 


Inconvénient 2 - Un code portable est moins performant que l’élision
--------------------------------------------------------------------
    
L’écriture d’un code portable ne peut pas se baser sur une hypothétique optimisation, d’autant plus si la construction de copie présente des effets de bords, chose peu recommandable de fait. Par exemple, un développeur pourrait hésiter entre ces deux approches ci-dessous.

### 2.1. Retour par valeur
    
Si le compilateur n’élide pas, l’appel du constructeur de copie peut devenir pénalisant donc ce n’est pas portable (pour des questions de performance).
    
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




Heureusement, le C++11 prend le relai et impose que la valeur retournée soit non pas copiée, mais déplacée. Si l’objet occupe plus de mémoire que ce que son `sizeof` va retourner (cas des chaînes, des vecteurs, etc), alors déplacer va faire une différence : on gagne une copie, et ce n’est pas négligeable. En revanche, si l’objet est simple et que son `sizeof` compte vraiment toute l’information qu’il représente (comme un quaternion), déplacer va coûter aussi cher que copier.


### 2.2. Paramètre de sortie
    
Le compilateur écrit directement dans la donnée préalablement construite par l’appelant. Cela permet de limiter la casse si le compilateur n’élide pas, mais cela peut être moins performant que l’élision. 
    
```cpp
void f2 (A& a)
{
  a.data = 42; // on écrit directement dedans
    
  // ou on déplace par affectation b dans a
  A b;
  a = std::move(b);
}
    
int main()
{
  A a;
  f2(a);
}
``` 
    
Cette technique présente à la fois des avantages et des inconvénients. Elle est très dépendante du contexte.
    
D’un côté, le compilateur ne saura plus résoudre correctement les problèmes d’_aliasing_ sur des fonctions non `inline`.
    
De l’autre, on évite de construire un `A` à chaque appel. Si `A` est un gros objet, un `vector<>` par exemple, même avec l’élision, à chaque appel on construit et on libère un objet `A`. L’approche du paramètre sortant `f2(A&a)` peut à la place redimensionner ce `vector<>` et le remplir ensuite. Un code appelant `f2(A&a)` en boucle permet d’économiser des millions d’allocations et de libérations, l’objet `A` étant alors un cache extérieur. Les gains réalisés ainsi sont intéressants.


Inconvénient 3 - Un code portable est moins naturel
---------------------------------------------------
    
C’est le point le plus important de cette dépêche, l’intérêt d’écrire `A f1()` plutôt que `void f1(A& out)`. Mais pourquoi donc cette dépêche s’obstine à vouloir écrire `A f1()` alors que `void f1(A& out)` fait très bien l’affaire ?
    
&emsp; &emsp; **Car utiliser `A f1()` est bien plus naturel !**
    
En mathématiques, nous écrivons `y = f(x)`, c’est naturel, notre cerveau est habitué à penser comme cela. Alors pourquoi on devrait écrire `f(x_in,y_out)` ?
    
**Réponse :** Le développeurs sont priés d’écrire `f(x_in,y_out)` car `y = f(x)` n’est pas portable (pour les raisons évoquées sur les points précédents).
    
Ce serait bien de pouvoir coder avec le retour par valeur `A f() { return A(); }` afin de porter la [sématique d’éxecution du logiciel](http://www.ulb.ac.be/di/verif/tmassart/Prog/html/chapitre14.html#definition-de-la-semantique-d-un-langage-de-programmation) et donc de mieux comprendre et maintenir le code source, non ?


Conclusion
==========
    
Cette dépêche présente une optimisation intéressante permise par le standard C++, mais qui malheureusement n’est pas vraiment exploitée.
    
Alors que faire pour résoudre tous ces inconvénients et démocratiser les possibilités de code offertes par l’élision du constructeur de copie ?
    
Réponse surprise dans la prochaine dépêche :-)



Réutilisation
=============
    
Le texte de cette dépêche est protégé par ~~le [droit d’auteur](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diﬀusion)~~ la [gauche d’auteur](https://fr.wikipedia.org/wiki/Gauche_d'auteur) et réutilisable sous licence [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr). Les images utilisées sont aussi sous licence libre (cliquer sur l’image pour plus de détails).
    
Donc n’hésitez pas à réutiliser ce contenu libre pour créer, par exemple, des supports de formation, des présentations _(Meetups)_, des publications sur d’autres blogs, des articles pour des magazines, et aussi un article C++17 sur Wikipédia dès que [Wikipédia utilisera la licence CC BY-SA-4.0](https://meta.wikimedia.org/wiki/Terms_of_use/Creative_Commons_4.0). &emsp; **٩(•‿•)۶**
    



Les auteurs
===========
    
Par respect de la licence, merci de [créditer](https://fr.wiktionary.org/wiki/cr%C3%A9diter#Verbe) les nombreux auteurs :
    
* Les principaux auteurs sont [Adrien Jeser](https://linuxfr.org/users/jeser), [lmg HS](http://linuxfr.org/users/isyfur), [gbdivers](https://linuxfr.org/users/gbdivers) et [Oliver H](https://linuxfr.org/users/oliver_h) ;
* Les nombreux autres contributeurs ayant contribué sur l’ancêtre de cette dépêche ou sur le [dépôt Git](https://github.com/cpp-frug/materials) sont [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [olibre](https://github.com/olibre) et [Guss](https://github.com/GuillaumeDua).
    



Continuer à améliorer ce document
=================================
    
Malgré tout le soin apporté, il reste certainement des oublis, des ambiguïtés, des fôtes… Bien que cette dépêche restera figée sur le site *LinuxFr.org*, il est possible de continuer à l’enrichir sur le [dépôt Git](https://github.com/cpp-frug/materials/blob/gh-pages/news/README.md) du [**Groupe des Utilisateurs C++ Francophone**](http://linuxfr.org/news/douzieme-rencontre-parisienne-c-mercredi-27-avril-2016#historique-des-rencontres-c-francophones) (C++FRUG). C’est donc sur ce dépôt que se trouve les versions les plus à jour. &emsp; **(ღ˘⌣˘ღ)**



Appel à contribution
====================
    
Nous nous efforçons de vous fournir une dépêche de qualité chaque jour ouvré. Et en plus, avec une illustration sympathique. Mais cela demande beaucoup de travail, et tenir les délais n’est pas toujours simple.
    
Merci de nous donner un coup de main, que ce soit sur la correction orthographique, le dessin, la lecture des spécifications techniques, la rédaction d’une nouvelle dépêche à intégrer au calendrier de l’Avent du C++. Tu peux aussi apporter ta contribution à la dépêche [*« Faut-il continuer à apprendre le C++ ? »*](https://linuxfr.org/news/faut-il-continuer-a-apprendre-le-c).
    
Rejoins-nous sur la [page du groupe de travail C++](https://linuxfr.org/redaction/news/groupe-de-travail-depeches-c-17) sur _LinuxFr.org_ (un [compte](https://linuxfr.org/compte/inscription) est nécessaire pour y accéder).
    
À suivre…
