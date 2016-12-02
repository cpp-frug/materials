C++17 indique la disponibilité des entêtes *(headers)*
======================================================

Auteurs | [Oliver H](https://linuxfr.org/users/oliver_h), [Adrien Jeser](https://linuxfr.org/users/jeser), [Guillaume Dua](https://github.com/GuillaumeDua), [olibre](https://github.com/olibre), [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky) et [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid)
--------|------------------------------
License | [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)
URL     | https://linuxfr.org/news/cpp17-indique-si-un-entete-est-disponible
Date    | 2016-12-01
Tags    | c++17, c++ et cpp
Score   |   0

Chaque jour de décembre a droit à sa surprise. Après l'[ordre d'évaluation][1], aujourd'hui, le [calendrier de l’Avent][avent] du C++ présente la [Spécification Technique][TS] [P0061](http://wg21.link/p0061) concernant une macro magique : `#define __has_include`.
    
[avent]: https://fr.wikipedia.org/wiki/Calendrier_de_l'Avent
[1]:  https://linuxfr.org/news/cpp17-fixe-l-ordre-d-evaluation-des-expressions
[TS]: https://linuxfr.org/news/les-coulisses-du-standard-cpp#technical-specification-ts


[![Une personne déprime de ne plus rien comprendre au C++ et son collègues le rassure que LinuxFr.org publie le calendrier de l'Avent du C++ avec des explications pédagogiques](http://cpp-frug.github.io/materials/images/calendrier-avent-cpp.png)](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#calendrier-de-l-avent-du-c)
 

----

* [Dépêche préliminaire dans « Les coulisses du standard C++ » (CC BY-SA 4.0)](https://linuxfr.org/news/les-coulisses-du-standard-cpp)
* [Dépêche de mise bouche racontant la genèse du C++17 (CC BY-SA 4.0)](https://linuxfr.org/news/c-17-genese-d-une-version-mineure)
* [Dépêche du 1er décembre "C++17 fixe l'ordre d'évaluation" (CC BY-SA 4.0)](https://linuxfr.org/news/cpp17-fixe-l-ordre-d-evaluation-des-expressions)
* [Contenu markdown de cette dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-12-02_Cpp17-indique-si-un-entete-est-disponible.md)
* [Spécification Technique P0061 "`__has_include` for C++17"](http://wg21.link/p0061)

----

Série de dépêches C++
=====================
    
Cette dépêche fait partie de toute une série disponible également sur [le dépôt Git][dG] du [*Groupe des Utilisateurs C++ Francophone*][CppFRUG]. 
    
[dG]: https://github.com/cpp-frug/materials
[CppFRUG]: http://linuxfr.org/news/douzieme-rencontre-parisienne-c-mercredi-27-avril-2016#historique-des-rencontres-c-francophones
[md]: https://github.com/cpp-frug/materials/blob/gh-pages/news/README.md#pour-contribuer
    
Publication        | Dépêche                        
-------------------|-------------------------------------------------
[20 août 2016][La] |[Les coulisses du standard C++][Ga]
[ 2 oct. 2016][Lo] |[Genèse du C++17][Go]
[1ᵉʳ déc. 2016][L1]|[C++17 fixe l’ordre d’évaluation des expressions][G1]
2 déc. 2016        |[C++17 indique la disponibilité des entêtes *(header)*][G2]
à venir…           |… d’autres dépêches … 
[en 2017][LE]      |[Faut-il continuer à apprendre le C++ ?][GE]
    
Initialement, nous allions publier [une grosse dépêche super trop longue](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md). Puis, fin novembre, nous nous sommes ravisés et nous vous proposons plutôt une petite dépêche par jour, d’où l’idée du calendrier de l’Avent du C++. &emsp; **(ღˇ◡ˇ)~♥**
    
[La]: https://linuxfr.org/news/les-coulisses-du-standard-cpp
[Lo]: https://linuxfr.org/news/cpp17-ameliore-les-lambdas-et-attribut-s
[L1]: https://linuxfr.org/news/cpp17-fixe-l-ordre-d-evaluation-des-expressions
[LE]: https://linuxfr.org/news/faut-il-continuer-a-apprendre-le-cpp
    
[Ga]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md
[Go]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md
[G1]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-12-01_Cpp17-ordre-evaluation.md
[G2]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-12-02_Cpp17-indique-si-un-entete-est-disponible.md
[GE]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2017_n14_Faut-il-apprendre-le-Cpp.md

Spécification Technique
=========================

La macro [`__has_include`](http://en.cppreference.com/w/cpp/preprocessor/include) est dans les cartons depuis plusieurs années.
Le comité de normalisation du C++ a intégrée cette fonctionnalité en amendant le [*TS*](https://linuxfr.org/news/les-coulisses-du-standard-cpp#technical-specification-ts) [P0061](http://wg21.link/p0061).

La macro
========
    
La macro [**`__has_include()`**](http://en.cppreference.com/w/cpp/preprocessor/include) vérifie si l’en-tête est disponible pour inclusion.

```cpp
#if    __has_include(<filesystem>)
#  include           <filesystem>
#elif  __has_include(<experimental/filesystem>)
#  include           <experimental/filesystem>
#elif __has_include(<boost/filesystem.hpp>)
#  include          <boost/filesystem.hpp>
#else
#  error Ne trouve aucune en-tête filesystem
#endif
```

Dépendance optionelle
=====================

Sans cette fonctionnalité, le code source avait moins de possibilité de s'adapter automatiquement à l'environnement de compilation. Pour les dépendances optionnelles, l'outil de compilation (autotools, CMake...) devaient détecter la présence de telle ou telle dépendance et passer au compilateur des macro pour activer/désactiver des parties du code source.

Et sans cette complexité en amont, il est difficil de proposer du code C ou C++ qui gère des dépendances optionelles : si l'entête *(header)* d'une dépendance est absent, le compilateur arrête la compilation car le code source tente d'inclure l'entête introuvable de cette dépendance, même si la dépendance est optionnelle.

Chère lectrice, cher lecteur *LinuxFr.org*, tu as peut être une exemple pertienent en tête.
Tu souhaites déplacer la complexité de l'outil de compilation vers le code source ?
Fait nous part de tes idées dans les commentaires.

L'exemple ci-dessous illustre l'utilisation de la macro `__has_include()` mais aurait aussi pu se baser sur la détection de macros comme `WIN32`, `_WIN64` ou `MSCVER`...

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

L'exemple suivant utilise également la macro `__has_include()`.
C'est une possibilité pour une implémentation multi-plateforme du future [*Networking TS*](https://github.com/SG4).

```cpp
#if __has_include(<winsock2.h>)

#include <winsock2.h>

struct WindowsSocketImpl : AbstractSocket
{
  // implémentation Windows
};

using MySocket = WindowsSocketImpl;

#else

#include <sys/socket.h>

struct UnixSocketImpl : AbstractSocket
{
  // implémentation Unix
};

using MySocket = UnixSocketImpl;

#endif

// Usage
AbstractSocket * socket = new MySocket();
```

Roue de secour
==============

Nous pouvons aussi imaginer l'utilisation de cette macro `__has_include()` pour selectionner la bibliothèque à utiliser selon la disponibilité de différentes alternatives.

```cpp
#if __has_include(<optional>)

#include <optional>
using MyOptional = std::optional;

#elif __has_include(<experimental/optional>)

#warning Utilise std::experimental::optional à la place de std::optional
#include <experimental/optional>  // roue de secour
using MyOptional = std::experimental::optional;

#elif __has_include(<boost/optional.hpp>)

#warning Utilise boost::optional à la place de std::optional
#include <boost/optional.hpp>     // roue de secour secondaire
using MyOptional = boost::optional;

#else
#  error Ne trouve ni <optional>, ni <experimental/optional>, ni <boost/optional>
#endif
```

Faut-il continuer à apprendre le C++ ?
======================================
     
[![Panneau Please Do Not Feed the Trolls](https://upload.wikimedia.org/wikipedia/commons/1/19/Trolls.jpg)](https://commons.wikimedia.org/wiki/File:Trolls.jpg) | [![Panneau Troll barré](https://upload.wikimedia.org/wikipedia/commons/e/ea/DoNotFeedTroll.svg)](https://commons.wikimedia.org/wiki/File:DoNotFeedTroll.svg)
----|----
    
Merci de nous aider à structurer et consolider les différentes idées sur cette question sur l'espace de rédaction collaboratif de *LinuxFr.org* : [*« Faut-il continuer à apprendre le C++ ? »*](https://linuxfr.org/news/faut-il-continuer-a-apprendre-le-c)

Réutilisation
=============
    
Le texte de cette dépêche est protégé par ~~le [droit d’auteur](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diﬀusion)~~ la [gauche d’auteur](https://fr.wikipedia.org/wiki/Gauche_d'auteur) et réutilisable sous licence [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr). Les images utilisées sont aussi sous licence libre (cliquer sur l'image pour plus de détails).
    
Donc n'hésitez pas à réutiliser ce contenu libre pour créer, par exemple, des supports de formation, des présentations _(Meetups)_, des publications sur d’autres blogs, des articles pour des magazines, et aussi un article C++17 sur Wikipédia dès que [Wikipédia passera de la licence CC-BY-SA-3.0 à la CC-BY-SA-4.0](https://meta.wikimedia.org/wiki/Terms_of_use/Creative_Commons_4.0) (le contenu de cette dépêche utilise la version la CC-BY-SA-4.0).
    

Les auteurs
===========
    
Par respect de la licence, merci de [créditer](https://fr.wiktionary.org/wiki/cr%C3%A9diter#Verbe) les auteurs :
    
* Les principaux auteurs sont [Adrien Jeser](https://linuxfr.org/users/jeser) et [Oliver H](https://linuxfr.org/users/oliver_h) ;
* Les nombreux autres contributeurs ayant contribué sur l'ancêtre de cette dépêche ou sur le [dépôt Git](https://github.com/cpp-frug/materials) sont [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [olibre](https://github.com/olibre) et [Guss](https://github.com/GuillaumeDua).
    

Continuer à améliorer ce document
=================================
    
Malgré tout le soin apporté, il reste certainement des oublis, des ambiguïtés, des fôtes... Bien que cette dépêche restera figée sur le site *LinuxFr.org*, il est possible de continuer à l'enrichir sur le [dépôt Git](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md) du [**Groupe des Utilisateurs C++ Francophone**](http://linuxfr.org/news/douzieme-rencontre-parisienne-c-mercredi-27-avril-2016#historique-des-rencontres-c-francophones) (C++FRUG). C’est donc sur ce dépôt que se trouve les versions les plus à jour. &emsp; **(ღ˘⌣˘ღ)**

Alors que cet article restera figé sur le site *LinuxFr.org*, il continuera d’évoluer sur le dépôt Git. Merci de nous aider [à maintenir ce document à jour][md] avec vos questions/suggestions/corrections. L’idée est de partager ce contenu libre et de créer/enrichir des articles Wikipédia quand la licence [sera CC BY-SA 4.0](https://meta.wikimedia.org/wiki/Terms_of_use/Creative_Commons_4.0/fr). &emsp; **٩(•‿•)۶**

La suite
========
    
La dépêche suivante nous dévoilera une autre nouveauté du C++17.
    
Chère lectrice, cher lecteur _LinuxFr.org_. Tu souhaites apporter ta pierre à cet édifice ? Rejoins‐nous dans l’[espace de rédaction collaborative sur _LinuxFr.org_](https://linuxfr.org/redaction) (un [compte](https://linuxfr.org/compte/inscription) est nécessaire pour y accéder).
    
À suivre...
