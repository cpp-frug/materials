
Pour contribuer à ce document, merci de lire le [`README.md`](https://github.com/cpp-frug/materials/blob/master/README.md) |
-----------------------------------------------------------------------------------------------------|


C++17 sera une version mineure
------------------------------

Authors |Oliver H, Lucas, palm123, Benoît Sibaud et RyDroid
--------|------------------------------
License |CC by-sa


Les fonctionnalités du **C++17** viennent tout juste d'être sélectionnées. Faisons donc le tour des nouveautés :-)

![Illustration C++ de Dominic Alves sous license CC-BY-SA 2.0](https://c2.staticflickr.com/2/1116/785982209_b0da7b4380_o.jpg)

Pour des questions de *"timing"*, la rédaction de cette dépêche n'est pas complète. De plus, cette dépêche LinuxFr.org restera figée après publication. Nous vous proposons donc de continuer à l'enrichir sur le [dépôt Git *"materials"* C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md). Cela nous permettra de partager nos recherches individuelles et de permettre la réutilisation d'un contenu libre (CC-BY-SA) pour des *"Meetups"*, la création d'un article Wikipédia en Français...

----

* [Première rencontre début mars 2016](https://isocpp.org/blog/2016/03/trip-report-jax-sutter)
* [Seconde rencontre fin juin 2016](https://www.reddit.com/r/cpp/comments/4pmlpz)
* [Dépôts Git du comité de standardisation ISO C++](https://github.com/cplusplus)
* [Article Wikipédia C++14](https://fr.wikipedia.org/wiki/C%2B%2B14)
* [Article Wikipédia C++17](https://en.wikipedia.org/wiki/C%2B%2B17)
* [Journal de rewind "C++17 est sur les rails" a propos de la première réunion](https://linuxfr.org/users/rewind/journaux/c-17-est-sur-les-rails)
* [Dépêche LinuxFr "Codeurs, Traducteurs, CppReference a besoin de vous" (2012)](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous)
* [Contenu Markdown de cette dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md)

----

Cycle et nommage des versions
-----------------------------


Après la version majeure **C++98** (et son correctif **C++03**), un nouveau standard C++ devait être publié dans les années suivantes. Comme sa date de publication n'était pas fixée, cette version a été nommée temporairement **C++0x**. Mais avec l'ajout continuel de nouvelles fonctionnalités, le comité de standardisation n'arrivait pas à stabiliser le standard. Et finalement **C++0x** a été publié en 2011 !


Afin d'éviter tout nouveau glissement, le comité a alors décidé de publier un nouveau standard C++ tous les 3 ans, en figeant les fonctionnalités l'année N-1. Avec un cycle d'une version majeure (**C++11**) suivie d'une version mineure (**C++14**).


Bien que ce process de standardisation ISO C++ permet de publier les nouvelles versions à la date prévue, les appellations **C++1y** (pour **C++14**) et **C++1z** (pour **C++17**) perdurent. Par exemple, l'[option de compilation `-std=c++1z`](https://gcc.gnu.org/projects/cxx-status.html) ou le [tag c++1z sur stackoverflow](http://stackoverflow.com/tags/c%2b%2b1z/info).


Les membres du comité de standardisation utilisent le terme **C++17** (et non pas C++1z). Soyons confiants, **C++1z** verra bien le jour en 2017 (et non pas en 2018, ni après).


Donc en 2016 (année N-1), le comité de standardisation ISO C++ (une centaine de personnes) s'est rencontré deux fois afin de figer le périmètre fonctionnel du **C++17** :

1. [Une semaine début mars](https://isocpp.org/blog/2016/03/trip-report-jax-sutter), à Jacksonville (Floride), pour valider des fonctionnalités _mineures_ et invalider des fonctionnalités _majeures_ ;
2. [Une semaine fin juin](https://www.reddit.com/r/cpp/comments/4pmlpz), à Oulu (Finlande), pour définitivement clore l'ajout de nouvelles fonctionnalités.

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
    * `[[nodiscard]]` indique que la valeur de retour d'une fonction ne doit pas être ignorée. Il y a une extension GNU qui proposait déjà cette fonctionnalité : `__attribute__((warn_unused_result))`.
      
      ```cpp
      // Ancienne version de la fonction foo()
      // void foo(int a) { std::cout << (42/a); }
      
      // Nouvelle version de la fonction foo()
      [[nodiscard]] int foo(int a)
      {
          if (a == 0)      // cette erreur doit être
              return -1;   // récupérée par l'appelant
          
          std::cout << (42/a);
          return 0;        // pas de problème
      }
      
      // la fonction main() utilise l'ancienne version de foo()
      int main (int argc, char *argv[])
      {
           foo (argc-1);  // Valeur de retour ignorée
      }                   // => le compilateur peut avertir
      ```
    * `[[maybe_unused]]` [(qui devait s'appeler `[[unused]]`)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf) indique quand une variable peut ne pas être utilisée et permet donc de supprimer des avertissements _(warning)_ inutiles. Cet attribut peut s'appliquer aux fonctions, aux paramètres de fonctions et aux variables.
      
      ```cpp
      [[maybe_unused]] void foo (int a)
      { std::cout << (42/a); }
      
      int main (int argc, [[maybe_unused]] char *argv[])
      {
           [[maybe_unused]] bool impaire = argc % 2;
           assert(impaire); // assert() est généralement désactivé 
      }                     // en mode Release (-DNDEBUG)
      
      // Avant, des macros permettaient d'éviter les warnings
      #ifdef DOXYGEN_PARSING
      #  define DOC_ONLY(x) x
      #else
      #  define DOC_ONLY(x)
      #endif
      
      #ifdef NDEBUG
      #  define DEBUG_ONLY(x)
      #else
      #  define DEBUG_ONLY(x) x
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


* Les boucles `for` *"each"* supportent des `begin()` `end()` retournant des types différents mais compatibles [*(Generalizing the Range-Based For Loop)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) ;


* Constante en virgule flottante exprimée en hexadécimal *(Hexadecimal [float point literals](http://en.cppreference.com/w/cpp/language/floating_literal))* ;


* [Allocation mémoire dynamique des données *"over-aligned"*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r3.html) ;


* [Déduction des arguments `template` des classes templates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html) ;


* [`template <auto>`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r1.html) ;


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

* `constexpr if`
    
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
        constexpr if (sizeof...(r))
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


* Ajout `clamp()` ;


* Ajout des fonctions `string::data()` non-const ;


* C++17 est maintenant basé sur C11 au lieu de C99 [*(C++17 refers to C11 instead of C99)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r2.html) ;


* `std::variant<type1, type2, type3>` [*(Variant: a type-safe union for C++17)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r2.html) ;


* `destroy(_at|_n)`, `uninitialized_move(_n)`, `uninitialized_value_construct(_n)`, `uninitialized_default_construct(_n)` [*(Extending memory management tools)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r2.html) ;


* Ajout des fonctions `std::set::splice()`, `std::map::splice()`, `std::unordered_set::splice()` et `std::unordered_map::splice()` comme pour [`std::list::splice()`](http://fr.cppreference.com/w/cpp/container/list/splice) [*(Splicing Maps and Sets)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r2.pdf) ;

* Afin de se permettre dans l'avenir de casser la rétrocompatibilité, on prépare le terrain en réservant le nommage `std[0-9]+` pour d'éventuelles futures versions de la ~~STL~~ bibliothèque standard C++ [*(Reserve a New Library Namespace Future Standardization)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0180r1.html).

Comment participer ?
--------------------


D'ici la standardisation finale C++17, le comité va s’efforcer de corriger les incohérences et les zones floues. Toute la communauté C++ est donc invitée à participer via [les dépôts Git du comité de standardisation ISO C++](https://github.com/cplusplus), notamment sur [le dépôt _"draft" (ébauche_)](https://github.com/cplusplus/draft).

[CppReference a aussi besoin de vous](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous) comme nous le disait nazcafan en 2012. D'autant plus que les pages anglaises C++17 sont incomplètes ou inexistantes, et c'est pire du côté des pages françaises !

Comme indiqué dans l’introduction, chacun peut faire profiter les autres de ses recherches **C++17** en enrichissant cette dépêche sur le [dépôt Git *"materials"* C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md). Ainsi nous pourrons partager un contenu libre CC-BY-SA pour :

* Ajouter un article Wikipédia C++17 en Français ;
* Organiser des conférences sur ce sujet *(Meetup)* ;
* Publier un billet *(post)* sur tout autre site *(blog)* ;
* ...

![Logo de la communauté C++ francophone](https://upload.wikimedia.org/wikipedia/commons/9/91/Cpp-Francophonie.svg)

C++17 est finalement une version mineure
----------------------------------------

Donc, aucune _grosse_ fonctionnalité majeure !

Les fonctionnalités suivantes n’ont pas été considérées comme suffisamment matures pour être incluses dans cette version du standard :

* [Concepts](http://fr.cppreference.com/w/cpp/concept) (en [Anglais](http://en.cppreference.com/w/cpp/language/constraints)) ;
* Modules, par exemple **`import std.string;`** à la place de **`#include <string>`** [*(A Module System for C++)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf) ;
* Syntaxe d'appel uniforme [*(Uniform call syntax)*](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax#C.2B.2B_proposal) ;
* [Coroutines](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0057r4.pdf).

Le comité attend de voir des implémentations satisfaisantes dans les compilateurs avant de les inclure...

Déception et nouveau process de standardisation pour C++19
----------------------------------------------------------

Cette nouvelle version C++17 apporte bon nombre de nouveautés intéressantes (et d’autres dont on ne voit pas encore l’intérêt). Cependant de nombreux développeurs C++ s’attendaient à une version majeure, un peu comme le C++11 l'avait été.

Face à la déception de cette _petite_ version mineure, le comité réfléchit à améliorer le processus de standardisation en livrant une nouvelle version tous les deux ans (au lieu de trois ans), mais aussi en facilitant la contribution de la communauté C++.

Donc, après le C++17, nous devrions avoir un C++19 avec, espérons-le, au moins une _grosse_ fonctionnalité majeure. À suivre…
