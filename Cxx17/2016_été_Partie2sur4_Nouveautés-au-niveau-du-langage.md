| Pour contribuer à ce document, merci de lire le [`README.md`](README.md)
|-------------------------------------------------------------------------


C++17 - Partie 2 sur 4 - Nouveauté au niveau du langage
=======================================================


Authors |Oliver H, olibre, Benoît Sibaud, Lucas, palm123, cracky, Martin Peres et RyDroid
--------|------------------------------
License |[CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)


Les fonctionnalités de la prochaine version **C++17** sont arrêtées. Cette seconde dépêche, d'une série de quatre dépêches, se concentre sur les changements au niveau du langage C++. C'est une dépêche très technique avec de nombreux exemples de code.

![Illustration C++ de Dominic Alves sous license CC-BY-SA 2.0](https://c2.staticflickr.com/2/1116/785982209_b0da7b4380_o.jpg)

Par manque de temps (ou d'aide à la rédaction), cette dépêche ne détaille pas toutes les fonctionnalités (et contient peut-être quelques erreurs). Comme cette dépêche LinuxFr.org restera figée après publication, nous vous proposons de continuer à l'enrichir sur [un dépôt Git C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md). Cela nous permettra de partager nos recherches individuelles et de permettre la réutilisation d'un contenu libre (CC-BY-SA) pour créer, par exemple, un article Wikipédia en français, des *"Meetups"*...

----

* [Première rencontre début mars 2016 racontée par Herb Sutter](https://isocpp.org/blog/2016/03/trip-report-jax-sutter)
* [Seconde rencontre fin juin 2016 racontée par Herb Sutter](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/)
* [Dépôts Git du comité de standardisation ISO C++](https://github.com/cplusplus)
* [Article Wikipédia C++14](https://fr.wikipedia.org/wiki/C%2B%2B14)
* [Article Wikipédia C++17](https://en.wikipedia.org/wiki/C%2B%2B17)
* [Journal de rewind "C++17 est sur les rails" a propos de la première réunion](https://linuxfr.org/users/rewind/journaux/c-17-est-sur-les-rails)
* [Dépêche LinuxFr "Codeurs, Traducteurs, CppReference a besoin de vous" (2012)](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous)
* [Contenu Markdown de cette dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md)
* [Première rencontre début mars 2016 très détaillée par botondballo](https://botondballo.wordpress.com/2016/03/21/trip-report-c-standards-meeting-in-jacksonville-february-2016/)
* [Résumé de la seconde rencontre fin juin 2016](https://www.reddit.com/r/cpp/comments/4pmlpz)
* [Liste très complète des nouveautés C++17 sur StackOverflow](http://stackoverflow.com/a/38060437/938111)
* [Liste des nouveautés C++17 sur Meeting C++](https://meetingcpp.com/index.php/br/items/final-features-of-c17.html)

----

Série de quatre dépêches C++17
==============================
    
Cette dépêche ainsi que les trois autres sont figées après publication. Par contre, corriger/compléter est possible sur [le dépôt Git C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md). Ainsi la mise en commun des contributions individuelles permet de l'enrichissement mutuel et la réutilisation d'un contenu libre (CC-BY-SA) pour créer, par exemple, un article Wikipédia C++17 en français. Merci aussi d'aider à la rédaction des trois autres dépêches.

Ce chapitre présente un résumé des quatre dépêches.

1. Genèse du C++17
------------------

La spécification C++ n'est pas libre et [son téléchargement coûte 180 €](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=64029). Alors, les développeurs C++ utilisent un [brouillon _(draft)_ gratuit](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf). Par contre, le C++ est bien un [standard ouvert](https://fr.wikipedia.org/wiki/Format_ouvert) : pas de brevets logiciels ni de propriété intellectuelle. Mais de toutes façons, la plupart des développeurs C++, même expérimentés, n'ont jamais lu le standard. Car ce sont surtout [des livres](https://fr.wikipedia.org/wiki/The_C%2B%2B_Programming_Language) et plus récemment des [sites](http://fr.cppreference.com/) qui sont utilisés.

2. Les changements au niveau du langage
---------------------------------------

Nettoyage, correction, évolution, sucre syntaxique :
    
- [Déduction des arguments `template` lors de la déclaration](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html) pour ne pas avoir besoin des fonctions d'aide `make_*()` ;
* [Déstructuration du retour de fonction](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r2.html) `char x; int y; std::tie(x,y) = fonction();` ~~> `auto [ x, y ] = fonction();` ;
- [`template<auto>`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r1.html) pour éviter la redondance `decltype(variable)` dans `MaClasse<decltype(variable),variable>` ;
* [`namespace` imbriqué](http://en.cppreference.com/w/cpp/language/namespace) `namespace aaa { namespace bbb { ... } }` --> `namespace aaa::bbb { ... }` ;
- [`if constrexpr`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0128r1.html) pour sélectionner du code à la compilation (peut remplacer `#if` dans certains cas) ;
- Lambda `constexpr` et pouvant capturer `*this` ;
- [`if(init;condition)` et `switch(init;condition)`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r0.html) pour faire un peu comme `for(init;cond;inc)` ;
- [Variables `inline`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r0.pdf) (après les [variables `template`](http://en.cppreference.com/w/cpp/language/variable_template) du C++14) ;
- ...


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
    
* La [algorithmes parallélisés](http://en.cppreference.com/w/cpp/experimental/parallelism#Parallelized_versions_of_existing_algorithms) (si multitâche performant) ;
* [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view) (pour remplacer les `const std::string&`).

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
    
* Les améliorations sont appréciables, mais aucune fonctionnalité majeure au niveau du langage  ;
* Et côté bibliothèque standard, la plupart des fonctionnalités majeures sont déjà disponibles dans [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) et supportent donc aussi d'anciennes versions des compilateurs.

Partager
--------

La version la plus à jour de cette dépêche peut se trouver sur [ce dépôt Git C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md). Et pour aller encore plus loin, participons à l'amélioration de ce contenu CC-BY-SA en y ajoutant nos découvertes individuelles C++17 afin d'en faire profiter le plus grand nombre :-)

------------------------------------------

Version et compatibilité avec le langage **C**
==============================================

*  Reserved `std[0-9]+` for [future standard libraries](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0180r1.html)

*  C++17 library is based on [C11 instead of C99](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r2.html)

* **C++17** est maintenant basé sur **C11** au lieu de **C99** + **C Unicode TR** [*(C++17 refers to C11 instead of C99)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r2.html).  
    
    Ajout des en-têtes (_headers_) `<stdalign.h>` et `<uchar.h>`. On ignore les en-têtes **C11** `<stdatomic.h>`, `<threads.h>` et `<stdnoreturn.h>`. [Dépréciation](https://fr.wikipedia.org/wiki/D%C3%A9pr%C3%A9ciation_(informatique)) des en-têtes `<ccomplex>`, `<ctgmath>`, `<cstdalign>`, `<cstdbool>`, `<complex.h>`, `<stdalign.h>`, `<stdbool.h>` et `<tgmath.h>`.
    
    Donc, **C++17** se base sur une partie du **C11**. Par exemple, la gestion du multitâche du **C** n'est pas prise en compte dans le standard (donc c'est optionnel). Pour la première fois, le **C++** n'est plus rétrocompatible avec le **C** (le **C** était un sous-ensemble du **C++**).  
    
    Finalement, peu de changements. Par exemple, la fonction [`aligned_alloc()`](http://en.cppreference.com/w/c/memory/aligned_alloc) avait déjà été intégrée avec **C++11**.


Suppression
===========

* [trigraphs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html) ;

* Mot clé [`register`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html#6.10) reservé pour utilisation ultérieure ;

* [`bool b; ++b;`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html) ;

* [ios aliases](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html).

Sucre syntaxique
================

*  [`namespace A::B`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)

* Simple [`static_assert(expression);`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf) with no string

*  [Hexadecimal float point literals](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)

*  [Structured bindings](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r2.html)
   *  Basically, first-class `std::tie` with `auto`
   *  Example:
     * `const auto [it, inserted] = map.insert( {"foo", bar} );`
     *  Creates variables `it` and `inserted` with deduced type from the `pair` that `map::insert` returns.
   * Works with tuple/pair-likes & `std::array`s and relatively flat structs
*  [`if (init; condition)` and `switch (init; condition)`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r0.html)
   * `if (const auto [it, inserted] = map.insert( {"foo", bar} ); inserted)`
   * Extends the `if(decl)` to cases where `decl` isn't convertible-to-bool sensibly


Corrections
===========

* [Arrays of pointer conversion fixes](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)

*  [Generalizing range-based for loops](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)
     * Appears to be mostly support for sentinals, or end iterators that are not the same type as begin iterators, which helps with null-terminated loops and the like.

* [Fixed order-of-evaluation for (some) expressions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r2.pdf)
   *  Not including function arguments, but function argument evaluation interleaving now banned
   *  Makes a bunch of broken code work mostly, and makes `.then` on future work.

* ["noexcept" in the type system](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)

*  [Inline variables](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4424.pdf)
   *  Like inline functions
   *  Compiler picks where the instance is instantiated?

*  [Dynamic memory allocation for over-aligned data](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r1.html)

*  [Guaranteed copy elision](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0135r0.html) (r1 accepted, not r0: have not found r1 on 'net yet)
    * Finally!
    * Not in all cases, but distingushes syntax where you are "just creating something" that was called elision, from "genuine elision".

*  Forward progress guarantees (FPG) (also, [FPGs for parallel algorithms](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0299r0.html))
   *  I think this is saying "the implementation may not stall threads forever"?

* [`u8'U', u8'T', u8'F', u8'8'`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html) character literals.

* [`__has_include`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)
   * Test if a header file include would be an error
   * makes migrating from experimental to std almost seamless
* La macro [**`__has_include(<windows.h>)`**](http://en.cppreference.com/w/cpp/experimental/feature_test#Language_Features#Function_Macros) vérifie si l'en-tête `<windows.h>` est disponible pour inclusion ;
    
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


* [inherited constructors](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) fixes to some corner cases.


Exceptions
==========

* Changement des paragraphes de la [spécification des exception et de l'utilisation de `throw`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4285.html)


Code générique et `template`
============================

*  [Template argument deduction for class templates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html)
    * Like how functions deduce template arguments, now constructors can deduce the template arguments of the class

*  [`template <auto>`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r1.html)
    * Represents a value of any (non-type template argument) type
* [`template <auto>`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r1.html) qui permet de remplacer `MaClasse<decltype(entier),entier>` par un élégant `MaClasse<entier>` dans cet exemple :
    
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

 * [Non-type template arguments fixes](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)

 * [`template<template<class...>typename bob> struct foo {}`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

 * [( Folding + ... + expressions ) ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)

 * [`auto x{8};` is an `int`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

 *  [constexpr if](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0128r1.html)
   *  Much requested feature to simplify almost-generic code

Lambda
======

 *  [constexpr lambdas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4487.pdf)
    * Lambdas are implicitly constexpr if they qualify

 *  [Capturing `*this` in lambdas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)
    * `[*this]{ std::cout << could << " be " << useful << '\n'; }`

* [Lambdas](http://en.cppreference.com/w/cpp/language/lambda)
    * `constexpr` par défaut si répond aux critères `constexpr`
    * possibilité de capturer `*this` (copie de la totalité de l'objet `*this`)  



Attributs
=========

* [`[[attributes]]` on `namespace`s and `enum { erator[[s]] }`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

*  [`[[fallthrough]]`, `[[nodiscard]]`, `[[maybe_unused]]`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf) attributes 

Trois nouveaux [attributs standards](http://en.cppreference.com/w/cpp/language/attributes#Standard_attributes) `[[fallthrough]]`, `[[nodiscard]]` et `[[maybe_unused]]` (qui complètent les `[[noreturn]]`, `[[carries_dependency]]` et `[[deprecated]]`).

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











* Suppression du constructeur de copie inutile ([Guaranteed copy elision](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0135r0.html)) ;

* Spécification de l'ordre d'évaluation des paramètres des fonctions dans les expressions idiomatiques du C++ [*(Fixed order-of-evaluation for idiomatic C++ expressions)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r2.pdf) ;


* [Forward progress guarantees (FPG)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0296r1.html) (voir aussi [FPGs for parallel algorithms](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0299r0.html)) ;


* Les [variables `inline`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r0.pdf) (après les [variables `template`](http://en.cppreference.com/w/cpp/language/variable_template) du C++14) ;

* `if(init;condition)` et `switch(init;condition)` pour faire un peu comme `for(init;cond;inc)` [*(If statement with initializer)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r0.html) ;


* Sucre syntaxique pour les [`namespace`](http://en.cppreference.com/w/cpp/language/namespace)s imbriqués  *(nested)*  
  Exemple : **`namespace A::B {`** correspond à **`namespace A { namespace B {`** ;

* Déstructuration du retour de fonction [*(Structured bindings)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r2.html)
    
    ```cpp
    struct Structure { int a; double b; };
    Structure fonction();
    auto [ x, y ] = fonction();
    ```

* [`if constexpr`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0128r1.html) (initialement [`constexpr_if`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0128r0.html), et encore avant c'était `static_if`)
    
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


* Correction des évaluations constantes pour tout argument `template` n'étant pas un type [_(N4198 Allow constant evaluation for all non-type template arguments)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html). Les types **pointeur**, **référence** et **pointeur-vers-membre** acceptent d'avantage d'expressions constantes. C'est un oubli de C++11 qui avait pourtant étendu la notion d'expression constante. La [table suivante](http://open-std.org/JTC1/SC22/WG21/docs/papers/2014/n4198.html) résume les changements.
         
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

* Constante en virgule flottante exprimée en hexadécimal *(Hexadecimal [float point literals](http://en.cppreference.com/w/cpp/language/floating_literal))*, voir l'exemple `float f = 0xA.Bp3f;` ci-dessous ;


* [Déduction des arguments `template` des classes templates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html), voir l'exemple `std::array` ci-dessous ;

Donc en C++17 nous pourrons écrire:

```cpp
#include <array>

struct Truc
{
  bool  b = false;      
  float f = 0xA.Bp3f; 
};       // Fraction hexadécimale
         // 0xA.B = 10,6875
         // exposant 2^3 => f=85,5

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

Alors, cher lecteur/chère lectrice de LinuxFr.org ?
Séduit(e) ? Conquis(e) ?
Impatient de coder en C++17 ?
La tentation est grande d'épater ses collègues avec du code qu'ils ne comprennent plus...
