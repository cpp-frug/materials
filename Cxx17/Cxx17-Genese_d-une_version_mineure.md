
Pour contribuer à ce document, merci de lire le [`README.md`](https://github.com/cpp-frug/materials/blob/master/README.md) |
-----------------------------------------------------------------------------------------------------|


C++17 - Partie 1 sur 4 - Genèse d'une version mineure
=====================================================


Authors |Oliver H, olibre, Lucas, palm123, Benoît Sibaud, RyDroid et cracky
--------|------------------------------
License |[CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)



L'ajout de fonctionnalités au **C++17** a été clôturé. Faisons donc le tour des nouveautés et vérifions ce titre provocateur :-)


![Illustration C++ de Dominic Alves sous license CC-BY-SA 2.0](https://c2.staticflickr.com/2/1116/785982209_b0da7b4380_o.jpg)
    
Cette dépêche est la première d'une série de quatre dépêches sur le C++17.

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

Première dépêche - Genèse du C++17
----------------------------------

La spécification C++ n'est pas libre et [son téléchargement coûte 180 €](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=64029). Alors, les développeurs C++ utilisent un [brouillon _(draft)_ gratuit](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf). Par contre, le C++ est bien un [standard ouvert](https://fr.wikipedia.org/wiki/Format_ouvert) : pas de brevets logiciels ni de propriété intellectuelle. Mais de toutes façons, la plupart des développeurs C++, même expérimentés, n'ont jamais lu le standard. Car ce sont surtout [des livres](https://fr.wikipedia.org/wiki/The_C%2B%2B_Programming_Language) et plus récemment des [sites](http://fr.cppreference.com/) qui sont utilisés.

Seconde dépêche - Les changements au niveau du langage
------------------------------------------------------

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

Troisième dépêche - Les changements au niveau de la bibliothèque standard
-------------------------------------------------------------------------

Les transfuges de chez [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) :
               
`boost::*` | `std::*`
-----------|---------
[`filesystem`](http://www.boost.org/doc/libs/1_61_0/libs/filesystem) | -> [`filesystem`](http://en.cppreference.com/w/cpp/filesystem)
[`variant`](http://www.boost.org/doc/libs/1_61_0/libs/variant) | -> [`variant`](http://en.cppreference.com/w/cpp/utility/variant)
[`any`](http://www.boost.org/doc/libs/1_61_0/libs/any) | -> [`any`](http://en.cppreference.com/w/cpp/utility/any)
[`optional`](http://www.boost.org/doc/libs/1_61_0/libs/optional) | -> [`optional`](http://en.cppreference.com/w/cpp/utility/optional)
[`math`](http://www.boost.org/doc/libs/1_61_0/libs/math) | -> [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math)

Ce qui peut changer notre vie de développeur C++ :
    
* La [algorithmes paralélisés](http://en.cppreference.com/w/cpp/experimental/parallelism#Parallelized_versions_of_existing_algorithms) (si multitâche performant) ;
* [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view) (pour remplacer les `const std::string&`).

Et pas mal d'autres nouveautés :
    
- [`std::string::data()`](http://en.cppreference.com/w/cpp/string/basic_string/data) non-`const` ;
- ...

Par contre, impasse sur une fonctionnalité majeure très attendue, les [_ranges_](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf). Une autre fonctionnalité majeure absente, le [réseau _(Networking)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf). Mais, de toutes façons, cette dernière n'était pas prévue pour C++17.

Quatrième dépêche - Bilan des fonctionnalités C++17 et attentes pour C++20
--------------------------------------------------------------------------

Alors, version mineure ou majeure ?
    
* Les améliorations sont appréciables, mais aucune fonctionnalité majeure au niveau du langage  ;
* Et côté bibliothèque standard, la plupart des fonctionnalités majeures sont déjà disponibles dans [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) et supportent donc aussi d'anciennes versions des compilateurs.

Partager
--------

La version la plus à jour de cette dépêche peut se trouver sur [ce dépôt Git C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17/Cxx17-Features.md). Et pour aller encore plus loin, participons à l'amélioration de ce contenu CC-BY-SA en y ajoutant nos découvertes individuelles C++17 afin d'en faire profiter le plus grand nombre :-)

------------------------------------------


La spécification du standard n'est ni libre ni gratuite
=======================================================
    
Les mentions de droit d'auteur ne laissent aucun doute, **la spécification du standard C++ n'est pas libre** :
      
> © ISO/IEC 2014 – All rights reserved  
> COPYRIGHT PROTECTED DOCUMENT  
> All rights reserved. Unless otherwise specified, no part of this publication may be reproduced or utilized otherwise in any form or by any means, electronic or mechanical, including photocopying, or posting on the internet or an intranet, without prior written permission.
> Permission can be requested from either ISO at the address below or ISO’s member body in the country of the requester.
    
Par contre, on peut rêver à un organisme ISO local qui donne des permissions de reproduction...
    
Et en plus, obtenir le standard C++ coûte cher, même le téléchargement d'un PDF :
        
* 182 € sur le [site de l'ISO](http://www.iso.org/iso/fr/catalogue_detail?csnumber=64029) (198 francs suisses) ;
* 238 € sur le [site de l'ANSI](http://webstore.ansi.org/RecordDetail.aspx?sku=ISO%2fIEC+14882%3a2014) (265 $ USA). 


Les anciens standard sont officiellement supprimés
==================================================
    
Mais le plus incroyable est qu'à chaque nouvelle version du standard ISO/IEC 14882, la version précédente est supprimée (_withdraw_ en anglais) :
    
* C++98 [ISO/IEC 14882:1998](http://www.iso.org/iso/fr/catalogue_detail?csnumber=25845) supprimé ;
* C++03 [ISO/IEC 14882:2003](http://www.iso.org/iso/fr/catalogue_detail?csnumber=38110) supprimé ;
* C++11 [ISO/IEC 14882:2011](http://www.iso.org/iso/fr/catalogue_detail?csnumber=50372) supprimé.
    
C'est vraiment étrange, sachant que la plupart des projets C++ utilisés actuellement sont codées en C++98. Et la plupart des entreprises utilisent encore aujourd'hui quelques versions de compilateur de référence pour l'ensemble des projet qui ne supporte pas ou partiellement le standard C++11. Alors comment faire pour connaître le standard C++ utilisée par le bon vieux compilateur que l'on est obligé d'utiliser ?
    
Yaplus que les brouillons du comité
===================================
    
Les documents de travail du comité de standardisation sont légalement gratuits (toujours pas libre) :
    
* [open-std.org/jtc1/sc22/wg21](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/)
* [github.com/cplusplus/draft](https://github.com/cplusplus/draft/tree/master/papers)
       
Quand le comité de standardisation C++ valide un brouillon (nouvelle version C++), ce brouillon bénéficie [de dernières corrections](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3338.html) puis est fourni à l'ISO qui change la mise en forme pour en faire une version officielle.

Les versions C++
================
            
La table suivante liste les différentes versions officielles C++ ainsi que le brouillon **C++17** en cours de consolidation. Nous pouvons remarquer le saut considérable du nombre de pages entre **C++03** et **C++11**.
              
      Version                       | Pages
------------------------------------|-------
C++98 [ISO/IEC 14882:1998 1998-09-01](http://www.lirmm.fr/~ducour/Doc-objets/ISO+IEC+14882-1998.pdf) | 776 pages
C++03 [ISO/IEC 14882:2003 2003-10-15](https://github.com/hstefan/htlib/blob/master/res/INCITS%2BISO%2BIEC%2B14882-2003.pdf) | 786 pages (+1%)
C++11 [ISO/IEC 14882:2011 2011-09-01](http://new.vk.com/doc100509572_160085962?hash=6801602629449dfa59&dl=27c32949114b3322a2)| 1356 pages (+73%)
C++11 [Draft N3376 2012-02-28](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3376.pdf)| 1324 pages
C++14 [Draft N4296 2014-11-19](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf) | 1368 pages (+3%)
C++17 [Draft N4606 2016-07-12](https://github.com/cplusplus/draft/blob/master/papers/n4606.pdf)| 1586 pages (+16%)
        
Attention, ce dernier lien est celui du brouillon **C++17** le plus récent lors de la rédaction de cette dépêche. Cette version est certainement obsolète quelques mois après la publication de cette dépêche.
     
Ceux qui ont l'oeuil aiguisé remarqueront que le brouillon N3376 représentant la version C++11 a été publié (2012-02-28) après la norme officielle 14882:2011 (2011-09-01). Ce N3376 correspond en fait à des corrections éditoriales mineures apportées au brouillon [N3291](http://www.joshuaburkholder.com/documents/n3291.pdf) fourni à l'ISO. En anglais, c'est le *first post-publication draft*.
     
Il est fréquent que des corrections soient apportées aux standards C++ même quelques années après la date officielle de publications (**TODO** donner un exemple).

Le C++ reste néanmoins un standard ouvert
=========================================
               
Par contre, c'est bien un [standard ouvert](https://fr.wikipedia.org/wiki/Format_ouvert), sans brevet logiciel, sans propriété intellectuelle. C'est à dire que le langage et sa bibliothèque standard (API) peuvent être implémentés librement. Ce qui n'est pas le cas des langages comme Java ou C#.
    
Nous aurions aimé un standard plus ouvert comme pour Go ou Rust. Et c'est vers ce sens que le comité s'oriente, en cherchant plus de proximité avec les utilisateurs C++, plus de transparence.
   

Un langage extrêmement compliqué qui se simplifie
=================================================
        
Par rapport à tous les langages utilisés en production, avouons que le C++ est le langage le plus complexe que l'humanité ait pu inventer ! Les développeurs C++ en ont bien conscience. C'est peut-être la raison pour laquelle, par rapport aux autres _meetups_, les conférences sur le C++ ne dénigrent pas les autres langages. Au contraire, nous aimerions un langage plus simple, mais attention qui **"ne sacrifie pas les performances"**.
    
Le C++ est tellement vaste, les développeurs C++ n'en connaissent bien souvent qu'une petite portion (10%). Ceux qui connaissent vraiment le C++ sur le bout des doigts, sont appelés des juristes du C++ *(C++ lawyers)*.
     
Pour inverser la tendance, certains membres du comité de standardisation, comme [Bjarne Stroustrup](https://fr.wikipedia.org/wiki/Bjarne_Stroustrup) (le créateur du C++) souhaitent accélérer l'évolution du langage vers un C++ plus intuitif, plus sûr, et toujours plus performant.

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
