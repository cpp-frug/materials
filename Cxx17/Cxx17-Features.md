
Pour contribuer à ce document, merci de lire le [`README.md`](https://github.com/cpp-frug/materials/blob/master/README.md) |
-----------------------------------------------------------------------------------------------------|


C++17 sera une version mineure
------------------------------

Authors |Oliver H, olibre, Lucas, palm123, Benoît Sibaud et RyDroid
--------|------------------------------
License |CC by-sa


L'ajout de fonctionnalités au **C++17** a été clôturé. Faisons donc le tour des nouveautés et vérifions ce titre provocateur :-)

![Illustration C++ de Dominic Alves sous license CC-BY-SA 2.0](https://c2.staticflickr.com/2/1116/785982209_b0da7b4380_o.jpg)

Par manque de temps, cette dépêche ne détaille pas toutes les fonctionnalités (et contient peut-être quelques erreurs). Comme cette dépêche LinuxFr.org restera figée après publication, nous vous proposons de continuer à l'enrichir sur [un dépôt Git C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md). Cela nous permettra de partager nos recherches individuelles et de permettre la réutilisation d'un contenu libre (CC-BY-SA) pour créer, par exemple, un article Wikipédia en français, des *"Meetups"*...

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

----------------------------------------------


En bref
-------


Cette dépêche étant très longue, ce premier chapitre donne un aperçu rapide.

#### La face cachée du C++
    
D'abord, le standard C++ n'est pas libre. En puis, le [télécharger coûte 180 €](www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=64029). Alors, on se repli sur la version gratuite : un brouillon _(draft)_ disponible sur [open-std.org](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf) et sur [github.com](https://github.com/cplusplus/draft/blob/master/papers/n4296.pdf).
    
Par contre, c'est bien un [standard ouvert](https://fr.wikipedia.org/wiki/Format_ouvert) : le langage et l'API sont librement implémentables (pas de brevets logiciels ni de propriété intellectuelle) contrairement à d'autres langages comme Java ou C# !
    
Finalement, le standard n'est pas pratique au quotidien. Alors, ce sont plutôt des sites comme [cppreference.com](http://fr.cppreference.com/) qui sont utilisés. Et la plupart des développeurs C++, même expérimentés, n'ont jamais lu le standard !

#### Sucre syntaxique et autres améliorations du langage

- [Déduction des arguments template lors de la déclaration](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html), pas mal de fonctions d'aide `make_*()` ne seront plus nécessaires ;
- [`template<auto>`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r1.html) pour éviter la redondance `decltype(ma_variable)` dans `MaClasse<decltype(ma_variable),ma_variable>` ;
- [Variables `inline`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r0.pdf) (après les [variables `template`](http://en.cppreference.com/w/cpp/language/variable_template) du C++14) ;
- [`if(init;condition)` et `switch(init;condition)`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r0.html) pour faire un peu comme `for(init;cond;inc)` ;
* [`namespace` imbriqué](http://en.cppreference.com/w/cpp/language/namespace) `namespace aaa { namespace bbb { ... } }` --> `namespace aaa::bbb { ... }` ;
* [Déstructuration du retour de fonction](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r2.html) `char x; int y; std::tie(x,y) = fonction();` ~~> `auto [ x, y ] = fonction();` ;
- [`if constrexpr`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0128r1.html) pour sélectionner du code à la compilation (peut remplacer `#if` dans certains cas) ;
- Lambda `constexpr` et pouvant capturer `*this` ;
- ...

#### Bibliothèque standard

- [Parallélisation de 69 algorithmes](http://en.cppreference.com/w/cpp/experimental/parallelism#Parallelized_versions_of_existing_algorithms) ;
- Ajout de [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math) ;
- Intégration des bibliothèques [`filesystem`](http://en.cppreference.com/w/cpp/filesystem), [`variant`](http://en.cppreference.com/w/cpp/utility/variant), [`optional`](http://en.cppreference.com/w/cpp/utility/optional) et [`any`](http://en.cppreference.com/w/cpp/utility/any) après une longue maturation dans [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) ;
- [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view) (mieux que `const std::string&`) ;
- [`std::string::data()`](http://en.cppreference.com/w/cpp/string/basic_string/data) non-`const` ;
- ...

#### Fonctionnalités attendues mais finalement reportées

* [Concepts](http://fr.cppreference.com/w/cpp/concept) ;
* [Modules](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf) (`#include <string>` --> `import std.string;`) ;
* [Syntaxe d'appel uniforme *(Uniform call syntax)*](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax#C.2B.2B_proposal) ;
* [Coroutines](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0057r4.pdf) ;
* [Réseau _(Networking)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) ;
* [_Ranges_](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf) ;
* [Mémoire Transactionnelle _(Transactional Memory)_](http://en.cppreference.com/w/cpp/language/transactional_memory) ;
* [Réflexion _(Static Reflection)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0194r1.html).

#### Version mineure ou majeure ?

Nous avions déjà l'équivalent de [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem) avec [`boost::filesystem`](http://www.boost.org/doc/libs/1_61_0/libs/filesystem) (ce dernier supporte les anciennes versions des compilateurs).

Et les algorithmes parallélisés, sont-ils vraiment intéressants pour la production ?

#### Partager

Pour vraiment apprécier les nouveautés, lisez la suite de cette dépêche. La version la plus à jour étant sur [un dépôt Git C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md). Et pour aller encore plus loin, explorer soi-même les nouveautés et publier ses découvertes sur ce dépôt Git afin d'en faire profiter les autres :-)


------------------------------------------


La face cachée du C++
---------------------
    
Obtenir le standard C++ coûte cher :
    
* 182 € sur le [site de l'ISO](http://www.iso.org/iso/home/store/catalogue_ics/catalogue_detail_ics.htm?ics1=35&ics2=060&ics3=&csnumber=64029) (198 francs suisses) ;
* 238 € sur le [site de l'ANSI](http://webstore.ansi.org/RecordDetail.aspx?sku=ISO%2fIEC+14882%3a2014) (265 $ USA). 
    
De plus, à chaque nouvelle version du standard ISO/IEC 14882, la version précédente est supprimée (_withdraw_ en anglais) :
    
* C++98 [ISO/IEC 14882:1998](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=25845) supprimé ;
* C++03 [ISO/IEC 14882:2003](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=38110) supprimé ;
* C++11 [ISO/IEC 14882:2011](http://www.iso.org/iso/iso_catalogue/catalogue_ics/catalogue_detail_ics.htm?ics1=35&ics2=60&ics3=&csnumber=50372) supprimé.
    
On se console avec les brouillons qui sont gratuitement téléchargeables sur deux sites :
    
* [open-std.org/jtc1/sc22/wg21](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/)
* [github.com/cplusplus/draft](https://github.com/cplusplus/draft/tree/master/papers)
       
Les brouillons validées par le comité de standardisation C++ sont fournis à l'ISO qui change la mise en forme pour en faire une version officielle. Le nombre de pages 
    
      Standard                      | Pages
------------------------------------|-------
C++98 [ISO/IEC 14882:1998 1998-09-01](http://www.lirmm.fr/~ducour/Doc-objets/ISO+IEC+14882-1998.pdf) | 776 pages
C++03 [ISO/IEC 14882:2003 2003-10-15](https://github.com/hstefan/htlib/blob/master/res/INCITS%2BISO%2BIEC%2B14882-2003.pdf) | 786 pages (+1%)
C++11 [ISO/IEC 14882:2011 2011-09-01](http://new.vk.com/doc100509572_160085962?hash=6801602629449dfa59&dl=27c32949114b3322a2)| 1356 pages (+73%)
C++11 [Draft N3376 2012-02-28](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf)| 1324 pages
C++14 [Draft N4296 2014-11-19](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf) | 1368 pages (+3%)
C++17 [Draft N4594 2016-05-30](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4594.pdf) (pas encore finalisé)| 1519 pages (+11%)

La notice de droit d'auteur du document ne laisse aucun doute : **le standard C++ n'est pas libre**. Par contre, l'organisme ISO local _pourrait_ donner des permissions de reproduction...
      
> © ISO/IEC 2014 – All rights reserved  
> COPYRIGHT PROTECTED DOCUMENT  
> All rights reserved. Unless otherwise specified, no part of this publication may be reproduced or utilized otherwise in any form or by any means, electronic or mechanical, including photocopying, or posting on the internet or an intranet, without prior written permission.
> Permission can be requested from either ISO at the address below or ISO’s member body in the country of the requester.
            
Par contre, ce sont bien un [standard ouvert](https://fr.wikipedia.org/wiki/Format_ouvert), sans brevet logiciel, sans propriété intellectuelle. C'est à dire que le langage et sa bibliothèque standard peuvent être implémentés librement. Ce qui n'est pas le cas des langages comme Java ou C#.
    
Nous aurions aimé un standard plus ouvert comme pour Go ou Rust. Et c'est vers ce sens que le comité s'oriente, en cherchant plus de proximité avec les utilisateurs C++, plus de transparence.
   

Par rapport à tous les langages utilisés en production, avouons que le C++ est le langage le complexe que l'humanité ait pu inventer ! Les développeurs C++ en ont bien conscience. C'est peut-être la raison pour laquelle, par rapport aux autres _meetups_, les conférences sur le C++ ne dénigrent pas les autres langages. Au contraire, nous aimerions un langage plus simple, mais attention qui **"ne sacrifie pas les performances"**.
    
Le C++ est tellement vaste, qu'aucun développeur C++ ne connaît vraiment le C++ ! Seulement une portion, souvent petite (10%). Ceux qui connaissent vraiment le C++ sur le bout des doigts, on les appelle des juristes du C++ (_C++ lawyers_).
     
Pour inverser la tendance, certaines personnes influentes au comité de standardisation, comme [Bjarne Stroustrup](https://fr.wikipedia.org/wiki/Bjarne_Stroustrup), le créateur du C++, souhaitent aller rapidement vers un C++ plus intuitif, plus sûr, mais toujours plus performant.


C'est dans ce cadre, que l'initiative [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines) a été lancé. A la fois pour proposer un sous-ensemble du C++ plus sûr, plus simple et sans sacrifier les performances. Mais aussi pour faire pression aux membres du comité pour adopter les idées de la [Guidelines Support Library](https://github.com/Microsoft/GSL) (voir aussi l'[implémentation de Martin Moene](https://github.com/martinmoene/gsl-lite) compatible avec beaucoup plus de compilateurs).

------------------------------------------------------


Cycle et nommage des versions
-----------------------------

Après la version majeure **C++98** (et son correctif **C++03**), un nouveau standard C++ devait être publié dans les années suivantes. Comme sa date de publication n'était pas fixée, cette version a été nommée temporairement **C++0x**. Mais avec l'ajout continuel de nouvelles fonctionnalités, le comité de standardisation n'arrivait pas à stabiliser le standard. Et finalement **C++0x** a été publié en 2011 !


Afin d'éviter tout nouveau glissement, le comité a alors décidé de publier un nouveau standard C++ tous les 3 ans, en figeant les fonctionnalités l'année N-1. Avec un cycle d'une version majeure (**C++11**) suivie d'une version mineure (**C++14**).


Bien que ce process de standardisation ISO C++ permet de publier les nouvelles versions à la date prévue, les appellations **C++1y** (pour **C++14**) et **C++1z** (pour **C++17**) perdurent. Par exemple, l'[option de compilation `-std=c++1z`](https://gcc.gnu.org/projects/cxx-status.html) ou le [tag c++1z sur stackoverflow](http://stackoverflow.com/tags/c%2b%2b1z/info).


Les membres du comité de standardisation utilisent le terme **C++17** (et non pas C++1z). Soyons confiants, **C++1z** verra bien le jour en 2017 (et non pas en 2018, ni après).


Donc en 2016 (année N-1), le comité de standardisation ISO C++ (une centaine de personnes) s'est rencontré deux fois afin de figer le périmètre fonctionnel du **C++17** :

1. [Une semaine début mars](https://isocpp.org/blog/2016/03/trip-report-jax-sutter), à Jacksonville (Floride), pour valider des fonctionnalités _mineures_ et invalider des fonctionnalités _majeures_ ;
2. [Une semaine fin juin](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/), à Oulu (Finlande), pour définitivement clore l'ajout de nouvelles fonctionnalités (Anecdote : Les membres sont rentrés épuisés, car le soleil se couchait après minuit et le décalage horaire était important pour ceux qui venaient des USA).

------------------------------------------


Fonctionnalités au niveau du langage C++
----------------------------------------

* **C++17** est maintenant basé sur **C11** au lieu de **C99** + **C Unicode TR** [*(C++17 refers to C11 instead of C99)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r2.html).  
    
    Ajout des en-têtes (_headers_) `<stdalign.h>` et `<uchar.h>`. On ignore les en-têtes **C11** `<stdatomic.h>`, `<threads.h>` et `<stdnoreturn.h>`. [Dépréciation](https://fr.wikipedia.org/wiki/D%C3%A9pr%C3%A9ciation_(informatique)) des en-têtes `<ccomplex>`, `<ctgmath>`, `<cstdalign>`, `<cstdbool>`, `<complex.h>`, `<stdalign.h>`, `<stdbool.h>` et `<tgmath.h>`.
    
    Donc, **C++17** se base sur une partie du **C11**. Par exemple, la gestion du multitâche du **C** n'est pas prise en compte dans le standard (donc c'est optionnel). Pour la première fois, le **C++** n'est plus rétrocompatible avec le **C** (le **C** était un sous-ensemble du **C++**).  
    
    Finalement, peu de changements. Par exemple, la fonction [`aligned_alloc()`](http://en.cppreference.com/w/c/memory/aligned_alloc) avait déjà été intégrée avec **C++11**.

* La macro [**`__has_include(<boost/any.hpp>)`**](http://en.cppreference.com/w/cpp/experimental/feature_test#Language_Features#Function_Macros) qui vérifie si l'en-tête `<boost/any.hpp>` est disponible pour inclusion ;
    
    ```cpp
    #if __has_include(<boost/any.hpp>)
    #  include <boost/any.hpp>
    #else
    #  include <mon_propre_any.hpp>
    #endif
    ```

* Trois nouveaux [attributs standards](http://en.cppreference.com/w/cpp/language/attributes#Standard_attributes) `[[fallthrough]]`, `[[nodiscard]]` et `[[maybe_unused]]` (qui complètent les `[[noreturn]]`, `[[carries_dependency]]` et `[[deprecated]]`)
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

* [Lambdas](http://en.cppreference.com/w/cpp/language/lambda)
    * `constexpr` par défaut si répond aux critères `constexpr`
    * possibilité de capturer `*this` (copie de la totalité de l'objet `*this`)  


* Les boucles `for` *"each"* supportent aussi des conteneurs ayant des fonctions `begin()` et `end()` retournant des types différents, mais compatibles [*(Generalizing the Range-Based For Loop)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html). Ce qui est nécessaire à l'implémentation des [_Ranges_](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf) ;

* [Allocation mémoire dynamique des données *"over-aligned"*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r3.html) ;


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

* Constante en virgule flottante exprimée en hexadécimal *(Hexadecimal [float point literals](http://en.cppreference.com/w/cpp/language/floating_literal))*, voir l'exemple `float f = 0xA.Bp3f;` ci-dessous ;


* [Déduction des arguments `template` des classes templates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html), voir l'exemple `std::array` ci-dessous ;

Donc en C++17 nous pourrons écrire:

```cpp
#if __has_include(<boost/array.hpp>)
#  include <boost/array.hpp>
   using namespace boost;
#else
#  include <array>
   using namespace std;
#endif

struct Truc
{
  char  c = 'z';
  int   i = 9;        //C'est une fraction hexa
  float f = 0xA.Bp3f; // 0xA.B = 10,6875
};                    // exposant 2^3 => f=85,5

int main(int argc, [[maybe_unused]]char*argv[])
{
  // Déduction array<int,4>
  array tableau {1, 2, 3, argc};
   
  // lambda constexpr
  auto lambda = [](){ return Truc(); };

  if constexpr (auto [a,b,c]=lambda(); a=='a')
    return b + tableau[1] * argc;
  else
    return b - tableau[2] * argc;
}
```

Alors, cher lecteur/chère lectrice de LinuxFr.org ?
Séduit(e) ? Conquis(e) ?
Impatient de coder en C++17 ?
La tentation est grande d'épater ses collègues avec du code qu'ils ne comprennent plus...

---------------------------------------------------


Fonctionnalités au niveau de la bibliothèque STL
------------------------------------------------

* Suppression des [digraphes et trigraphes](https://en.wikipedia.org/wiki/Digraphs_and_trigraphs#Removal_of_trigraphs).
    
    ```cpp
    TODO Fournir un exemple
    ```
    
    Certaines entreprises maintiennent du très vieux code C/C++ contenant des digraphes/trigraphes. Ces digraphes/trigraphes peuvent être replacés par les caractères correspondant avec un script. Mais ces entreprises préfèrent que les compilateurs conservent cette complexité et que les développeurs aient des surprises quand ils utilisent certains caractères.
     
    La dépréciation des digraphes/trigraphes avait été prévue en 2009 pour C++11. Mais certains membres comme IBM et Bloomberg étaient réticents. Finalement, c'est la suppression pure et simple qui a été votée par les membres pour C++17 (sans passer par la dépréciation). IBM a même tenté une dernière [tentative pour conserver les digraphes/trigraphes](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4210.pdf) ;

* Ajout des [versions parallélisées de 69 algorithmes](http://en.cppreference.com/w/cpp/experimental/parallelism) *(Parallelism TS v1)* ; ![Deux cochons en position 69](http://vignette3.wikia.nocookie.net/necyklopedie/images/8/80/Porno_prase.png/revision/latest?cb=20090116191951)

* Ajout des [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math). C'est une longue histoire dont la [première proposition date de 2003](http://open-std.org/JTC1/SC22/WG21/docs/papers/2003/n1422.html) !
    
    ```cpp
    TODO fournir un exemple
    ```


* Ajout de [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem). Enfin le C++ dispose d'une API standardisée pour gérer fichiers et répertoires ! 
    
    ```cpp
    TODO fournir un exemple
    ```
    
    C'est aussi une longue histoire :
    
    * 2003 [`boost::filesystem`](http://www.boost.org/doc/libs/1_61_0/libs/filesystem) ;
    * 2004 [requête pour intégration dans la bibliothèque standard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1576.html) ;
    * 2005 [première proposition détaillée pour intégration dans la bibliothèque standard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1841.html) ;
    * Il aura fallu une dizaine d'années et trois versions majeures pour permettre au groupe d'étude SW3 _(Study Group 3)_ de rédiger l'ultime spécification technique _(TS)_ [N4100 (le titre est en français dans le document)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf) qui correspond au standard [ISO/IEC TS 18822:2015](http://www.iso.org/iso/catalogue_detail.htm?csnumber=63483) ;
    * L'implémentation de `std::experimental::filesystem` sur plusieurs plateformes et compilateurs ([Visual C++ 2012/2013/2015](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/msdn.microsoft.com/en-us/library/hh874694.aspx) et [GCC-5.3](https://gcc.gnu.org/onlinedocs/libstdc++/manual/using_dynamic_or_shared.html#manual.intro.using.linkage.experimental)) a été nécessaire pour décider de l'intégration dans la bibliothèque standard.

* Ajout du `std::variant` [*(type-safe union for C++17)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r2.html) et d'une partie des [*Library Fundamentals TS v1*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) :
    
    * [`std::variant<int,char,float>`](http://en.cppreference.com/w/cpp/utility/variant) en s'inspirant de [`boost::variant<>`](http://www.boost.org/doc/libs/1_61_0/libs/variant) (certains auraient aimé la possibilité d’interdire un objet `std::variant` vide et l'optimisation du `std::variant` pour les types légers) ;
    * [`std::optional<std::string>`](http://en.cppreference.com/w/cpp/utility/optional) en s'inspirant de [`boost::optional<>`](http://www.boost.org/doc/libs/1_61_0/libs/optional) ;
    * [`std::any`](http://en.cppreference.com/w/cpp/utility/any) en s'inspirant de [`boost::any`](http://www.boost.org/doc/libs/1_61_0/libs/any) ;
    * [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view) ;
    * et [autres extensions](http://en.cppreference.com/w/cpp/experimental/lib_extensions#Merged_into_C++17).

* Ajout de `hardware_*_interference_size` ;

* Ajout de `.is_always_lockfree()` ;

* Ajout de [`std::clamp()`](http://en.cppreference.com/w/cpp/algorithm/clamp). Par exemple, `std::clamp(x,4,8)` est l'équivalent de `std::min(std::max(x,4),8)`.

* Ajout des fonctions `string::data()` non-const ;


* Ajout des `destroy(_at|_n)`, `uninitialized_move(_n)`, `uninitialized_value_construct(_n)`, `uninitialized_default_construct(_n)` [*(Extending memory management tools)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r2.html) ;

* Ajout des fonctions `std::set::splice()`, `std::map::splice()`, `std::unordered_set::splice()` et `std::unordered_map::splice()` comme pour [`std::list::splice()`](http://fr.cppreference.com/w/cpp/container/list/splice) [*(Splicing Maps and Sets)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r2.pdf) ;

* Réservation du nommage `std[0-9]+` pour d'éventuelles futures versions de la ~~STL~~ bibliothèque standard C++ qui casseraient la rétrocompatibilité [*(Reserve a New Library Namespace Future Standardization)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0180r1.html).

C++17 fait l'impasse sur des fonctionnalités _majeures_
------------------------------------------------------

Deux _gros_ morceaux ont été inclus dans **C++17** :


* le parallélisme avec les [69 algorithmes parallélisées](http://en.cppreference.com/w/cpp/experimental/parallelism) ;
* et [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem).

Par contre, les fonctionnalités suivantes n’ont pas été considérées comme suffisamment mures pour être incluses :

* [Concepts](http://fr.cppreference.com/w/cpp/concept) (voir aussi la [version en anglais](http://en.cppreference.com/w/cpp/language/constraints)) ;
* Modules, par exemple **`import std.string;`** à la place de **`#include <string>`** [*(A Module System for C++)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf) ;
* Syntaxe d'appel uniforme [*(Uniform call syntax)*](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax#C.2B.2B_proposal) ;
* [Coroutines](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0057r4.pdf) ;
* Réseau [_(Networking)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) ;
* Tableaux [_(Array)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3820.html). Une idée de 2013, mais finalement abandonnée ;
* [_Ranges_](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf) ;
* Mémoire transactionnelle [_(Transactional Memory)_](http://en.cppreference.com/w/cpp/language/transactional_memory) ;
* Réflexion [_(Static Reflection)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0194r1.html) ;
* et autres extensions majeures de la bibliothèque standard. 

Le comité attend de voir des implémentations satisfaisantes dans les compilateurs avant de les inclure...

Même si **C++17** va un peu plus transcender notre façon de coder en C++, de nombreux développeurs s’attendaient à une version majeure (révolutionnaire). Par rapport à **C++11**, les apports du **C++17** ressemblent plus à une version mineure.

![Évolution des fonctionnalités majeures](https://herbsutter.files.wordpress.com/2016/06/wg21-timeline.png)


---------------------------------------------------------------


Déception et nouveau processus de standardisation pour ~~C++20~~ C++19
--------------------------------------------------------------------

Face à la déception de cette version _pas très majeure_, le comité réfléchit à faciliter la contribution de la communauté C++ et à améliorer le processus de standardisation :


* Une nouvelle version tous les deux ans (au lieu de trois ans) ;
* Chaque version inclura toutes les fonctionnalités prêtes l'année N-1 (au lieu d'avoir une alternance de versions majeurs/mineures).

Donc, après le **C++17**, le comité pourrait clôturer les fonctionnalités du prochain standard dès 2018 et publier un **C++19** en avance sur le **C++20** prévu initialement… Espérons que cet hypothétique **C++19** intégrera des fonctionnalités majeures. À suivre…

Et toi, cher lecteur/chère lectrice de LinuxFr.org, es-tu un peu déçu(e) du périmètre fonctionnel C++17 ?
Souhaites-tu des versions C++ plus fréquentes ?
Penses-tu que toutes ces nouvelles fonctionnalités ne font que compliquer inutilement le langage le plus complexe que l'humanité ait inventé ?
Ou au contraire, es-tu persuadé(e) que grâce à ces évolutions, le C++ va progresser dans le classement du _TIOBE Index_ et écarter des prétendants comme ~~[D](https://fr.wikipedia.org/wiki/D_(langage)),~~ [Rust](https://fr.wikipedia.org/wiki/Rust_(langage)) ou [Pony](http://www.ponylang.org/) ?

![Indice TIOBE de popularité des langages de programmation, la courbe en vert clair représente l'inexorable descente du C++ qui reste quand même en troisième place derrière Java et C, mais devant Python et C#](http://cdn.edureka.co/blog/wp-content/uploads/2016/06/TIOBE-index-2016.png)

---------------------------------------------------------------


Support des compilateurs
------------------------

Les différentes fonctionnalités du C++17 commencent à être implémentées par les principaux compilateurs. Souvent les fonctionnalités sont annoncées comme implémentées, malgré la présence de bugs ou de limitations. Voici une anecdote à ce sujet :   

Date        | Événement
------------|-------------
Mai 2013    |[**GCC-4.8.1**](https://gcc.gnu.org/gcc-4.8/changes.html) est annoncé comme le [premier compilateur C++11](https://gcc.gnu.org/projects/cxx-status.html#cxx11).
Janvier 2014|[**Clang-3.4**](http://llvm.org/releases/3.4/tools/clang/docs/ReleaseNotes.html) est annoncé comme le [premier compilateur C++14](http://clang.llvm.org/cxx_status.html#cxx14).
Avril 2015  |[**GCC-5.1**](https://gcc.gnu.org/gcc-5/changes.html) est annoncé comme implémentant toutes les fonctionnalités C++14.
Mai 2016    |La bibliothèque `boost::hana` est enfin intégrée à `boost` car au moins deux compilateurs supportent les fonctionnalités C++14 utilisées par cette bibliothèque : **Clang-3.5** et **GCC-6**. Donc, les versions précédentes **Clang-3.4** et **GCC-5.1** ne supportaient pas tout à fait C++14 !
Été 2017    |C'est peut-être au tour de Visual C++ d'être le premier compilateur C++17...

Il n'existe pas ~~vraiment~~ encore de test de conformité du support des fonctionnalités de telle ou telle version du C++ (pas d'équivalent aux [Acid3](https://fr.wikipedia.org/wiki/Acid3), [Sputnik](Sputnik_(JavaScript_conformance_test)) des technologies du web).


Vers un standard C++ modulaire
------------------------------


Par contre, on peut trouver des tables de compatibilité sur le support des différentes fonctionnalités C++ :

* sur [cppreference](http://en.cppreference.com/w/cpp/compiler_support) ;
* sur le site officiel [GCC](https://gcc.gnu.org/projects/cxx-status.html#cxx1z) ;
* sur le site officiel [Clang](http://clang.llvm.org/cxx_status.html#cxx17) et sa [libcxx](http://libcxx.llvm.org/cxx1z_status.html) ;
* sur le _blog_ [Visual C++](https://msdn.microsoft.com/fr-fr/library/hh567368.aspx) [(version en anglais)](https://blogs.msdn.microsoft.com/vcblog/2015/06/19/c111417-features-in-vs-2015-rtm/).

Changement important des nouvelles versions C++ : **un compilateur n'est plus obligé d'implémenter toutes les fonctionnalités C++17 pour être annoncé comme supportant C++17**. 

Par exemple, un éditeur pourrait vendre un compilateur supportant tout le C++17 sauf [_"attribute specifier sequence"_](http://en.cppreference.com/w/cpp/language/attributes) qu'il juge fastidieux et inutiles pour ses clients/prospects. Cet éditeur peut annoncer que son compilateur est conforme au C++17 excepté ces _"attributs"_. 

Donc, le support des fonctionnalités C++ est à la carte. Au lieu de devoir attendre un compilateur supportant toutes les fonctionnalités C++17 pour enfin coder en C++17, il est possible de coder dès maintenant en C++17 sur telle ou telle fonctionnalité C++17.


Par exemple, GCC-6 permet de profiter en avance des [_Concepts_ et de la _Transactional Memory_](https://gcc.gnu.org/projects/cxx-status.html#tses) (encore plus en avance que C++17). Et Clang-3.5 implémente un [support expérimental des _Modules_ C++](http://llvm.org/releases/3.5.0/tools/clang/docs/Modules.html) (support amélioré avec les [versions suivantes](http://llvm.org/releases/3.6.0/tools/clang/docs/Modules.html)).


En conclusion, pas la peine d'attendre la sortie du standard C++17 (ou des versions suivantes) pour utiliser les nouvelles fonctionnalités déjà supportées par nos compilateurs.

Tester le support C++17
-----------------------

Attention, la [macro **`__cplusplus`**](http://en.cppreference.com/w/cpp/preprocessor/replace#Predefined_macros) n'indique pas la version C++ supportée par le compilateur. Mais indique la version C++ activée par les options de compilation. Pour information, GCC avant 4.7 a [`__cplusplus` qui vaut `1` au lieu de `199711`](gcc.gnu.org/bugzilla/show_bug.cgi?id=1773).

```cpp
#ifdef __cplusplus
#  if __cplusplus <= 199711 // Bug GCC < 4.7
#    warning Compilé pour C++99
#  elif __cplusplus == 201103
#    warning Compilé pour C++11 (-std=c++0x ?)
#  elif __cplusplus == 201402 // Défaut GCC-6
#    warning Compilé pour C++14( -std=c++1y
#  elif __cplusplus > 201700
#    warning Compilé pour C++17 (-std=c++1z ?)
#  else
#    error Valeur inattendue __cplusplus
#  endif
#else
#  warning __cplusplus non défini
#endif
```




Deux alternatives pour vérifier le support des fonctionnalités C++ :

1. les macros [Boost.Config](http://www.boost.org/doc/libs/1_61_0/libs/config/doc/html/boost_config/boost_macro_reference.html) ;
2. les macros de [test des fonctionnalités C++](en.cppreference.com/w/cpp/experimental/feature_test#Language_Features).

Cette seconde série de macros est plus élégante, mais nécessite un compilateur récent. Voici un exemple d'utilisation :

```cpp
#if __cpp_experimental_concepts
   template<typename T>
   bool pareil (T&& a, T&& b) requires EqualityComparable<T>
   { return a == b; }
#else
   template<typename T>
   bool pareil (const T& a, const T& b)
   { return a == b; }
#endif

#if __cpp_lib_experimental_filesystem
#  include <filesystem>
   void archiver()
   { std::filesystem::copy("fichier.txt","archive.txt"); }
#else
   void archiver()
   { /* ... */ }
#endif
```

Ah ! On me signale que [GCC aurait implémenté **`__cpp_concepts`**](https://gcc.gnu.org/projects/cxx-status.html#tses), que les documents du comité de standardisation C++ parlent plutôt de [**`__cpp_concepts`**](www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0118r0.pdf) et de [**`__cpp_lib_filesystem`**](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0096r3.html), et la partie `_experimental` sera de toute façon retirée dans quelques années...

Vérifions donc avec et sans `_experimental` :

```cpp
#define SUPPORT_LANG(f) (defined(__cpp_experimental_##f)     || defined(__cpp_##f))
#define SUPPORT_LIB(f)  (defined(__cpp_lib_experimental_##f) || defined(__cpp_lib_##f))

#if SUPPORT_LANG(concepts)
   template<typename T>
   bool pareil (T&& a, T&& b) requires EqualityComparable<T>
   { return a == b; }
#else
   // ...
#endif

#if SUPPORT_LIB(filesystem)
   // ...
#else
   // ...
#endif
```



Pour aller plus loin, tester aussi la [valeur (année mois)](en.cppreference.com/w/cpp/experimental/feature_test#Language_Features) des macros `__cpp_concepts` et `__cpp_lib_filesystem` (du style `201501`).

Pour indiquer les [fonctionnalités C++ utilisées par son code](https://cmake.org/cmake/help/latest/prop_gbl/CMAKE_CXX_KNOWN_FEATURES.html) avec CMake :

```cmake
# CMake-3.1 a introduit target_compile_features() 
cmake_minimum_required(VERSION 3.1)

add_library(MaLib malib/src/lib.cpp
                  malib/include/malib/lib.h)
target_include_directories(MaLib PUBLIC malib/include)

# lib.cpp utilise le constexpr du C++11
target_compile_features(MaLib PRIVATE cxx_constexpr)

# L'en-tête publique utilise [[deprecated]] (C++14)
target_compile_features(MaLib PUBLIC cxx_attribute_deprecated)

# L'application utilise le decltype du C++11
add_executable(MonApp src/main.cpp)
target_compile_features(MonApp PRIVATE cxx_decltype)
target_link_libraries(MonApp MaLib)
```




Et toi, cher lecteur/chère lectrice de LinuxFr.org, es-tu content(e) de la disponibilité rapide des fonctionnalités des prochaines versions C++ ?
Et quand penses-tu que tu pourras utiliser ces nouvelles fonctionnalités C++ dans ton travail ?
Subis-tu l'interdiction d'utiliser C++17 ? (à cause de règles de codage figées ou de l'obligation de rester sur un vieux compilateur ?)
Et dans tes loisirs, dans combien de temps penses-tu passer au C++17 ?

---------------------------------------------------------------


Comment participer ?
--------------------
D'ici la standardisation finale C++17, le comité va s’efforcer de corriger les incohérences et les zones floues. Toute la communauté C++ est donc invitée à participer via [les dépôts Git du comité de standardisation ISO C++](https://github.com/cplusplus), notamment sur [le dépôt _"draft" (ébauche_)](https://github.com/cplusplus/draft).

[CppReference a aussi besoin de vous](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous) comme nous le disait nazcafan en 2012. D'autant plus, qu'au moment de la rédaction de cette dépêche, les pages anglaises C++17 sont incomplètes ou inexistantes, et c'est pire du côté des pages françaises !

Comme indiqué dans l’introduction, chacun peut faire profiter les autres de ses propres recherches **C++17** en enrichissant cette présentation sur le [dépôt Git *"materials"* C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md) (les personnes intéressées peuvent indiquer dans les commentaires son pseudo GitHub). Ainsi nous pourrons partager un contenu libre CC-BY-SA pour :

* Ajouter un article Wikipédia C++17 en français ;
* Organiser des conférences *(Meetup)* ;
* Publier un billet sur tout autre site ;
* ...

![Logo de la communauté C++ francophone](https://upload.wikimedia.org/wikipedia/commons/9/91/Cpp-Francophonie.svg)
