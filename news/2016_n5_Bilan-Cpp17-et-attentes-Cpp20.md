Déception et nouveau processus de standardisation pour C++20
============================================================

Face à la déception de cette version _pas très majeure_,
le comité réfléchit à faciliter la contribution de la communauté C++
et à améliorer le processus de standardisation.

C'est la fin de l'alternance de versions majeurs/mineures : 
Toutes fonctionnalités prêtes l'année N-1 seront intégrées dans le standard pour l'année N,
qu'elles soient majeurs ou mineures.

Et toi, cher lecteur/chère lectrice de LinuxFr.org, es-tu un peu déçu(e) du périmètre fonctionnel C++17 ?
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
# if __cplusplus <= 199711  //Bug GCC < 4.7
#  warning Compilé pour C++99
# elif __cplusplus == 201103
#  warning Compilé pour C++11 //-std=c++0x
# elif __cplusplus == 201402 //par défaut GCC6
#  warning Compilé pour C++14 //-std=c++1y
# elif __cplusplus > 201700
#  warning Compilé pour C++17 //-std=c++1z
# else
#  error Valeur inattendue de __cplusplus  
# endif
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
