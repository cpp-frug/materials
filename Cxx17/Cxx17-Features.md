
Authors |Oliver H, Lucas et palm123
--------|------------------------------
License |CC by-sa

C++17 sera une version mineure
------------------------------

Le périmètre fonctionnel du standard C++17 vient tout juste d'être figé en deux rencontres du comité de standardisation ISO :

1. [Début mars 2016](https://isocpp.org/blog/2016/03/trip-report-jax-sutter), à Jacksonville (Floride), le comité de standardisation ISO C++ a validé quelques fonctionnalités et en a invalidé d’autres, ce qui créa une certaine déception ;
2. [Fin juin 2016](https://www.reddit.com/r/cpp/comments/4pmlpz), à Oulu (Finlande), le comité vient de clore l'ajout de nouvelles fonctionnalités.


Cette dépêche *"bookmark"* présente plusieurs des nouvelles fonctionnalités apportées par C++17 (liste non exhaustive).


![Illustration C++ de Dominic Alves sous license CC-BY-SA 2.0](https://c2.staticflickr.com/2/1116/785982209_b0da7b4380_o.jpg)

----

* [Première rencontre début mars 2016](https://isocpp.org/blog/2016/03/trip-report-jax-sutter)
* [Seconde rencontre fin juin 2016](https://www.reddit.com/r/cpp/comments/4pmlpz)
* [Dépôts Git du comité de standardisation ISO C++](https://github.com/cplusplus)
* [Article Wikipédia C++14](https://fr.wikipedia.org/wiki/C%2B%2B14)
* [Article Wikipédia C++17](https://en.wikipedia.org/wiki/C%2B%2B17)
* [Journal de rewind "C++17 est sur les rails" a propos de la première réunion](https://linuxfr.org/users/rewind/journaux/c-17-est-sur-les-rails)
* [Dépêche LinuxFr "Codeurs, Traducteurs, CppReference a besoin de vous" (2012)](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous)
* [Préparation d'une présentation basée sur cette dépêche](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md)

----

C++17 ou C++1z ?
----------------


La prochaine version du standard C++, nommée **C++17**, est prévue pour l'année prochaine (2017).


Les sceptiques qui ne sont pas certains que C++17 sortira en 2017, utilisent plutôt la dénomination **C++1z**. Ainsi **z** peut signifier `7`, `8` ou `9` (ou encore `A` en hexadécimal). Car si le nouveau standard C++ est finalement reporté à l'année 2018, son nom sera **C++18** (c'est le cas de l'[option de compilation `-std=c++1z`](https://gcc.gnu.org/projects/cxx-status.html) ou du [tag c++1z sur stackoverflow](http://stackoverflow.com/tags/c%2b%2b1z/info)).


Cette méfiance vient de **C++0x** qui n'avait pas de date butoir pour être publiée et a mis une dizaine d'année à se stabiliser pour finalement sortir en 2011. La publication était prévue avant 2010. Pour trouver une logique entre **0x** et **11**, on peut dire que **x** vaut **A** en hexadécimal (**0A** vaut **11** en base 10).


Mais bon, ceux qui suivent le nouveau process de standardisation ISO C++ sont confiants que **C++1z** verra bien le jour en 2017 (et non pas en 2018, ni après).


Fonctionnalités au niveau du langage C++
----------------------------------------

* [Attributs](http://en.cppreference.com/w/cpp/language/attributes) `[[fallthrough]]`, `[[nodiscard]]` et `[[maybe_unused]]` ;


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
    const auto [ x, y ] = fonction();
    ```

* `constexpr if`, exemple :
    
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
        // [...]
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
        // [...]
    
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

[CppReference a aussi besoin de vous](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous) comme nous le disait nazcafan en 2012. D'autant plus que les pages Anglaise C++17 sont incomplètes ou inexistantes, et c'est pire du côté des pages Françaises !


Cette dépêche LinuxFr restera figée après publication et vous souhaitez peut-être l'enrichir en donnant des exemples pour chacune des nouvelles fonctionnalités. C'est possible sur le [dépôt Git *"materials"* C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md) (lire le [`README.md`](https://github.com/cpp-frug/materials/blob/master/README.md) pour contribuer). L'idée de ce dépôt Git est de permettre le travail collaboratif et le partage de la documentation pour par exemple :

* Ajouter un article Wikipédia C++17 en Français ;
* Organiser des conférences sur ce sujet *(Meetup)* ;
* Publier un billet *(post)* sur tout autre site *(blog)* plus détaillé que l'original publié ici sur LinuxFr.

![Logo de la communauté C++ francophone](https://upload.wikimedia.org/wikipedia/commons/9/91/Cpp-Francophonie.svg)

C++17 est finalement une version mineure
----------------------------------------

Donc, aucune _grosse_ fonctionnalité majeure !

Les fonctionnalités suivantes n’ont pas été considérées comme suffisamment matures pour être inclues dans cette version du standard :

* [Concepts](http://fr.cppreference.com/w/cpp/concept) (en [Anglais](http://en.cppreference.com/w/cpp/language/constraints)) ;
* Modules, par exemple **`import std.string;`** à la place de **`#include <string>`** [*(A Module System for C++)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf) ;
* Syntaxe d'appel uniforme [*(Uniform call syntax)*](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax#C.2B.2B_proposal) ;
* [Coroutines](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0057r4.pdf).

Le comité attend de voir des implémentations satisfaisantes dans les compilateurs avant de les inclure...

Déception et nouveau process de standardisation pour C++19
----------------------------------------------------------

Cette nouvelle version C++17 apporte bon nombre de nouveautés intéressantes (et d’autres dont on ne voit pas encore l’intérêt). Cependant de nombreux développeurs C++ s’attendaient à une version majeure, un comme peu comme le C++11 avait été.

Face à la déception de cette _petite_ version mineure, le comité réfléchit à améliorer le processus de standardisation en livrant une nouvelle version tous les deux ans (au lieu de trois ans), mais aussi en facilitant la contribution de la communauté C++.

Donc, après le C++17, nous devrions avoir un C++19 avec, espérons-le, au moins une _grosse_ fonctionnalité majeure. À suivre…
