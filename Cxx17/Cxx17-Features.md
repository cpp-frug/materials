
Pour contribuer à ce document, merci de lire le [`README.md`](https://github.com/cpp-frug/materials/blob/master/README.md) |
-----------------------------------------------------------------------------------------------------|


C++17 sera une version mineure
------------------------------

Authors |Oliver H, Lucas, palm123, Benoît Sibaud et RyDroid
--------|------------------------------
License |CC by-sa


Les fonctionnalités du **C++17** ont été sélectionnées. Faisons donc le tour des nouveautés et vérifions ce titre provocateur :-)

![Illustration C++ de Dominic Alves sous license CC-BY-SA 2.0](https://c2.staticflickr.com/2/1116/785982209_b0da7b4380_o.jpg)

Cette dépêche ne détaille pas toutes les fonctionnalités. Comme cette dépêche LinuxFr.org restera figée après publication, nous vous proposons de continuer à l'enrichir sur le [dépôt Git *"materials"* C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md). Cela nous permettra de partager nos recherches individuelles et de permettre la réutilisation d'un contenu libre (CC-BY-SA) pour créer un article Wikipédia en Français, des *"Meetups"*...

----

* [Première rencontre début mars 2016 racontée par Herb Sutter](https://isocpp.org/blog/2016/03/trip-report-jax-sutter)
* [Seconde rencontre fin juin 2016](https://www.reddit.com/r/cpp/comments/4pmlpz)
* [Dépôts Git du comité de standardisation ISO C++](https://github.com/cplusplus)
* [Article Wikipédia C++14](https://fr.wikipedia.org/wiki/C%2B%2B14)
* [Article Wikipédia C++17](https://en.wikipedia.org/wiki/C%2B%2B17)
* [Journal de rewind "C++17 est sur les rails" a propos de la première réunion](https://linuxfr.org/users/rewind/journaux/c-17-est-sur-les-rails)
* [Dépêche LinuxFr "Codeurs, Traducteurs, CppReference a besoin de vous" (2012)](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous)
* [Contenu Markdown de cette dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md)
* [Première rencontre début mars 2016 très détaillée par botondballo](https://botondballo.wordpress.com/2016/03/21/trip-report-c-standards-meeting-in-jacksonville-february-2016/)
* [Seconde rencontre fin juin 2016 racontée par Herb Sutter](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/)

----

Cycle et nommage des versions
-----------------------------


Après la version majeure **C++98** (et son correctif **C++03**), un nouveau standard C++ devait être publié dans les années suivantes. Comme sa date de publication n'était pas fixée, cette version a été nommée temporairement **C++0x**. Mais avec l'ajout continuel de nouvelles fonctionnalités, le comité de standardisation n'arrivait pas à stabiliser le standard. Et finalement **C++0x** a été publié en 2011 !


Afin d'éviter tout nouveau glissement, le comité a alors décidé de publier un nouveau standard C++ tous les 3 ans, en figeant les fonctionnalités l'année N-1. Avec un cycle d'une version majeure (**C++11**) suivie d'une version mineure (**C++14**).


Bien que ce process de standardisation ISO C++ permet de publier les nouvelles versions à la date prévue, les appellations **C++1y** (pour **C++14**) et **C++1z** (pour **C++17**) perdurent. Par exemple, l'[option de compilation `-std=c++1z`](https://gcc.gnu.org/projects/cxx-status.html) ou le [tag c++1z sur stackoverflow](http://stackoverflow.com/tags/c%2b%2b1z/info).


Les membres du comité de standardisation utilisent le terme **C++17** (et non pas C++1z). Soyons confiants, **C++1z** verra bien le jour en 2017 (et non pas en 2018, ni après).


Donc en 2016 (année N-1), le comité de standardisation ISO C++ (une centaine de personnes) s'est rencontré deux fois afin de figer le périmètre fonctionnel du **C++17** :

1. [Une semaine début mars](https://isocpp.org/blog/2016/03/trip-report-jax-sutter), à Jacksonville (Floride), pour valider des fonctionnalités _mineures_ et invalider des fonctionnalités _majeures_ ;
2. [Une semaine fin juin](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/), à Oulu (Finlande), pour définitivement clore l'ajout de nouvelles fonctionnalités.

Fonctionnalités au niveau du langage C++
----------------------------------------

* Trois nouveaux [attributs standards](http://en.cppreference.com/w/cpp/language/attributes#Standard_attributes) (ce qui double le nombre d'attributs standards)
    * `[[fallthrough]]` indique au compilateur (ou à l'outil d'analyse de code) que c'est normal qu'il n'y ait pas de `break;` à la fin d'un `case`, on continue bien avec le `case` suivant. Cela évite ainsi d'avoir des avertissements _(warnings)_ inutiles.
      
      ```cpp
      switch (valeur)
      {
          case 1:
              std::cout <<"valeur 1"  "\n";
              break;
          case 2:
              std::cout <<"valeur 2"  "\n";
              [[fallthrough]]; // pas de break
          case 3:              // on continue avec le case suivant
              std::cout <<"valeur 2 ou 3"  "\n";
              break;
          case 4:
              std::cout <<"valeur 4"  "\n";
              // ici le break manque (c'est un bug)
              // => Le compilateur peut afficher un warning
          default:
              std::cout <<"valeur différente de 1, 2, 3, 4" "\n";
              break;
      }
      ```
    * `[[nodiscard]]` indique que la valeur de retour d'une fonction ne doit pas être ignorée. Ce fonctionnent était déjà implémenté par l'extension GNU `__attribute__((warn_unused_result))`.
      
      ```cpp
      // Ancienne version de la fonction affiche_division()
      // void affiche_division(int a) { std::cout << (42/a); }
      
      // Nouvelle version de la fonction affiche_division()
      [[nodiscard]] int affiche_division(int a)
      {
          if (a == 0)      // cette erreur doit être
              return -1;   // récupérée par l'appelant
          
          std::cout << (42/a);
          return 0;        // pas de problème
      }
      
      // Mais la fonction main() n'a pas été mise à jour !
      int main (int argc, char *argv[])
      {
           affiche_division(argc-1);
           // La valeur de retour est ignorée
      }    // => le compilateur peut avertir
      ```
    * `[[maybe_unused]]` [(qui devait s'appeler `[[unused]]`)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf) indique quand une variable peut ne pas être utilisée et permet donc de supprimer des avertissements _(warning)_ inutiles. Cet attribut peut s'appliquer aux fonctions, aux paramètres de fonctions et aux variables.
      
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

* Constante en virgule flottante exprimée en hexadécimal *(Hexadecimal [float point literals](http://en.cppreference.com/w/cpp/language/floating_literal))* ;


* [Allocation mémoire dynamique des données *"over-aligned"*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r3.html) ;


* [Déduction des arguments `template` des classes templates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html) ;


* [`template <auto>`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r1.html) qui permet de remplacer `MaClasse<decltype(entier),entier>` par un élégant `MaClasse<entier>` dans cet exemple :
    
    ```cpp
    // Avant C++17
    
    template <typename T, T V>
    class MaClasse
    {
        T fonction_exemple()
        {
            T x = V;
            ++x;
            return x;
        }
    };
    
    int main()
    {
        int entier = 42;
        MaClasse<decltype(entier),entier> mon_instance;
    }
    
    // Grâce à C++17
    
    template <auto V>
    class MaClasse
    {
        T fonction_exemple()
        {                    // on peut aussi
            auto x = V;      // utiliser decltype(v)
            ++x;
            return x;
        }
    };
    
    int main()
    {
        int entier = 42;
        MaClasse<entier> mon_instance;
    }

* [Guaranteed copy elision](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0135r0.html) ;


* Spécification de l'ordre d'évaluation des paramètres des fonctions dans les expressions idiomatiques du C++ [*(Fixed order-of-evaluation for idiomatic C++ expressions)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r2.pdf) ;


* [Forward progress guarantees (FPG)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0296r1.html) (voir aussi [FPGs for parallel algorithms](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0299r0.html)) ;


* Les [variables `inline`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r0.pdf) (après les [variables `template`](http://en.cppreference.com/w/cpp/language/variable_template) du C++14) ;

* `if(init;condition)` et `switch(init;condition)` pour faire un peu comme `for(init;cond;inc)` [*(If statement with initializer)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r0.html) ;


* Sucre synthaxique pour les [`namespace`](http://en.cppreference.com/w/cpp/language/namespace)s imbriqués  *(nested)*  
  Exemple : **`namespace A::B {`** correspond à **`namespace A { namespace B {`** ;

* Liaison entre retour de fonction structuré et variables locales [*(Structured bindings)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r2.html), exemple :
    
    ```cpp
    struct Structure { int a; double b; };
    Structure fonction();
    auto [ x, y ] = fonction();
    ```

* [`if constexpr`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0128r1.html) (initialement [`constexpr_if` et `constexpr_else`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0128r0.html), et encore avant c'était `static_if` et `static_else`)
    
    ```cpp
    // ----- Trois définitions avant C++17 -----
    
    void fonction_variadique_template() 
    {
        // Pas d'argument => Ne fait rien
    }
    
    template <class T>
    void fonction_variadique_template (const T& t) 
    {
        // Gère un seul argument T
        std::cout << t << std::endl;
    }
    
    template <class T, class... Reste> 
    void fonction_variadique_template (const T& t, const Reste&... r) 
    {
        fonction_variadique_template(t); 
        fonction_variadique_template(r...); // Gère le reste
    }
    
    // ----- Une seule définition grâce à C++17 -----
    
    template <class T, class... Reste> 
    void fonction_variadique_template (const T& t, const Reste&... r) 
    {
        // Gère un seul argument T
        std::cout << t << std::endl;
    
        // Gère le reste
        if constexpr (sizeof...(r))
            fonction_variadique_template(r...);
    }
    ```   

Fonctionnalités au niveau de la bibliothèque STL
------------------------------------------------

* Suppression des [digraphes et trigraphes](https://en.wikipedia.org/wiki/Digraphs_and_trigraphs#Removal_of_trigraphs) ;


* Ajout des [`std::optional`](http://en.cppreference.com/w/cpp/utility/optional), [`std::any`](http://en.cppreference.com/w/cpp/utility/any), [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view) et [autres extensions](http://en.cppreference.com/w/cpp/experimental/lib_extensions#Merged_into_C++17) (une partie des *Library Fundamentals TS v1*) ;


* Ajout des [versions parallélisées de 69 algorithmes](http://en.cppreference.com/w/cpp/experimental/parallelism) *(Parallelism TS v1)* ;


* Ajout [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem) *(File System TS v1)* ;


* Ajout des [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math) ;


* Ajout `hardware_*_interference_size` ;


* Ajout `.is_always_lockfree()` ;


* Ajout [`std::clamp()`](http://en.cppreference.com/w/cpp/algorithm/clamp). Par exemple, `std::clamp(x,4,8)` est l'équivalent de `std::min(std::max(x,4),8)`.

* Ajout des fonctions `string::data()` non-const ;


* C++17 est maintenant basé sur C11 au lieu de C99 [*(C++17 refers to C11 instead of C99)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r2.html) ;


* `std::variant<type1, type2, type3>` [*(Variant: a type-safe union for C++17)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r2.html) ;


* `destroy(_at|_n)`, `uninitialized_move(_n)`, `uninitialized_value_construct(_n)`, `uninitialized_default_construct(_n)` [*(Extending memory management tools)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r2.html) ;


* Ajout des fonctions `std::set::splice()`, `std::map::splice()`, `std::unordered_set::splice()` et `std::unordered_map::splice()` comme pour [`std::list::splice()`](http://fr.cppreference.com/w/cpp/container/list/splice) [*(Splicing Maps and Sets)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r2.pdf) ;

* Afin de se permettre dans l'avenir de casser la rétrocompatibilité, on prépare le terrain en réservant le nommage `std[0-9]+` pour d'éventuelles futures versions de la ~~STL~~ bibliothèque standard C++ [*(Reserve a New Library Namespace Future Standardization)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0180r1.html).

C++17 fait l'impasse sur des fonctionnalités _majeurs_
------------------------------------------------------

Deux _gros_ morceaux ont été inclus dans **C++17** :


* le Parralélisme avec les [69 algorithmes parralélisées](http://en.cppreference.com/w/cpp/experimental/parallelism) ;
* et [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem).


Par contre, les fonctionnalités suivantes n’ont pas été considérées comme suffisamment matures pour être incluses :

* [Concepts](http://fr.cppreference.com/w/cpp/concept) (voir aussi la [version en Anglais](http://en.cppreference.com/w/cpp/language/constraints)) ;
* Modules, par exemple **`import std.string;`** à la place de **`#include <string>`** [*(A Module System for C++)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf) ;
* Syntaxe d'appel uniforme [*(Uniform call syntax)*](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax#C.2B.2B_proposal) ;
* [Coroutines](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0057r4.pdf) ;
* Réseau [_(Networking)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) ;
* Tableaux [_(Array)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3820.html). Une idée de 2013, mais finalement abandonnée ;
* [_Ranges_](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf) ;
* Mémoire Transactionnelle [_(Transactional Memory)_](http://en.cppreference.com/w/cpp/language/transactional_memory) ;
* Réflexion [_(Static Reflection)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0194r1.html) ;
* et autres extensions majeures à la bibliothèque standard. 

Le comité attend de voir des implémentations satisfaisantes dans les compilateurs avant de les inclure...

Même si **C++17** va un peu plus transcender notre façon de coder en C++, de nombreux développeurs s’attendaient à une version majeure (révolutionnaire). Par rapport à **C++11**, les apports du **C++17** ressemblent plus à une version mineure.

![Évolution des fonctionnalités majeures](https://herbsutter.files.wordpress.com/2016/06/wg21-timeline.png)


Déception et nouveau process de standardisation pour C++19
----------------------------------------------------------

Face à la déception de cette version _pas très majeure_, le comité réfléchit à faciliter la contribution de la communauté C++ et à améliorer le processus de standardisation :


* Une nouvelle version tous les deux ans (au lieu de trois ans) ;
* Chaque version inclura toutes les fonctionnalités prêtes l'année N-1 (au lieu d'avoir une alternance de versions majeurs/mineures).

Donc, après le **C++17**, nous devrions avoir un **C++19**. avec, espérons-le, des fonctionnalités majeures. À suivre…


Et toi, cher lecteur LinuxFr, es-tu un peu déçu du périmètre fonctionnel C++17 ? Souhaites-tu des version C++ plus fréquentes ?

Support des compilateurs
------------------------


* Mai 2013, [**GCC-4.8.1**](https://gcc.gnu.org/gcc-4.8/changes.html) est annoncé comme le [premier compilateur](https://gcc.gnu.org/projects/cxx-status.html#cxx11) a supporter pleinement C++11 ;
* Janvier 2014, [**Clang-3.4**](http://llvm.org/releases/3.4/tools/clang/docs/ReleaseNotes.html) est annoncé comme le [premier compilateur](http://clang.llvm.org/cxx_status.html#cxx14) à supporter pleinement C++14 ;
* Avril 2015, [**GCC-5.1**](https://gcc.gnu.org/gcc-5/changes.html) est annoncé comme supporter pleinement C++14 ;
* Mai 2016, la bibliothèque `boost::hana` est enfin intégrée à `boost` car au moins deux compilateurs supportent les fonctionnalités C++14 utilisées par cette bibliothèque, c'est à dire **Clang-3.5** et **GCC-6** (les versions précédentes ne supportent donc pas pleinement le C++14) ;
* été 2017, c'est peut-être au tour de Visual C++ d'être annoncé comme étant le premier compilateur à pleinement supporter C++17...


Support des fonctionnalités C++17 :


* sur [cppreference](http://en.cppreference.com/w/cpp/compiler_support) ;
* sur le site officiel [GCC](https://gcc.gnu.org/projects/cxx-status.html#cxx1z) ;
* sur le site officiel [Clang](http://clang.llvm.org/cxx_status.html#cxx17) et sa [libcxx](http://libcxx.llvm.org/cxx1z_status.html) ;
* sur le _blog_ [Visual C++](https://msdn.microsoft.com/fr-fr/library/hh567368.aspx) [(version en Anglais)](https://blogs.msdn.microsoft.com/vcblog/2015/06/19/c111417-features-in-vs-2015-rtm/).


Et toi, cher lecteur LinuxFr, pour quelle années penses-tu pouvoir utiliser les fonctionnalités C++17 dans ton travail ? Dans tes loisirs ? 

Comment participer ?
--------------------
D'ici la standardisation finale C++17, le comité va s’efforcer de corriger les incohérences et les zones floues. Toute la communauté C++ est donc invitée à participer via [les dépôts Git du comité de standardisation ISO C++](https://github.com/cplusplus), notamment sur [le dépôt _"draft" (ébauche_)](https://github.com/cplusplus/draft).

[CppReference a aussi besoin de vous](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous) comme nous le disait nazcafan en 2012. D'autant plus que les pages anglaises C++17 sont incomplètes ou inexistantes, et c'est pire du côté des pages françaises !


Comme indiqué dans l’introduction, chacun peut faire profiter les autres de ses propres recherches **C++17** en enrichissant cette présentation sur le [dépôt Git *"materials"* C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md) (les personnes intéressées peuvent indiquer dans les commentaires son pseudo Github). Ainsi nous pourrons partager un contenu libre CC-BY-SA pour :

* Ajouter un article Wikipédia C++17 en Français ;
* Organiser des conférences *(Meetup)* ;
* Publier un billet sur tout autre site ;
* ...
![Logo de la communauté C++ francophone](https://upload.wikimedia.org/wikipedia/commons/9/91/Cpp-Francophonie.svg)
