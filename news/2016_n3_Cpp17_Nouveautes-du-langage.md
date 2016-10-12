| Pour contribuer à ce document, merci de lire le [`README.md`](README.md)
|-------------------------------------------------------------------------


Nouveautés C++17 au niveau du langage
=====================================

Auteurs | Oliver H, olibre, Benoît Sibaud, Lucas, cracky, Martin Peres, RyDroid, Adrien Jeser, gorbal, Storm, palm123, khivapia et Segfault
--------|------------------------------
License | [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)
URL     | https://linuxfr.org/news/nouveautes-c-17-au-niveau-du-langage
Date    | 2016-07-22T00:53:12+02:00
Tags    | cpp, c++17 et c++
Score   |   0

L'ajout des fonctionnalités au **C++17** a été clôturé. Cette troisième dépêche se concentre sur les changements au niveau du langage C++. Faisons donc le tour des nouveautés :-)
    
![C++17 à l'école primaire](https://cpp-frug.github.io/materials/images/cpp-ecole-primaire_copyright-Ziyue-OliverH-2016_CC-BY-SA-3.jpg)

----

* [La précédente dépêche "C++17, Genèse d'une version mineure"](https://linuxfr.org/redaction/news/c-17-genese-d-une-version-mineure)
* [Contenu markdown de cette dépêche sur le dépôt C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md)
* [Journal "C++17 est sur les rails" par rewind a propos de la réunion du comité en mars 2016](https://linuxfr.org/users/rewind/journaux/c-17-est-sur-les-rails)
* [Réunion du comité en mars 2016 racontée par Herb Sutter](https://isocpp.org/blog/2016/03/trip-report-jax-sutter)
* [Réunion du comité en juin 2016 racontée par Herb Sutter](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/)
* [Réunion du comité en mars 2016 détaillée par botondballo](https://botondballo.wordpress.com/2016/03/21/trip-report-c-standards-meeting-in-jacksonville-february-2016/)
* [Liste très complète des nouveautés C++17 sur StackOverflow.com](http://stackoverflow.com/a/38060437/938111)
* [Liste des nouveautés C++17 sur Meeting C++](https://meetingcpp.com/index.php/br/items/final-features)
* [Dépôts Git du comité de standardisation ISO C++](https://github.com/cplusplus))
* [Article Wikipédia C++17](https://en.wikipedia.org/wiki/C%2B%2B17)

----

![Illustration C++ de Dominic Alves sous license CC-BY-SA 2.0](https://c2.staticflickr.com/2/1116/785982209_b0da7b4380_o.jpg)


Série de dépêches C++
=====================
    
Cette dépêche LinuxFr.org est figée après publication. Par contre, la corriger, la  compléter est possible sur [le dépôt Git C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md). Ainsi la mise en commun des contributions individuelles permet de l'enrichissement mutuel et la réutilisation d'un contenu libre (CC-BY-SA) pour créer, par exemple, un article Wikipédia C++17 en français.
    
Résumé des dépêches pour les décideurs pressés :

1. Les coulisses du C++
-----------------------
    
La spécification C++ n'est pas libre et [son téléchargement coûte 180 €](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=64029). Alors, les développeurs C++ utilisent un [brouillon _(draft)_ gratuit](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf). Par contre, le C++ est bien un [standard ouvert](https://fr.wikipedia.org/wiki/Format_ouvert) : pas de brevets logiciels ni de propriété intellectuelle. Mais de toutes façons, la plupart des développeurs C++, même expérimentés, n'ont jamais lu le standard. Car ce sont surtout [des livres](https://fr.wikipedia.org/wiki/The_C%2B%2B_Programming_Language) et plus récemment des [sites](http://fr.cppreference.com/) qui sont utilisés.


2. Genèse du C++17
------------------
    
Les deux réunions du comité de standardisation C++ pour définir le périmètre fonctionnel du prochain C++17.

3. Changements C++17 au niveau du langage
-----------------------------------------
    
Nettoyage, correction, évolution, sucre syntaxique :
    
* [Déduction des arguments `template` lors de la déclaration](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html) pour ne pas avoir besoin des fonctions d'aide `make_*()` ;
* [Déstructuration du retour de fonction](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r2.html) `char x; int y; std::tie(x,y) = fonction();` ~~> `auto [ x, y ] = fonction();` ;
* [`template<auto>`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r1.html) pour éviter la redondance `decltype(variable)` dans `MaClasse<decltype(variable),variable>` ;
* [`namespace` imbriqué](http://en.cppreference.com/w/cpp/language/namespace) `namespace aaa { namespace bbb { ... } }` --> `namespace aaa::bbb { ... }` ;
* [`if constexpr`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0128r1.html) pour sélectionner du code à la compilation (peut remplacer `#if` dans certains cas) ;
* Lambda `constexpr` et pouvant capturer `*this` ;
* [`if(init;condition)` et `switch(init;condition)`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r0.html) pour faire un peu comme `for(init;cond;inc)` ;
* [Variables `inline`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r0.pdf) (après les [variables `template`](http://en.cppreference.com/w/cpp/language/variable_template) du C++14) ;
* ...

Par contre, aucune fonctionnalité majeure n'est présente dans C++17 :
    
* [Concepts](http://fr.cppreference.com/w/cpp/concept) ;  
* [Modules](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf) pour remplacer les `#include <string>` par des `import std.string;`) ;
* [Syntaxe d'appel uniforme *(Uniform call syntax)*](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax#C.2B.2B_proposal) ;
* [Coroutines](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0057r4.pdf) ;
* [Mémoire Transactionnelle _(Transactional Memory)_](http://en.cppreference.com/w/cpp/language/transactional_memory) ;
* [Réflexion _(Static Reflection)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0194r1.html).


3. Les changements au niveau de la bibliothèque standard
--------------------------------------------------------
    
Les changements qui peuvent bousculer notre vie de développeur :
    
* Les [algorithmes parallélisés](http://en.cppreference.com/w/cpp/experimental/parallelism#Parallelized_versions_of_existing_algorithms) (si multitâche performant).
* [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view) (pour utiliser les méthodes de std::string sur des const char* sans faire de ré-allocation inutile).
    
Les transfuges de chez [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) :
               
`boost::*` | `std::*`
-----------|---------
[`filesystem`](http://www.boost.org/doc/libs/1_61_0/libs/filesystem) | -> [`filesystem`](http://en.cppreference.com/w/cpp/filesystem)
[`variant`](http://www.boost.org/doc/libs/1_61_0/libs/variant) | -> [`variant`](http://en.cppreference.com/w/cpp/utility/variant)
[`any`](http://www.boost.org/doc/libs/1_61_0/libs/any) | -> [`any`](http://en.cppreference.com/w/cpp/utility/any)
[`optional`](http://www.boost.org/doc/libs/1_61_0/libs/optional) | -> [`optional`](http://en.cppreference.com/w/cpp/utility/optional)
[`math`](http://www.boost.org/doc/libs/1_61_0/libs/math) | -> [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math)
    
Par contre, impasse sur des fonctionnalités majeures très attendues, comme les [intervalles *(Ranges)*](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf). Nous aurions aussi aimé que le [réseau _(Networking)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) intègre plus tôt le C++.

4. Bilan C++17 et attentes pour C++20
-------------------------------------
    
Alors, version mineure ou majeure ?
    
* Les améliorations sont appréciables, mais aucune fonctionnalité majeure au niveau du langage.
* Et côté bibliothèque standard, la plupart des fonctionnalités majeures sont déjà disponibles dans [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) et supportent donc aussi d'anciennes versions des compilateurs.

Partager
========
    
Chère lectrice, cher lecteur _LinuxFr.org_. Tu souhaites donner un coup de main pour les dépêches suivantes ? Rejoins‐nous dans l’[espace de rédaction collaborative sur _LinuxFr.org_](https://linuxfr.org/redaction). Un [compte](https://linuxfr.org/compte/inscription) est nécessaire pour y accéder.
    
De nombreux lecteurs *LinuxFr.org* ont beaucoup contribué à cette dépêche pour détailler au mieux l’ensemble des nouvelles fonctionnalités. Malgré les ambiguïtés/erreurs/fôtes/maladresses résiduelles, cette dépêche restera figée sur le site *LinuxFr.org*.
    
Par contre, tu peux continuer à enrichir ce contenu sur [le dépôt Git C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news). C’est donc sur ce dépôt [Git C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news) que tu trouveras les versions de ces dépêches les plus à jour :
    
1. [_Les coulisses du standard C++_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md) ;
2. [_Genèse d’une version mineure_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md) ;
3. [_Nouveautés du langage_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md) ;
4. [_Nouveautés de la bibliothèque standard_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n4_Cpp17_Nouveautes-de-la-bibliotheque.md) ;
5. [_Bilan et attentes pour C++20_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n5_Bilan-Cpp17-et-attentes-Cpp20.md).
    
Avec toutes nos contributions réunies, nous proﬁterons davantage de nos découvertes individuelles et nous offrirons un contenu CC BY-SA de qualité pour créer, par exemple, des supports de formation _(Meetups)_, des publications sur d’autres blogs, des ~~articles Wikipédia~~ Ah zut, pas pour le moment : notre dépêche utilise la version 4 de la licence CC BY-SA et Wikipédia la [version précédente](https://fr.wikipedia.org/wiki/Wikipédia:Citation_et_réutilisation_du_contenu_de_Wikipédia) :-/

Compatibilité avec le langage **C**
===================================


**C++17** est maintenant [basé sur **C11** au lieu de **C99**](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r2.html) + **C Unicode TR**.
    
Ajout des en-têtes (_headers_) `<stdalign.h>` et `<uchar.h>`. On ignore les en-têtes **C11** `<stdatomic.h>`, `<threads.h>` et `<stdnoreturn.h>`. [Dépréciation](https://fr.wikipedia.org/wiki/D%C3%A9pr%C3%A9ciation_(informatique)) des en-têtes `<ccomplex>`, `<ctgmath>`, `<cstdalign>`, `<cstdbool>`, `<complex.h>`, `<stdalign.h>`, `<stdbool.h>` et `<tgmath.h>`.
    
Donc, **C++17** se base sur une partie du **C11**. Par exemple, la gestion du multitâche du **C** n'est pas prise en compte dans le standard (donc c'est optionnel). Pour la première fois, le **C++** n'est plus rétrocompatible —  du moins une partie — avec les en-têtes du **C** (le **C** était un sous-ensemble du **C++**).  
    
Finalement, peu de changements. Par exemple, la fonction [`aligned_alloc()`](http://en.cppreference.com/w/c/memory/aligned_alloc) avait déjà été intégrée avec **C++11**.

Suppression
===========


[[P0001R1]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html) Mot clé `register`
---------------------------------------------------------------------------------------------------------

Pour rappel en C, le mot-clé `register` indique que la variable devrait être stockée dans un registre du processeur. On gagne en performance par rapport à ceux qui sont en mémoire, mais à plusieurs contraintes. 

```cpp

register int f = 0;  // Interdit sur les variables globales

int main(int argc, char *argv[]) {
    register int c = 0;  // Les variables register n'existe plus en C++17

    // Erreur puisque une variable register n'a pas d'adresse
    int *pointeur_vers_c = &c;

    register int tableau[1];  // Comportement indéfini

    return 0;
}

```


Son utilisation est déconseillée en C++11, plutôt que retirée à l’époque, car il ne rentrait pas en conflit avec une réaffectation, contrairement à `auto`. L’une des raisons énoncées pour la conservation est la compatibilité avec le C, en particulier avec les arguments des fonctions. Pourtant, son usage n’est pas pertinent en C++. Il est redondant avec d’autres fonctionnalités et les restrictions de `register` ne peuvent être transcrites en C++. Plutôt que d’essayer de résoudre les différences avec le C, il devient un mot-clé réservé pour un usage futur.

[[P0002R1]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html) Incrémentation sur un booléen
-----------------------------


Dans les temps anciens du C, le type booléen n’excitait pas. Les entiers — int — les remplaçaient. Zéro pour faux et les autres valeurs pour vrai. Le passage du C au C++ avait nécessité de garder une comptabilité avec le vieux code. Ne pouvant implémenter correctement la décrémentation, car produisant un comportement indéfini quand il est supérieur à 1. Il a été décidé de rendre illégale l’incrémentation d’un booléen, déjà dépréciée en C++98.

[[P0004R1]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)  Alias de iostreams
------------------

Obsolète en C++98, les alias de iostreams sont proscrits, pour simplifier la norme. Ils sont avantageusement remplacés par les masques de bits `os_base::iostate`, `ios_base::openmode`, … Les changements à apporter aux codes existants sont minimes.

```cpp
    std::ofstream mon_fichier;

    /* Légale avant C++17 */
    std::ios_base::open_mode mode = std::ios::out | std::ios::app;
    un_fichier.open("exemple.txt", mode);

    std::ios_base::io_state etat = std::ios_base::goodbit;
    un_fichier.clear(etat);

    /* Devrait être */
    std::ios_base::openmode mode = std::ios::out | std::ios::app;
    un_fichier.open("exemple.txt", mode);

    std::ios_base::iostate etat = std::ios_base::goodbit;
    un_fichier.clear(etat);

```




[[N4086]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html) Digraphes et trigraphes
-----------------------

Certaines entreprises maintiennent du très vieux code C/C++ contenant des [digraphes et trigraphes](https://en.wikipedia.org/wiki/Digraphs_and_trigraphs#Removal_of_trigraphs). Ces digraphes/trigraphes peuvent être remplacés par les caractères correspondant avec un script. Mais ces entreprises préfèrent que les compilateurs conservent cette complexité et que les développeurs aient des surprises quand ils utilisent certains caractères.

La dépréciation des digraphes/trigraphes avait été prévue en 2009 pour C++11. Mais certains membres comme IBM et Bloomberg étaient réticents. Finalement, c’est la suppression pure et simple qui a été votée par les membres pour C++17 (sans passer par la dépréciation). IBM a même tenté une dernière [tentative pour conserver les digraphes/trigraphes](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4210.pdf) ;

```cpp
/* Avec des digraphes et trigraphes */
??=include <iostream>

int main(int argc, char *argv<::>) ??< 
        const char hello_world ??(??) = "Hello world !??/0";
        std::cout << hello_world << std::endl;
        return 0;
??>

/* Équivaut à */
#include <iostream>
int main(int argc, char *argv[]) {
        const char hello_world[] = "Hello world !\0";
        std::cout << hello_world << std::endl;
        return 0;
}

```


Corrections
===========


[[N4261]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html) Conversion des tableaux de pointeurs
---------------------------------------------------------------------------------------------------------- 

Le brouillon N4261 complète la section 4.4 (conversion de qualification) sur la conversion d’un tableau de pointeurs constants/volatiles vers un autre type similaire.

```cpp
double *tableau_2d[2][3];
  
      double  *       (*tableau_2d_ptr1)[3] = tableau_2d;
      double  * const (*tableau_2d_ptr2)[3] = tableau_2d_ptr1;
const double  * const (*tableau_2d_ptr3)[3] = tableau_2d_ptr2; // Légal en C++17

```


[[P0136R1]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) Héritage des constructeurs
--------------------------------------------------------------------------------------------------
 Certaines règles d’héritage des constructeurs via `using` ont été modifiées dans un soucis de cohérence et de simplification. Concrètement, plusieurs cas d’héritages précédemment interdits sont maintenant autorisés.

SFINAE sur les constructeurs hérités fonctionne de manière fiable :

```cpp
struct A {
  template<typename T> A(T, typename enable_if<sizeof(T) == 4, int>::type = 0);
};
struct B : A {
  using A::A; // déclare les constructeur suivants :
              //   #1: B(T)
              //   #2: B(T, typename enable_if<...>::type)
              // car maintenant A::A(T, typename enable_if<...>::type = 0)
              // est un constructeur visible depuis B
  B();
};
B b(123ull);  // maintenant autorisé ; 
```

Paramètres variables :


```cpp
struct A { A(const char *, ...); };
struct B : A { using A::A; };
    B b("%d %d", 1, 2); // Maintenant accepté dans toutes les implémentations
```

Les droits d’accès sont maintenant identique à ceux de la classe de base :

```cpp
class A {
public:
 template<typename T> A(T, typename T::type);
 private:
  A(int);
  friend void f();
};
class B {
  typedef int type;
  friend class A;
};
struct C : A {
  using A::A;
};
void f() {
  A a1(B(), 0); // accepté (pas de changement)
  C c1(B(), 0); // précédemment refusé (le constructeur implicite de C ne pouvait pas accéder à B::type), maintenant accepté
    
  A a2(42); // accepté (pas de changement), f est un `friend`)
  C c2(42); // précédemment refusé,( (le constructeur implicite de C ne pouvait pas accéder au constructeur de A), maintenant accepté
}
C c3(123); // reste refusé, pas d'accès à A(int) 
``` 
En présence d’arguments par défaut, le masquage des constructeurs fonctionne maintenant de la même manière que pour les autres membres hérités via `using`.

```cpp
struct A {
  A(int a, int b = 0);
  void f(int a, int b = 0);
};
struct B : A {
  B(int a);      using A::A;
  void f(int a); using A::f;
};
struct C : A {
  C(int a, int b = 0);      using A::A;
  void f(int a, int b = 0); using A::f;
};

B b(0); // était accepté, maintenant ambigu.
b.f(0); // ambigu(pas de changement)

C c(0); // était ambigu, maintenant accepté
c.f(0); // accepté (pas de changements)
```

[[P0145R2]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r2.pdf) Évaluation stricte des expressions
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Héritées du C, les sous-expressions sont indéfiniment séquencées. Ce choix amène à des comportements incertains, notamment lorsqu’on utilise le même objet.

```cpp

std::map<int, int> m;
m[0] = m.size();
int i = 0;

// Doit afficher 0 ou 1 ?
// Avec Clang : 0
// Avec G++ : 1
std::cout << m[0] << std::endl; 

// Avec Clang : 00
// Avec G++ : 10
std::cout << i << i++; 

```



Cette absence de spécification est dommageable avec les pratiques courantes, comme le chaînage (`std::future<T>`, `std::io_base`, …).

```cpp

    std::string s = "but I have heard it works even if you don't believe in it";
    s.replace(0, 4, "")
//  ^ ^       ^  ^  ^
//  A B       |  |  |
//            1  2  3

        .replace(s.find("even"), 4, "only")
//       ^       ^               ^  ^
//       C       |               |  |
//               4               5  6
//              
        .replace(s.find(" don't"), 6, "");
//      ^        ^                 ^  ^
//      D        |                 |  |
//               7                 8  9
     assert(s == "I have heard it works only if you believe in it");


```



Dans l’exemple ci-dessus, l’assertion peut — selon le compilateur — échouer. Les expressions annotées alphabétiquement sont dites séquencées, dans l’ordre suivant : A, B, C, D.

TODO : À continuer

* Les boucles `for` *"each"* supportent des conteneurs ayant des
  [`begin()` et `end()` retournant des types différents mais comparables](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html).
  Cette correction est nécessaire à l'implémentation des [Intervalles *(Ranges)*](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf).
  Cela permet également de supporter d'avantage de [valeurs sentinelles](https://fr.wikipedia.org/wiki/Valeur_sentinelle) ;



* `noexcept` rejoint les [types systèmes](http://en.cppreference.com/w/cpp/language/type) afin de pouvoir distinguer les types de [pointeur de fonction](http://en.cppreference.com/w/cpp/language/pointer#Pointers_to_functions) `noexcept` des autres.
  Ainsi [C++17 peut interdir la conversion de pointeurs de fonction `throw(quelqchose)` vers ceux de fonctions `noexcept`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html), mais l'inverse est toujours possible. Le code suivant est valide en **C++14**, mais ne compile plus avec *C++17** :
    
    ```cpp
    void (*p)() throw(int);
    void (**pp)() noexcept = &p; //Erreur C++17
    
    struct S
    {
      typedef void (*p)();
      operator p();
    };
    void (*q)() noexcept = S(); //Erreur C++17
    
    template<class T>
    void f(T*, T*) {}
    void g1() noexcept {}
    void g2()          {}
    f(g1, g2);             // Erreur C++17
    ```
 

[[N4424]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r0.pdf) Variables `inline`
-------------------------------------------------------------------------------------------------

Les variables `inline` — comme les fonctions `inline` — peuvent être définies dans plusieurs unités de traduction (_translation units_). Son utilisation suggère au compilateur de substituer l'appel à la variable par son contenu. Elles sont adéquates pour remplacer les macros non-triviales. Plus subtil, on peut contourner la règle de la définition unique (_One Definition Rule_).

```cpp

struct A
{
    static int variable_inline;
};

inline int A::variable_inline = 0; // On peut maintenant appeler A::variable_inline

/* Ou plus simplement */
struct A
{
    static inline int variable_inline = 0; 
};

// Les constexpr de variables sont implicitement inline
const int constexpr celerite_lumiere = 299'792'458;



```



[À titre informatif](https://framagit.org/Cpp17/variable_inline), voici un exemple des différences d'instructions — x86_64 — avec et sans variable `inline`.

```nasm
-	.type	_ZN1A27variable_inline_sans_inlineE,@object # @_ZN1A27variable_inline_sans_inlineE
-	.section	.rodata,"a",@progbits
-	.globl	_ZN1A27variable_inline_sans_inlineE
-	.p2align	2
-_ZN1A27variable_inline_sans_inlineE:
-	.long	42                      # 0x2a
-	.size	_ZN1A27variable_inline_sans_inlineE, 4
```

[[P0035R3]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r3.html) Allocation mémoire dynamique des données
--------------------------------------------------------------------------------------------------------------------------


"over-aligned"* C++11 a permis de préciser l’alignement mémoire d'une structure avec le mot clef `alignas`
    
```cpp
class alignas(16) maclasse{
	float f[4];
};
```


Mais rien n'avait été précisé dans le cas d'une allocation dynamique


```cpp
maclasse *p = new maclasse[5];
```


Dans ce cas l'alignement mémoire de la zone allouée restait au choix du compilateur.


Avec C++17 des surcharges des opérateurs `new` et `delete` permettent de préciser l'alignement. 
`new maclasse[5]` est convertis soit en :

*  `operator new[](sizeof(maclasse)*5+x)` 
*  `operator new[](sizeof(maclasse)*5+x, std::align_val_t(alignof(maclasse)))`  nouvelle surcharge)

Si `std::align_val_t(alignof(maclasse))` est supérieur à `__STDCPP_DEFAULT_NEW_ALIGNMENT__`, c'est la nouvelle surcharge de `new` qui sera utilisée.

* [Garantie](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0135r0.html) de [court-circuitage du constructeur par copie](https://en.wikipedia.org/wiki/Copy_elision) ;
     
      TODO: Identifier la partie du TS qui a été acceptée
    *  r1 accepted, not r0
    * Finally!
    * Not in all cases, but distingushes syntax where you are "just creating something" that was called elision, from "genuine elision".



* [Forward progress guarantees (FPG)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0296r1.html)
  (voir aussi [FPGs for parallel algorithms](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0299r0.html)) ;
    
      TODO: Comprendre... Est-ce que cela veut dire "the implementation may not stall threads forever" ?


* [`Littéraux de caractère UTF-8`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html) ;
    
```cpp

const char une_chaine_de_caractere_utf8 = u8'U';
const char une_chaine_de_caractere_utf16 = u8'学'; // Erreur

```

* Réécriture des paragraphes a propos des [exception et `throw`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4285.html)
    
    TODO: Vérifier l'intérêt de ces changements


* La macro [**`__has_include(<filesystem>)`**](http://en.cppreference.com/w/cpp/experimental/feature_test#Language_Features#Function_Macros) vérifie si l'en-tête `<filesystem>` est disponible pour inclusion ;
    
    ```cpp
    #if    __has_include(<filesystem>)
    #  include <filesystem>
    #elif  __has_include(<experimental/filesystem>)
    #  include <experimental/filesystem>
    #elif __has_include(<boost/filesystem.hpp>)
    #  include <boost/filesystem.hpp>
    #else
    #  error Ne trouve aucune en-tête filesystem
    #endif
    ```
    
    ```cpp
    #if __has_include(<windows.h>)
    #  include <windows.h>
       LONGLONG ticks1nano = []() {
         LARGE_INTEGER freq;
         QueryPerformanceFrequency(&freq);
         return freq.QuadPart / 1000'000;
       }();
       LONGLONG nanosecondes() {
         LARGE_INTEGER time;
         QueryPerformanceCounter(&time);
         return time.QuadPart/ticks1nano;
       }
    #elif __has_include(<time.h>)
    #  include <time.h>
       auto nanosecondes() {
          struct timespec ts;
          clock_gettime(CLOCK_MONOTONIC,&ts);
          return 1000'000'000 * ts.tv_sec + ts.tv_nsec;
       }
    #else
    #  error Ne trouve ni <windows.h> ni <time.h>
    #endif
    ```


* Correction des évaluations constantes pour tout argument `template` n'étant pas un type [_(Allow constant evaluation for all non-type template arguments)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html). Les types **pointeur**, **référence** et **pointeur-vers-membre** acceptent d'avantage d'expressions constantes. C'est un oubli de C++11 qui avait pourtant étendu la notion d'expression constante. La [table suivante](http://open-std.org/JTC1/SC22/WG21/docs/papers/2014/n4198.html) résume les changements.
         
    Type     | C++14  | C++17
    ---------|--------|-------
    Pointeur|`&variable`, tableau, fonction référant un objet statique ou `nullptr` | évaluation d'une adresse constante d'un objet complet statique ou d'une fonction, ou `nullptr`
    Référence|objet ou fonction référant un objet statique| évaluation d'un *glvalue* constant référant un objet complet statique ou d'une fonction
    Pointeur-vers-membre|`&S::statique` ou `nullptr`|toutes expressions constantes
    Intégral `bool char int` ...|toutes expressions constantes|pareil
    `enum`|toutes expressions constantes|pareil
    `nullptr_t`|toutes expressions constantes|pareil
    
    ```cpp
    // Cette classe permet de tester
    // les expressions constantes
    template<int* EXPRESSION_CONSTANTE>
    class Test
    { };
    
    // La fonction constexpr getPtr() retourne
    // un pointeur vers un objet statique
    // (static storage duration object)
    int entier = 42;
    constexpr int* getPtr()     {return &entier;}
    constexpr int* getNullptr() {return nullptr;}
    Test<&entier>        ok_entier;
    Test<getPtr()>       ok_Cxx17; //KO C++14
    Test<getNullptr()>   ok_nullptr;
    
    // L'expression &obj.statique est un
    // pointeur-vers-membre d'un objet statique
    struct Str
    { int membre; static int statique; };
    Str obj;
    Test<&Str::membre>   ko_ptr_non_statique;
    Test<&Str::statique> ok_ptr_statique;
    Test<&obj.statique>  ok_cxx17; //KO C++14
    
    // Le pointeur vers un élément de tableau
    // statique ne semblent pas être supportés
    int   tableau[5];
    Test<&tableau[2]>    ko_adresse_element;
    ```



Sucre syntaxique
================


* **[`namespace`](http://en.cppreference.com/w/cpp/language/namespace) [`aa::bb { }`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)** correspond à **`namespace aa { namespace bb { } }`** ;

* [`static_assert(condition)`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf) avec un seul paramètre. Avant, seule la fonction [`static_assert(condition, message)`](http://fr.cppreference.com/w/cpp/language/static_assert) était disponible avec le second paramètre `message` obligatoire ;

Constante virgule flottante en hexadécimal
------------------------------------------
    
Le [TS P0245 *Hexadecimal floating literals*](http://wg21.link/p0245) amendé à la réunion de Jacksonville en février 2016 permet d'exprimer les [virgule flottante (IEEE 754)](https://fr.wikipedia.org/wiki/Virgule_flottante#Norme_IEEE_754) en hexadécimal. Enfin, le C++ permet d'avoir une représentation exacte des [virgules flottantes](http://en.cppreference.com/w/cpp/language/floating_literal). Cette fonctionnalité était déjà présente depuis longtemps dans d'autres langages : C99, Java 5 (2004)...
    
La représentation hexadécimale a l'avantage d'être celle du registre (mémoire binaire). Attention à la notation décimale des virgules flottantes. Par exemple, `0.1f` ne vaut pas exactement `0.1` mais `0.10000000149...`. Un petit exemple :
    
```cpp
#include <stdint.h>
#include <iostream>
#include <cassert>
    
int main()
{
  float un_dixieme = 0.1;
  float fois_1E12 = un_dixieme * 1E12;
  int64_t similaire = 1E12 / 10;
  long double diff_longd = fois_1E12;
  int64_t     diff_int64 = fois_1E12;
  diff_longd -= similaire;
  diff_int64 -= similaire;
    
  std::cout.precision(99);
  std::cout << 
   "un_dixieme = "<< un_dixieme << "\n"
   "fois_1E12  = "<< fois_1E12  << "\n"
   "similaire  = "<< similaire  << "\n"
   "diff_longd = "<< diff_longd << "\n"
   "diff_int64 = "<< diff_int64 << '\n';
}
```


    
    
Qui donne le résultat :
    
    un_dixieme = 0.100000001490116119384765625
    fois_1E12  = 99999997952
    similaire  = 100000000000
    diff_int64 = -2048
    diff_longd = -2048
    
Convaincu de l'intérêt des hexadécimaux pour les virgules flottantes ?
Passons à la pratique :
    
```cpp
// Fraction hexadécimale
float  v = 0xa.bp3f;
assert(v == 85.5f);
// 0xA.B = 0xA*16^0 + 0xB*16^-1
// 0xA   = 10
// 0x.B  = 11/16 = 0,6875
// 0xA.B = 10,6875
// p3 = 2^3 = 8
// v = 10,6875*8 = 85,5
// 'f' final = type 'float'
    
double w = 0xC0DE2017.1CAFEp-1;
assert(w == 1617891339.55602931976318359375);
// 0xC0DE2017 = 3235782679
// 0x1CAFE    = 117502
// 0xFFFFF    = 1048576
// p-1        = 2^-1 = 1/2
// w = (3235782679 + 117502/1048576) / 2
```


    
Chère lectrice, cher lecteur *LinuxFr.org*, as-tu d'autres idées de jeux de mots avec cette notation hexadécimale ? Alors défoule toi dans les commentaires ;-)
    
Remarquons le `p` à la fin. Celui-ci représente l'exposant binaire et il est suivi par un entier décimal (et non pas hexadécimal). Cet exposant binaire est obligatoire pour plusieurs raisons :
    
- Évite l'ambiguïté du `f` final dans `0xA.Bf` (`float` ou le chiffre `F` hexadécimal ?) ;
- Évite l'ambiguïté du `E` dans `0xa.bE-12` (exposant `-12` ou `0xA.BE - 12` ?) ;
- Correspond à la norme [IEEE 754](https://fr.wikipedia.org/wiki/IEEE_754) (puissance de deux) ;
- 100% compatible avec la notation C99 (et celle d'autres langages).
    
Tentons de représenter cette notation hexadécimale en regex :
    
* `0[xX][0-9a-fA-F]+[.]?[pP][+-]?[0-9]+[fFlL]?`
* `0[xX][0-9a-fA-F]*[.][0-9a-fA-F]+[pP][+-]?[0-9]+[fFlL]?`
    
Allez, soyons curieux, regardons comment le standard C++ spécifie cette notation avec un extrait du chapitre **§ 2.13.4 Floating literals** du [brouillon C++17](https://github.com/cplusplus/draft/raw/master/papers/n4604.pdf) :
    
> *hexadecimal-floating-literal:*
>   &emsp; *hexadecimal-prefix hexadecimal-fractional-constant binary-exponent-part floating-suffix<sub>opt</sub>*
>   &emsp; *hexadecimal-prefix hexadecimal-digit-sequence binary-exponent-part floating-suffix<sub>opt</sub>*
> *hexadecimal-fractional-constant:*
>   &emsp; *hexadecimal-digit-sequence<sub>opt</sub> . hexadecimal-digit-sequence*
>   &emsp; *hexadecimal-digit-sequence .*
> *binary-exponent-part:*
>   &emsp; `p` *sign<sub>opt</sub> digit-sequence*
>   &emsp; `P` *sign<sub>opt</sub> digit-sequence*
> *sign:* one of
>   &emsp; `+` `-`
> *digit-sequence:*
>   &emsp; *digit*
>   &emsp; *digit-sequence ’<sub>opt</sub> digit*
> *floating-suffix:* one of
>   &emsp; `f` `l` `F` `L`
    
Et l'équivalent chez [cppreference.com](http://en.cppreference.com/w/cpp/language/floating_literal) :
    
> `0x | 0X hex-digit-sequence`
> `0x | 0X hex-digit-sequence .`
> `0x | 0X hex-digit-sequence(optional) . hex-digit-sequence`
>
> Hexadecimal digit-sequence representing a whole number without a radix separator. The exponent is never optional for hexadecimal floating-point literals: `0x1ffp10`, `0X0p-1`, `0x1.p0`, `0xf.p-1`, `0x0.123p-1`, `0xa.bp10l`
>
> The exponent syntax for hexadecimal floating-point literal has the form
> `p | P exponent-sign(optional) digit-sequence`
>
> exponent-sign, if present, is either + or -
>
> suffix, if present, is one of `f`, `F`, `l`, or `L`. The suffix determines the type of the floating-point literal:
>
>  * (no suffix) defines double
>  * `f F` defines float
>  * `l L` defines long double
    
En attendant C++17, il est possible d'utiliser [`strtof()`](http://en.cppreference.com/w/cpp/string/byte/strtof) et [`std::hexfloat`](http://en.cppreference.com/w/cpp/io/manip/fixed) pour jouer avec les virgules flottantes hexadécimales. Un exemple :

```cpp
#include <iostream>
#include <cstdlib>
#include <cstdio>

int main (int argc, char *argv[])
{
   if (argc != 2) {
        std::cout <<"Usage: "<< argv[0] <<" 0xA.Bp-1  => Decode hexfloat" "\n";
        return 1;
   }
    
   std::cout <<"Decode floating point hexadecimal = "<< argv[1];
   long double l = std::strtold(argv[1],NULL); if(errno==ERANGE)std::cout<<"\nstrtold() erreur";
   double      d = std::strtod (argv[1],NULL); if(errno==ERANGE)std::cout<<"\nstrtod() erreur";
   float       f = std::strtof (argv[1],NULL); if(errno==ERANGE)std::cout<<"\nstrtod() erreur";
    
   std::cout <<"\n"  "long double = "<< std::defaultfloat << l <<'\t'<< std::hexfloat << l
             <<"\n"  "double      = "<< std::defaultfloat << d <<'\t'<< std::hexfloat << d
             <<"\n"  "float       = "<< std::defaultfloat << f <<'\t'<< std::hexfloat << f <<'\n';
}
```


Nous pouvons regretter qu'il faille utiliser des fonctions `strtof()` issues du C. En théorie, `std::hexfloat` devrait fonctionner pour l'entrée (`istream`). Mais dans la pratique `std::hexfloat` semble ne fonctionner que pour la sortie (`ostream`). L'exemple suivant ne fonctionne toujours pas avec GCC-6.2 et Clang-3.9 :
    
```cpp
double d;
std::istringstream("0xA.Bp-1") >> std::hexfloat >> d;
std::cout << d;
```

* Déstructuration du retour de fonction [*(Structured bindings)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r2.html) comme `std::tie` mais avec `auto`. S'applique aux `std::tuple`, aux tableaux (comme `std::array`) et aux structures plates (comme `std::pair`).
    
    ```cpp
    struct S { int a; double b; };
    S fonction() { return S{5,6}; }
    auto [ x, y ] = fonction();
    assert( x == 5 );
    ```

* [`if(init;condition)` et `switch(init;condition)`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r0.html) comme pour `for(init;cond;inc)`.
  L'expression **`if(MonType v = truc())`** peut être remplacée par **`if(MonType v = truc(); v)`**.
    
    ```cpp
    // Version verbeuse
    { // <-- bloc nécessaire pour limiter
      // la portée des variables locales 
      const auto paire = map.insert({k,v});
      auto iterateur   = paire.first;
      bool inserted    = paire.second;
      if (inserted)
        return iterateur;
    }
    
    // Version C++17
    if (const auto [iterateur, inserted]
           = map.insert({key,value}); 
           inserted)
      return iterateur;
    ```

* [`if constexpr`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0128r1.html), initialement [`constexpr_if`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0128r0.html), et encore avant c'était `static_if`. Cette fonctionnalité très attendue va simplifier beaucoup de code générique :
    
    ```cpp
    //__Trois définitions avant C++17__
    void fonction()
    { std::cout << std::endl; }
    
    template <class T>
    void fonction (const T& t)
    { std::cout << t; }
    
    template <class T, class... R>
    void fonction (const T& t, const R&... r)
    {
      fonction(t);    // Gère un argument
      fonction(r...); // Gère le reste
    }                 // (peut être vide)
    
    //__Une seule définition grâce à C++17__
    template <class T, class... R>
    void fonction (const T& t, const R&... r)
    {
      std::cout << t;    // Gère un argument
      if constexpr (sizeof...(r))
        fonction(r...);  // Gère le reste
      else
        std::cout << std::endl;
    }
    ```


* [Déduction des arguments `template` par le constructeur](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html) comme le font déjà les fonctions `template` ;
    
    ```cpp
    using std;
    array<int,3> avantCpp17{4,5,6};
    array        avecCpp17 {4,5,6};
    
    // Avec fonction d'aide template
    decltype(auto) a = make_array(4,5,6);
    ```

* [`template<auto>`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r1.html)
  permet de remplacer `MaClasse<decltype(entier),entier>`
  par un élégant `MaClasse<entier>` dans cet exemple :
    
    ```cpp
    // Avant C++17
    template <typename T, T Constante>
    class MaClasse
    {
        T maFonction() const {
            T x = Constante;
            return ++x;
        }
    };
    
    int main()
    {
        int entier = 42;
        MaClasse<decltype(entier),entier> mon_instance;
        return mon_instance.maFonction();
    }
    
    // Grâce à C++17
    template <auto Constante>
    class MaClasse
    {
        auto maFonction() const {
            auto x = Constante;
            return ++x;
        }
    };
    
    int main()
    {
        int entier = 42;
        MaClasse<entier> mon_instance;
        return mon_instance.maFonction();
    }
    ```


* [`template<template<class...>typename foo> struct bar {}`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)
    
    TODO: Approfondir



* [( Folding + ... + expressions ) ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)
    
    TODO: Approfondir


* [`auto x{8};` est de type `int`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)
    
    TODO: Approfondir



[Lambda](http://en.cppreference.com/w/cpp/language/lambda)
========


* [`constexpr` par défaut](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4487.pdf)
  si répond aux critères `constexpr` ;


* Possibilité de [capturer `*this`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).
  Tout le contenu de l'objet `*this` est copié au lieu du pointeur `this`.
  C'est très avantageux pour les petits objets.
  La copie d'un objet plus volumineux permet aussi d'éviter de mettre en place des verrous
  entre fils d'éxécution [*(value semantics)*](https://en.wikipedia.org/wiki/Value_semantics) ;



Attributs
=========


* Possibilité d'appliquer des [`[[attributs]]` aux `namespace`s et `enum { erator[[s]] }`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html) ;
    
    TODO: à vérifier



Trois nouveaux [attributs standards](http://en.cppreference.com/w/cpp/language/attributes#Standard_attributes)
[`[[fallthrough]]`, `[[nodiscard]]` et `[[maybe_unused]]`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf)
(qui complètent les `[[noreturn]]`, `[[carries_dependency]]` et `[[deprecated]]`) :


- **`[[fallthrough]]`** indique au compilateur (ou à l'outil d'analyse de code) que c'est normal qu'il n'y ait pas de `break;` à la fin d'un `case`, on continue bien avec le `case` suivant. Cela évite ainsi d'avoir des avertissements _(warnings)_ inutiles.
      
      ```cpp
      switch (valeur)
      {
        case 1:
          std::cout <<" valeur 1";
          break;
        case 2:
          std::cout <<" valeur 2";
          [[fallthrough]]; // pas de break
                       // => continue avec
        case 3:        // le case suivant
          std::cout <<" valeur 2 ou 3";
          break;
        case 4:
          std::cout <<" valeur 4";
              // ici le break manque
              // (un oubli du dév. ?)
              // => Le compilateur peut
              // afficher un avertissement
        default:
          std::cout <<" valeur différente"
                      " de 1, 2, 3, 4";
      }
      ```


- **`[[nodiscard]]`** indique que la valeur de retour d'une fonction ne doit pas être ignorée. Ce fonctionnent était déjà implémenté par l'extension GNU `__attribute__((warn_unused_result))`.
      
      ```cpp
      // Ancienne version de affiche_division()
      // avec une possible division par zéro 
      // void affiche_division (int a)
      // { std::cout << (42/a); }
      
      // Nouvelle version
      [[nodiscard]] int affiche_division (int a)
      {                  // ce code d'erreur
          if (a == 0)    // doit être récupérée
              return -1; // par l'appelant
          
          std::cout << (42/a);
          return 0;      // pas de problème
      }
      
      // Mais main() n'a pas été mise à jour !
      int main (int argc, char *argv[])
      {
           affiche_division(argc-1);
           // Le compilateur peut avertir que
      }    // le code de retour est ignorée
      ```


- **`[[maybe_unused]]`** [(qui devait s'appeler `[[unused]]`)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf) indique quand une variable peut ne pas être utilisée et permet donc de supprimer des avertissements _(warning)_ inutiles. Cet attribut peut s'appliquer aux fonctions, aux paramètres de fonctions et aux variables.
      
      ```cpp
      [[maybe_unused]] void affiche_division(int a)
      { std::cout << (42/a); }
      
      int main (int argc, [[maybe_unused]] char *argv[])
      {
           [[maybe_unused]] bool test = argc % 2;
           assert(test); // assert() est généralement désactivé 
      }                  // en mode Release (-DNDEBUG)
      
      // Avant, des macros permettaient d'éviter les warnings
      #ifdef DOXYGEN_PARSING
      #  define DOC_ONLY(x) x
      #else
      #  define DOC_ONLY(x)
      #endif
      
      #ifdef NDEBUG
      #  define DEBUG_ONLY(x)        // Release
      #else
      #  define DEBUG_ONLY(x) x      // Debug
      #endif
      
      int main (int argc, char** DOC_ONLY(argv))
      {
           DEBUG_ONLY(bool impaire = argc % 2);
           assert(impaire);
      }
      ```
      [Mozilla propose aussi `DebugOnly<T>`](https://developer.mozilla.org/docs/Mozilla/Debugging/DebugOnly%3CT%3E) (plus élégant qu'une macro).



Donc en C++17 nous pourrons écrire:


```cpp
#include <array>

struct Truc
{
  bool  b = false;      
  float f = 0xA.Bp3f; // hexa
};

int main (int argc, 
    [[maybe_unused]] char* argv[])
{
  // Déduction array<int,4>
  std::array tableau {1,2,3,argc};
   
  // lambda constexpr
  auto f = [](){ return Truc(); };

  if constexpr (auto [x,y]=f(); x)
    return y + tableau[1] * argc;
  else
    return y - tableau[2] * argc;
}
```



Alors, chères lectrices et chers lecteurs de *LinuxFr.org* ?
Séduits ? Conquis ? Impatients de coder en C++17 ?
La tentation est grande d’épater ses collègues avec du code qu’ils ne comprennent plus… non ?
