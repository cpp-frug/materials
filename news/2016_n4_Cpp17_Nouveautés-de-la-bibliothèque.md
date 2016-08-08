Fonctionnalités au niveau de la bibliothèque standard
-----------------------------------------------------
    
Petit rappel, l'ensemble des fonctionnalités `std::*` ne s'appelle plus [**STL**](https://fr.wikipedia.org/wiki/Standard_Template_Library) _(Standard Template Library)_, mais [**bibliothèque standard du C++**](https://fr.wikipedia.org/wiki/Biblioth%C3%A8que_standard_du_C%2B%2B) _(C++ Standard Library)_.

* Suppression des [digraphes et trigraphes](https://en.wikipedia.org/wiki/Digraphs_and_trigraphs#Removal_of_trigraphs).
    
    ```cpp
    TODO Fournir un exemple
    ```
    
    Certaines entreprises maintiennent du très vieux code C/C++ contenant des digraphes/trigraphes. Ces digraphes/trigraphes peuvent être replacés par les caractères correspondant avec un script. Mais ces entreprises préfèrent que les compilateurs conservent cette complexité et que les développeurs aient des surprises quand ils utilisent certains caractères.
     
    La dépréciation des digraphes/trigraphes avait été prévue en 2009 pour C++11. Mais certains membres comme IBM et Bloomberg étaient réticents. Finalement, c'est la suppression pure et simple qui a été votée par les membres pour C++17 (sans passer par la dépréciation). IBM a même tenté une dernière [tentative pour conserver les digraphes/trigraphes](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4210.pdf) ;

* Ajout des [versions parallélisées de 69 algorithmes](http://en.cppreference.com/w/cpp/experimental/parallelism) *(Parallelism TS v1)* ;
    
    ![Deux cochons en position 69](http://vignette3.wikia.nocookie.net/necyklopedie/images/8/80/Porno_prase.png/revision/latest?cb=20090116191951)

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



