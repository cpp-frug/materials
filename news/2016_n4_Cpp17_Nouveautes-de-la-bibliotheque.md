Fonctionnalités au niveau de la bibliothèque standard
=====================================================

La STL
======
    
Petit rappel, l'ensemble des fonctionnalités `std::*` ne s'appelle plus [**STL**](https://fr.wikipedia.org/wiki/Standard_Template_Library) _(Standard Template Library)_, mais [**bibliothèque standard du C++**](https://fr.wikipedia.org/wiki/Biblioth%C3%A8que_standard_du_C%2B%2B) _(C++ Standard Library)_.
    
    TODO Rappeler l'historique de la STL à la std, Mieux expliquer


Résumé
======
    
* Les [algorithmes parallélisés](http://en.cppreference.com/w/cpp/experimental/parallelism#Parallelized_versions_of_existing_algorithms) (si multitâche performant) ;
* [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view) (pour utiliser les méthodes de std::string sur des const char* sans faire de ré-allocation inutile) ;
* Les transfuges de chez [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) :

`boost::*` | `std::*`
-----------|---------
[`boost::filesystem`](http://www.boost.org/libs/filesystem) | -> [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem)
[`boost::variant`](http://www.boost.org/libs/variant) | -> [`std::variant`](http://en.cppreference.com/w/cpp/utility/variant)
[`boost::any`](http://www.boost.org/libs/any) | -> [`std::any`](http://en.cppreference.com/w/cpp/utility/any)
[`boost::optional`](http://www.boost.org/libs/optional) | -> [`std::optional`](http://en.cppreference.com/w/cpp/utility/optional)
[`boost::math`](http://www.boost.org/libs/math) | -> [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math)

Par contre, les fonctionnalités majeures très attendues, comme les [intervalles *(Ranges)*](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf) ou le [réseau _(Networking)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) seront publiées pour une autre version du C++.



Nouvelles structures de données
===============================

Le *TS* [[N4480]](https://wg21.link/n4480) intégre trois nouvelles structures de données que nous allons aborder en trois sections (le numéro de ce *TS* sera dupliqué dans cacun de ces titres de section). Ce chapitre termine par un second *TS*, le [[P0088]](https://wg21.link/p0088), pour une quatrième structure de donnée.

[[N4480]](https://wg21.link/n4480) `optional`, `any`, `string_view`...
----------------------------------------------------------------------
    
* [`std::optional<>`](http://en.cppreference.com/w/cpp/utility/optional) en s'inspirant de [`boost::optional<>`](http://www.boost.org/doc/libs/1_61_0/libs/optional) ;
* [`std::any`](http://en.cppreference.com/w/cpp/utility/any) en s'inspirant de [`boost::any`](http://www.boost.org/doc/libs/1_61_0/libs/any) ;
* [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view) ;
* et [autres extensions](http://en.cppreference.com/w/cpp/experimental/lib_extensions#Merged_into_C++17).


[[P0088]](https://wg21.link/p0088) `std::variant`
------------------------------------------------
    
* Ajout du `std::variant` [*(type-safe union for C++17)*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r2.html) et d'une partie des [*Library Fundamentals TS v1*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) :
* [`std::variant<int,char,float>`](http://en.cppreference.com/w/cpp/utility/variant) en s'inspirant de [`boost::variant<>`](http://www.boost.org/doc/libs/1_61_0/libs/variant) (certains auraient aimé la possibilité d’interdire un objet `std::variant` vide et l'optimisation du `std::variant` pour les types légers) ;
    



Invoke
======

[[N4169]](https://wg21.link/n4169) `std::invoke`
-----------------------------------------------
    
    TODO


[[N4480]](https://wg21.link/n4480) `std::apply`
----------------------------------------------
    
    TODO


[[P0077]](https://wg21.link/p0077) `std::is_callable`
----------------------------------------------------
    
    TODO


[[P0209]](https://wg21.link/p0209) `std::make_from_tuple` et `std::apply`
------------------------------------------------------------------------
    
    TODO


File System TS v1
=================

Ajout de [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem). Enfin le C++ dispose d'une API standardisée pour gérer fichiers et répertoires ! 
    
    TODO fournir un exemple
    
C'est une longue histoire :
    
* 2003 [`boost::filesystem`](http://www.boost.org/doc/libs/1_61_0/libs/filesystem) ;
* 2004 [requête pour intégration dans la bibliothèque standard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1576.html) ;
* 2005 [première proposition détaillée pour intégration dans la bibliothèque standard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1841.html) ;
* Il aura fallu une dizaine d'années et trois versions majeures pour permettre au groupe d'étude SW3 _(Study Group 3)_ de rédiger l'ultime spécification technique _(TS)_ [N4100 (le titre est en français dans le document)](https://wg21.link/n4100) qui correspond au standard [ISO/IEC TS 18822:2015](http://www.iso.org/iso/catalogue_detail.htm?csnumber=63483) ;
* L'implémentation de `std::experimental::filesystem` sur plusieurs plateformes et compilateurs ([Visual C++ 2012/2013/2015](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/msdn.microsoft.com/en-us/library/hh874694.aspx) et [GCC-5.3](https://gcc.gnu.org/onlinedocs/libstdc++/manual/using_dynamic_or_shared.html#manual.intro.using.linkage.experimental)) a été nécessaire pour décider de l'intégration dans la bibliothèque standard.


Le *TS* [[P0218]](https://wg21.link/p0218) propose d'intégrer `boost::filesystem` dans C++17 avec quelques différences.

* `[class.path]`
* `[class.filesystem.error]`
* `[class.file_status]`
* `[class.directory_entry]`
* `[class.directory_iterator]` and `[class.recursive_directory_iterator]`
* `[fs.ops.funcs]`



Threading
=========

[[N4071]](https://wg21.link/n4071) Parallelism TS v1
----------------------------------------------------
    
    TODO


[[N4508]](https://wg21.link/n4508) `std::shared_mutex`
-----------------------------------------------------
    
    TODO


[[P0152]](https://wg21.link/p0152) `atomic<T>::is_always_lockfree`
--------------------------------------------------------------------

Ajout de `.is_always_lockfree()`.
    
    TODO


[[P0154]](https://wg21.link/p0154) Ajout `hardware_*_interference_size`
----------------------------------------------------------------------
    
    TODO


[[P0156]](https://wg21.link/p0156) `lock_guard<Mutexes...>`
----------------------------------------------------------
    
    TODO


Library Fundamentals TS v1
==========================

[[N4480]](https://wg21.link/n4480) xxxxxxxxxxxxxx
-------------------------------------------------

* `[func.searchers]` and `[alg.search]`
* `[pmr]`
* `std::sample`, sampling from a range?


[[P0220]](https://wg21.link/p0220) xxxxxxxxxxxxxx
-------------------------------------------------
    
    TODO


Amélioration des conteneurs
===========================

[[N4279]](https://wg21.link/n4279) `try_emplace` et `insert_or_assign`
---------------------------------------------------------------------
    
    TODO


[[N4280]](https://wg21.link/n4280) Fonctions globales `std::size()`, `std::empty()` et `std::data()`
---------------------------------------------------------------------------------------------------
    
    TODO


[[N4284]](https://wg21.link/n4284) Contiguous iterator `concept`
---------------------------------------------------------------
    
    TODO


[[N4510]](https://wg21.link/n4510) Minimal incomplete type support in containers
--------------------------------------------------------------------------------
    
    TODO


[[P0031]](https://wg21.link/p0031) Itérateurs `constexpr` 
--------------------------------------------------------
    
    TODO


[[P0083]](https://wg21.link/p0083) Splicing for `map<>`, `unordered_map<>`, `set<>` et `unordered_set<>`
-------------------------------------------------------------------------------------------------------
    
Ce TS *Splicing Maps and Sets* ajoute des fonctions `std::set::splice()`, `std::map::splice()`, `std::unordered_set::splice()` et `std::unordered_map::splice()` comme pour [`std::list::splice()`](http://fr.cppreference.com/w/cpp/container/list/splice).
    
    TODO


[[P0084]](https://wg21.link/p0084) Les fonctions `emplace()` retournent maintenant une référence vers l'objet fraichement créé
------------------------------------------------------------------------------------------------------------------------------
    
    TODO


[[P0272]](https://wg21.link/p0272) Fonction `string::data()` non-`const`
-----------------------------------------------------------------------
    
Ajout des fonctions `std::string::data()` non-const.



Smart pointer
=============

[[N4089]](https://wg21.link/n4089) Corrections `unique_ptr<T[]>`
---------------------------------------------------------------
    
    TODO


[[N4366]](https://wg21.link/n4366) Autres corrections `unique_ptr`
-----------------------------------------------------------------
    
    TODO


[[P0033]](https://wg21.link/p0033) `weak_from_this`
--------------------------------------------------
    
    TODO



Amélioratons sur d'autres structures de données
===============================================

[[N4387]](https://wg21.link/n4387) Construction `{}` pour `std::tuple`
---------------------------------------------------------------------
    
    TODO


[[N4277]](https://wg21.link/n4277) TriviallyCopyable reference_wrapper, can be performance boost
------------------------------------------------------------------------------------------------
    
    TODO



Ajout des [versions parallélisées de 69 algorithmes](http://en.cppreference.com/w/cpp/experimental/parallelism) *(Parallelism TS v1)* ;
    
    ![Deux cochons en position 69](http://vignette3.wikia.nocookie.net/necyklopedie/images/8/80/Porno_prase.png/revision/latest?cb=20090116191951)


Fonctions mathématiques
=======================



[[N3060]](https://wg21.link/n3060) Fonctions spéciales mathématiques
--------------------------------------------------------------------
     
Les [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math) sont discuttées au comité de normalisation du C++ depuis plus d'une dizaine d'années. Avec un peu d'archéologie, on retrouve la *TS* [[N1422]](https://wg21.link/n1422) qui en parlait déjà en 2003 !
    
En 2007, ces fonctions étaient déjà dans le wagon de la `std` TR1 avec la norme [ISO/IEC TR 19768:2007](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=43289).
Puis en 2010, ces fonctions sont sorties du TR1 pour représenter une norme ISO à part, la norme [ISO/IEC 29124:2010](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=50511).
Et ce n'est que pour 2017, que ces [fonctions](http://en.cppreference.com/w/cpp/numeric/special_math) sont enfin intégrée au C++ !
    
Mais les matheux pouvaient déjà utiliser [`boost::math`](http://www.boost.org/libs/math)
qui a été l'implementation de test avant intégration au standard C++.
Son [dépôt Git](https://github.com/boostorg/math) montre une existance depuis 2001 avec une activité importante depuis 2006 (première version livrée). 
    
Ci-dessous un apperçut des domaines mathématiques couverts par cette bibliothèque.
C'est un sacré morceau, et je ne sais pas trop comment les éditeurs de biblithèque standard C++
vont s'y prendre pour implémenter avec leur droit d'auteur une telle bibliothèque de qualité et performante...
Car si ces éditeur (GNU, LLVM, Microsoft, Intel...) réutilisent la [`boost::math`](http://www.boost.org/libs/math),
alors ils auront à repsecter la [Boost Software License](http://www.boost.org/LICENSE_1_0.txt).
    
* [Polynômes de Laguerre généralisés](https://fr.wikipedia.org/wiki/Polyn%C3%B4me_de_Laguerre#Polyn.C3.B4mes_de_Laguerre_g.C3.A9n.C3.A9ralis.C3.A9s)
* [Polynômes associés de Legendre](https://fr.wikipedia.org/wiki/Polyn%C3%B4mes_associ%C3%A9s_de_Legendre)
* [Fonction bêta](https://fr.wikipedia.org/wiki/Fonction_b%C3%AAta)
* [Intégrales elliptiques](https://fr.wikipedia.org/wiki/Int%C3%A9grale_elliptique)
* [Fonctions de Bessel](https://fr.wikipedia.org/wiki/Fonction_de_Bessel)
* [Exponentielle intégrale](https://fr.wikipedia.org/wiki/Exponentielle_int%C3%A9grale)
* [Polynôme d'Hermite](https://fr.wikipedia.org/wiki/Polyn%C3%B4me_d%27Hermite)
* [Fonction zêta de Riemann](https://fr.wikipedia.org/wiki/Fonction_z%C3%AAta_de_Riemann) 
    
L'avantage de celle de `boost::` est qu'elle est compatible avec une très grande variété de compilateurs, même de très anciens.
Alors qu'une application utilisant celle de `std::` requiera un compilateur compatible C++17.
    
Chère léctrice, cher lecteur *LinuxFr.org*, as-tu déjà utilisé [`boost::math`](http://www.boost.org/libs/math).
Peux-tu partager ton retour d'expérience dans les commentaires ?
Quelles sont tes attentes avec cette intégration dans la `std::` ?
Penses-tu utiliser un jour la version de la `std::` plutôt quer celle de `boost::` ?


[[P0025]](https://wg21.link/p0025) `std::clamp(x,4,8) == std::min(std::max(x,4),8)`
----------------------------------------------------------------------------------

Ajout de [`std::clamp()`](http://en.cppreference.com/w/cpp/algorithm/clamp).

Exemple pour borner x dans l'intervalle [4, 8] :
    
```cpp
// C++14
auto x = std::max(4,std::min(x,8));

// C++17
auto x = std::clamp(x,4,8);
```    



Améliorations diverses
======================

[[P0180]](https://wg21.link/p0180) Mots-clés `std[0-9]+` réservés pour de futures versions de la `std::`
-------------------------------------------------------------------------------------------------------
    
Ce TS *Reserve a New Library Namespace Future Standardization* résèrve tous les mots-clés `std[0-9]+` pour le nommage d'éventuelles futures versions de la ~~STL~~ bibliothèque standard C++ qui casseraient la rétrocompatibilité.



[[P0040]](https://wg21.link/p0040) `destroy(_at|_n)`, `uninitialized_move(_n)`, `uninitialized_value_construct(_n)`, `uninitialized_default_construct(_n)`
---------------------------------------------------------------------------------------------------------------------------------------------------------

Ce TS *Extending memory management tools* ajoute :

* `destroy(_at|_n)`
* `uninitialized_move(_n)`
* `uninitialized_value_construct(_n)`
* `uninitialized_default_construct(_n)`
    
    TODO liens vers cppref + explications 


[[N3911]](https://wg21.link/n3911) `std::void_t<T>`
--------------------------------------------------
    
    TODO


[[N4258]](https://wg21.link/n4258) Fonctions `noexcept` pour `std::*`
--------------------------------------------------------------------
    
    TODO


[[N4259]](https://wg21.link/n4259) `std::uncaught_exceptions`
------------------------------------------------------------
    
    TODO


[[N4389]](https://wg21.link/n4389) `std::bool_constant`
------------------------------------------------------
    
    TODO


[[P0005]](https://wg21.link/p0005) `std::not_fn`
-----------------------------------------------
    
    TODO


[[P0006]](https://wg21.link/p0006) Les variables `*_v` pour SFINAE
------------------------------------------------------------------
    
    TODO


[[P0007]](https://wg21.link/p0007) `std::as_const`
-------------------------------------------------
    
    TODO


[[P0013]](https://wg21.link/p0013) `std::conjunction`, `std::disjunction` et `std::negation`
-------------------------------------------------------------------------------------------
    
    TODO


[[P0074]](https://wg21.link/p0074) `std::owner_less<void>` comme `std::less<void>` mais pour les *smart pointers*
-----------------------------------------------------------------------------------------------------------------
    
Cela sert à trier les *smart pointers* indépendament de l'objet contenu. 


[[P0092]](https://wg21.link/p0092) Corrections pour `std::chrono`
----------------------------------------------------------------
    
    TODO

[[P0067]](https://wg21.link/p0067) `std::to_chars` et `std::from_chars`
----------------------------------------------------------------------

Des fonctions de conversion **ASCII <-> nombres** haute performance ignorant les *locales*.
Enfin, plus besoin de réinventer la roue pour les nombreuses bibliothèques qui sérialisent/désérialisent entre les formats lisibles aux humains (HTML/XML/JSON/YAML...)  et les formats binaires lisibles par la machine.


[[P0137]](https://wg21.link/p0137) `std::launder`
------------------------------------------------
    
    TODO


[[P0258]](https://wg21.link/p0258) `std::is_contiguous_layout` (pour le hashage)
--------------------------------------------------------------------------------
    
    TODO


Suppression
===========

[[N4190]](https://wg21.link/n4190) `auto_ptr`, old `<functional>` stuff, `random_shuffle`
--------------------------------------------------------------
    
    TODO


[[P0004]](https://wg21.link/p0004) ios aliases
-------------------
    
    TODO


[[P0181]](https://wg21.link/p0181) Suppression de `std::default_order` (indirection vers `std::less`)
-----------------------------------------------------------------------------------------------------

Cela cassait l'ABI de certains compilateurs à cause du *mangling*


[[P0302]](https://wg21.link/p0302) Allocateurs des `std::function`
-----------------------------------------------------------------
    
    TODO



Fonctionnalités *majeures* 
==========================
    
Quatre _gros_ morceaux ont été inclus dans **C++17** :
    
* le parallélisme avec les [69 algorithmes parallélisées](http://en.cppreference.com/w/cpp/experimental/parallelism) ;
* le [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem) ;
* les autres transfuges de boost (optional, any, string_view, variant...) ;
* les fonctions spéciales mathématiques.
    
Par contre, les fonctionnalités suivantes n’ont pas été considérées comme suffisamment mures pour être incluses :
    
* [Coroutines](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0057r4.pdf) ;
* Réseau [_(Networking)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) ;
* Tableaux [_(Array)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3820.html). Une idée de 2013, mais finalement abandonnée ;
* [_Ranges_](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf) ;
* Mémoire transactionnelle [_(Transactional Memory)_](http://en.cppreference.com/w/cpp/language/transactional_memory) ;
* et autres extensions majeures de la bibliothèque standard. 
    
Le comité attend de voir des implémentations satisfaisantes dans les compilateurs avant de les inclure...
     
Même si **C++17** va un peu plus transcender notre façon de coder en C++, de nombreux développeurs s’attendaient à une version majeure (révolutionnaire). Par rapport à **C++11**, les apports du **C++17** ressemblent plus à une version mineure.
    
![Évolution des fonctionnalités majeures](https://herbsutter.files.wordpress.com/2016/06/wg21-timeline.png)
