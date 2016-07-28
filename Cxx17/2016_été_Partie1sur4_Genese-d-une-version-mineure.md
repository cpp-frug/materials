
| Pour contribuer à ce document, merci de lire le [`README.md`](README.md)
|-------------------------------------------------------------------------


C++17 - Partie 1 sur 4 - Genèse d'une version mineure
=====================================================


Authors |Oliver H, olibre, Benoît Sibaud, Lucas, palm123, cracky, Martin Peres et RyDroid
--------|------------------------------
License |[CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)


Les fonctionnalités de la prochaine version du C++ sont arrêtées. Cette première dépêche, d'une série de quatre dépêches, s'attarde sur la face cachée du C++, et peut intéresser tous les lecteurs LinuxFr.org, pas seulement les développeurs C++ :-)

![Illustration C++ de Dominic Alves sous license CC-BY-SA 2.0](https://c2.staticflickr.com/2/1116/785982209_b0da7b4380_o.jpg)

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

Série de dépêches C++17
=======================
    
Ce chapitre résume cette série de quatre dépêches consacré aux ~~r~~ évolutions apportées par la mouture **C++17**.

1. Genèse du C++17
------------------

Cette première dépêche nous amène dans les coulisses du standard C++, la face cachée d'un document non-libre et [payant](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=64029), et d'un [brouillon](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf) _(draft)_ qui sert de référence. Par contre, le C++ est bien un [standard ouvert](https://fr.wikipedia.org/wiki/Format_ouvert) (pas de brevets logiciels ni de propriété intellectuelle). Mais de toutes façons, la plupart des développeurs C++, même expérimentés, n'ont jamais lu le standard. Ce sont surtout [des livres](https://fr.wikipedia.org/wiki/The_C%2B%2B_Programming_Language) et plus récemment des [sites](http://fr.cppreference.com/) qui sont utilisés.

2. Nouveautés du langage
------------------------

Cette seconde dépêche présente beaucoup de changements au niveau du langage. Voici un rapide aperçu :
    
- [Déduction des arguments `template` par le constructeur](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html) comme dans `std::array a{1,2,3}` ;
* [Déstructuration `auto [x, y] = f();`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r2.html) qui simplifie `char x; int y; std::tie(x,y)=f();` ;
- [`template<auto> class C`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r1.html) pour éviter `decltype(var)` dans `C<decltype(var),var>` ;
* [`namespace aa::bb{}`](http://en.cppreference.com/w/cpp/language/namespace) pour simplifier `namespace aa{ namespace bb{} }` ;
- [`if constrexpr`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0128r1.html) pour sélectionner du code à la compilation ;
- Lambda `constexpr` et capture `*this` ;
- [`if(init;condition)` et `switch(init;condition)`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r0.html) comme pour `for(init;cond;inc)` ;
- [Variables `inline`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r0.pdf) (après les [variables `template`](http://en.cppreference.com/w/cpp/language/variable_template) du C++14) ;
- ...

Par contre, des fonctionnalités majeures très attendues comme les [Concepts](http://fr.cppreference.com/w/cpp/concept), les [Modules](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf), la [Syntaxe d'appel uniforme](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax#C.2B.2B_proposal) ou la [Réflexion](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0194r1.html) ne seront pas embarqué dans la publication **C++17**.

3. Nouveautés de la bibliothèque standard
-----------------------------------------

Cette troisième dépêche nous présente les changements au niveau de la bibliothèque standard. 
    
Comme par exemple les [algorithmes parallélisés](http://en.cppreference.com/w/cpp/experimental/parallelism#Parallelized_versions_of_existing_algorithms) et [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view) (remplace les `const std::string&`) qui pourraient bousculer notre petite vie de développeur.

Mais aussi les composants [`filesystem`](http://en.cppreference.com/w/cpp/filesystem), [`variant`](http://en.cppreference.com/w/cpp/utility/variant), [`any`](http://en.cppreference.com/w/cpp/utility/any), [`optional`](http://en.cppreference.com/w/cpp/utility/optional) et les [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math) ayant  fait leurs preuves au sein de [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques).

4. Bilan C++17 et attentes pour C++20
-------------------------------------

Cette quatrième dépêche mesure le degré de changement : Version mineure ou majeure ?
    
D'un côté, les améliorations sont nombreuses et appréciables. Mais de l'autre mais aucune fonctionnalité majeure au niveau du langage, et la plupart des fonctionnalités majeures de la bibliothèque standard sont déjà disponibles dans [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) (donc déjà supportées par un large panel d'anciens compilateurs).


Mais où sont les [Intervalles *(Ranges)*](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf) au le [Réseau _(Networking)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) ?
    
Conséquences sur le processus de standardisation ? 
Qu'attendre de C++20 ?
Comment contribuer ?

Partage
=======
    
Cette dépêche ainsi que les trois suivantes sont figées après publication. Allons encore plus loin, participons à l'amélioration de ce contenu CC-BY-SA sur le repo [Git C++FRUG](https://github.com/cpp-frug/materials/blob/master/Cxx17) en y ajoutant nos découvertes individuelles C++17 afin d'en faire profiter le plus grand nombre :-)
    
1. [Genèse d'une version mineure](https://github.com/cpp-frug/materials/blob/master/Cxx17/2016_%C3%A9t%C3%A9_Partie1sur4_Genese-d-une-version-mineure.md) ;
2. [Nouveautés du langage](https://github.com/cpp-frug/materials/blob/master/Cxx17/2016_%C3%A9t%C3%A9_Partie2sur4_Nouveaut%C3%A9s-du-langage.md) ;
3. [Nouveautés de la bibliothèque standard](https://github.com/cpp-frug/materials/blob/master/Cxx17/2016_%C3%A9t%C3%A9_Partie3sur4_Nouveaut%C3%A9s-de-la-biblioth%C3%A8que-standard.md) ;
4. [Bilan et attentes pour C++20](https://github.com/cpp-frug/materials/blob/master/Cxx17/2016_%C3%A9t%C3%A9_Partie4sur4_Bilan-et-attentes-pour-C%2B%2B20.md).
    
Avec toutes nos contributions individuelles réunis, nous profiterons d'avantage de nos recherces et nous offrions un contenu libre (CC-BY-SA) et de qualité pour créer, par exemple, un article Wikipédia C++17 en français.
    
![Logo C++FRUG représenté par un gros "C++" au centre du cercle de la Francophonie](https://upload.wikimedia.org/wikipedia/commons/9/91/Cpp-Francophonie.svg)

-------------------------------------------------------
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

Les anciens standards supprimés
===============================
    
Mais le plus incroyable est que chaque nouvelle publication du standard supprime _(withdraw)_ la version précédente sur tous les sites officiels :
    
* C++98 [ISO/IEC 14882:1998](http://www.iso.org/iso/fr/catalogue_detail?csnumber=25845) supprimé ;
* C++03 [ISO/IEC 14882:2003](http://www.iso.org/iso/fr/catalogue_detail?csnumber=38110) supprimé ;
* C++11 [ISO/IEC 14882:2011](http://www.iso.org/iso/fr/catalogue_detail?csnumber=50372) supprimé.
    
C'est vraiment étrange, sachant que la plupart des projets C++ utilisés actuellement sont codés en C++98. Et la plupart des entreprises utilisent encore aujourd'hui des versions de compilateurs qui ne supportent pas ou partiellement le standard C++11.
    
Alors comment faire pour connaître le standard C++ utilisé par le bon vieux compilateur que l'on est obligé d'utiliser ? (à part les [consulter à l'INRIA](http://opac.inria.fr/search*frf/a?searchtype=Y&searcharg=14882))


Et les brouillons du comité ?
=============================
        
Les documents en cours de rédaction _(draft)_ du comité de standardisation sont gratuitement accessibles (mais toujours pas libres) :
    
* [open-std.org/jtc1/sc22/wg21](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/)
* [github.com/cplusplus/draft](https://github.com/cplusplus/draft/tree/master/papers)
       
Quand le comité de standardisation C++ valide un brouillon (nouvelle version C++), ce brouillon bénéficie [de dernières corrections](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3338.html) puis est fourni à l'ISO qui change la mise en forme pour en faire une version officielle.

Un standard ouvert tout de même !
=================================
    
Néanmoins, le C++ est bien un [standard ouvert](https://fr.wikipedia.org/wiki/Format_ouvert), sans brevet logiciel, sans propriété intellectuelle. C'est à dire que le langage et sa bibliothèque standard (API) peuvent être implémentés librement. Ce qui n'est pas le cas des langages comme Java ou C# (troll).
    
De même, le nom **"C++"** n'est pas une marque, ni aucun type de propriété intellectuelle. À la différence de la marque [**JavaScript®**](https://developer.mozilla.org/fr/docs/Web/JavaScript/A_propos#Ressources_JavaScript) déposée par Oracle, ou des marques non déposées [**Rust™**](https://www.mozilla.org/en-US/foundation/trademarks/list/), [**Go™**](https://www.google.fr/intl/fr/permissions/trademark/trademark-list.html) (et une [autre **Go™**](https://www.thoughtworks.com/news/innova-using-thoughtworks-studios-go)).
    
Et même si C++ n'est pas encore aussi ouvert que peut l'être Rust™, de nombreux membres du comité améliorent constamment la façon de travailler pour plus de transparence, plus de proximité avec les utilisateurs C++, comme pour le [compte GitHub du comité](https://github.com/cplusplus). Cependant, l'organisme ISO et les institutions locales (AFNIC, AFNOR...) sont conservatrices.

Les versions C++
================
    
Même si le langage [naît à la fin des années 1970](http://en.cppreference.com/w/cpp/language/history), il n'est standardisé que 20 ans plus tard afin d'arrêter la profusion de [versions C++ incompatibles](http://open-std.org/JTC1/SC22/WG21/docs/papers/1989/X3_89-738R%20Programming%20Language%20C++%20Proposal.pdf).
    
La table suivante liste les différentes versions C++ standardisées ainsi que le brouillon **C++17** en cours de consolidation. Nous pouvons remarquer le saut considérable du nombre de pages entre **C++03** et **C++11**.
              
      Version                       | Pages
------------------------------------|-------
C++98 [ISO/IEC 14882:1998 1998-09-01](http://www.lirmm.fr/~ducour/Doc-objets/ISO+IEC+14882-1998.pdf) | 776 pages
C++03 [ISO/IEC 14882:2003 2003-10-15](https://github.com/hstefan/htlib/blob/master/res/INCITS%2BISO%2BIEC%2B14882-2003.pdf) | 786 pages (+1%)
C++11 [ISO/IEC 14882:2011 2011-09-01](http://new.vk.com/doc100509572_160085962?hash=6801602629449dfa59&dl=27c32949114b3322a2)| 1356 pages (+73%)
C++11 [Draft N3376 2012-02-28](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3376.pdf)| 1324 pages
C++14 [Draft N4296 2014-11-19](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf) | 1368 pages (+3%)
C++17 [Draft N4606 2016-07-12](https://github.com/cplusplus/draft/blob/master/papers/n4606.pdf)| 1586 pages (+16%)
        
Attention, ce dernier lien est celui du brouillon **C++17** le plus récent lors de la rédaction de cette dépêche. Cette version est certainement obsolète quelques mois après la publication de cette dépêche.
     
Ceux qui ont l'œil aiguisé remarqueront que le brouillon N3376 représentant la version C++11 a été publié (2012-02-28) après la norme officielle 14882:2011 (2011-09-01). Ce N3376 correspond en fait à des corrections éditoriales mineures apportées au brouillon [N3291](http://www.joshuaburkholder.com/documents/n3291.pdf) fourni à l'ISO. En anglais, c'est le *first post-publication draft*.

Rapport d'Anomalie
==================
    
Même après moult relectures par les meilleurs experts C++ au monde, avec toutes les précautions prises par les institutions officielles, les publications des standards C++ contenaient 5000 anomalies ayant fait l'objet d'un [rapport d'anomalie _(Defect Report)_](https://isocpp.org/std/submit-issue) !
     
* 2200 rapports d'anomalie au niveau du [langage](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_toc.html) ;
* 2750 rapports d'anomalie au niveau de la [bibliothèque standard](http://www.open-std.org/jtc1/sc22/wg21/docs/lwg-toc.html).
    
Lors des ses réunions, le comité discute des rapports d'anomalie et devrait publier régulièrement des rectificatifs techniques _(Technical Corrigendum)_. Mais le comité n'a jamais publié aucun rectificatif technique à ce jour !
    
Par exemple, le comité avait approuvé un [rectificatif technique en 2003](http://www.open-std.org/jtc1/sc22/wg21/docs/standards). Et finalement, le comité publie comme étant une nouvelle version du standard => **C++03** :
    
> A technical corrigendum was approved in 2003, . and the standard was published again as the ISO/IEC 14882:2003 edition, published 2003-10-16.
    
Bon, c'est vrai, à la décharge du comité, ce rectificatif technique de 2003 contenait une nouvelle fonctionnalité : [*Value  initialization*](http://en.cppreference.com/w/cpp/language/value_initialization#Notes). C'était la dernière fois, que le comité avait travaillé sur un rectificatif technique.

Néanmoins, même si le comité ne publie aucun rectificatif technique, les rapports d'anomalie qu'il approuve sont [pris en compte par les compilateurs](http://clang.llvm.org/cxx_dr_status.html). Et des sites comme cppreference.com indiquent scrupuleusement les changements induits : 
    
* Quatre rapports d'anomalie pour l'[opérateur ternaire `cond ? a : b`](http://en.cppreference.com/w/cpp/language/operator_other#Defect_reports) ;
* Trois rapports d'anomalie pour les [variables membres](http://en.cppreference.com/w/cpp/language/data_members#Defect_reports) ;
* Trois rapports d'anomalie pour [`return`](http://en.cppreference.com/w/cpp/language/return#Defect_reports) ;
* Deux rapports d'anomalie pour [`throw`](http://en.cppreference.com/w/cpp/language/throw#Defect_reports) ;
* ...

Un langage extrêmement compliqué qui se simplifie
=================================================
        
Par rapport à tous les langages utilisés en production, avouons que le C++ est peut être le langage le plus complexe que l'humanité ait pu inventer ! Les développeurs C++ en ont bien conscience. C'est peut-être la raison pour laquelle les participants aux _meetups_ se montrent souvent bienveillants à l'égard des autres langages. Les développeurs C++ aimeraient un langage plus simple, à condition qu'il **"ne sacrifie pas les performances"**.
    
Le C++ est tellement vaste que les développeurs C++ n'en connaissent bien souvent qu'une petite portion (10%). Ceux qui connaissent vraiment le C++ sur le bout des doigts sont appelés des juristes du C++ *(C++ lawyers)*.
     
Pour inverser la tendance, certains membres du comité de standardisation, comme [Bjarne Stroustrup](https://fr.wikipedia.org/wiki/Bjarne_Stroustrup) (le créateur du C++) souhaitent accélérer l'évolution du langage vers un C++ plus intuitif, plus sûr, et toujours plus performant.

C'est dans ce cadre que l'initiative [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines) a été lancée. A la fois pour proposer un sous-ensemble du C++ plus sûr, plus simple et sans sacrifier les performances. Mais aussi pour faire pression sur les membres du comité pour adopter les idées de la [Guidelines Support Library](https://github.com/Microsoft/GSL) (voir aussi l'[implémentation de Martin Moene](https://github.com/martinmoene/gsl-lite) compatible avec beaucoup plus de compilateurs).

Cycle de publication [triannuel](http://www.universalis.fr/dictionnaire/triannuel/)
================================

Après la version majeure **C++98** (et son correctif **C++03**), un nouveau standard C++ devait être publié dans les années suivantes. Comme sa date de publication n'était pas fixée, cette version a été nommée temporairement **C++0x**.
    
Mais, avec le manque de maturité de certaines fonctionnalités et les requêtes continuelles d'ajout de nouvelles fonctionnalités, le comité de standardisation n'arrivait pas à stabiliser le standard. Et finalement **C++0x** a été publié en 2011 ! Ne perdons pas la face, `0x = 11` est correct mathématiquement avec `x = A` en [hexadécimal](https://fr.wikipedia.org/wiki/Syst%C3%A8me_hexad%C3%A9cimal) :-)

Afin d'éviter tout nouveau glissement, le comité a alors décidé de publier un nouveau standard C++ tous les 3 ans, en figeant les fonctionnalités l'année N-1. Avec un cycle d'une version majeure (**C++11**) suivie d'une version mineure (**C++14**).


Malgré des dates de publication figées, les appellations **C++1y** (pour **C++14**) et **C++1z** (pour **C++17**) perdurent. Par exemple, l'[option de compilation `-std=c++1z`](https://gcc.gnu.org/projects/cxx-status.html) ou le [tag c++1z sur stackoverflow](http://stackoverflow.com/tags/c%2b%2b1z/info).

Les membres du comité de standardisation utilisent le terme **C++17** (et non pas C++1z). Soyons confiants, **C++1z** verra bien le jour en 2017 (et non pas en 2018, ni après).


Deux sommets pour délimiter le périmètre C++17
==============================================


Donc en 2016 (année N-1), afin de figer le périmètre fonctionnel du **C++17**, les membres  du comité de standardisation C++ (une centaine de personnes) se sont réunis deux fois :
    
1. [Une semaine début mars](https://isocpp.org/blog/2016/03/trip-report-jax-sutter), à Jacksonville (Floride), pour adopter beaucoup de fonctionnalités, mais aussi pour rejeter plusieurs fonctionnalités majeures très attendues ;
2. [Une semaine fin juin](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/), à Oulu (Finlande), pour intégrer pas mal d'autres fonctionnalités et ainsi clore l'ajout des fonctionnalités.
    
La semaine se déroule sur six jours, du lundi au samedi. Pas de grasse matinée car les premières réunions débutent à 8:30. Ces réunions permettent de débattre et voter l'intégration de chacune des spécifications techniques (*Technical Specification)*. Plusieurs réunions se déroulent en parallèle, et les membres rejoignent les réunions selon leur centre d'intérêt. Après ces réunions *officielles*, les membres se retrouvent pour continuer à échanger ou pour améliorer les spécifications techniques.  
    
Mais à Oulu, un phénomène naturel a eu un impact direct sur la productivité : le [soleil se couche après minuit en juin](http://dateandtime.info/fr/citysunrisesunset.php?id=643492&month=6&year=2016) ! Si bien, que la plupart des membres ne se rendaient pas compte de l'heure et ont veillé bien plus tard que d'habitude. En plus du soleil qui *dort* deux heures par nuit, le décalage horaire pour les non-européens a littéralement épuisé les membres qui ont eu besoin de plusieurs jours de repos pour s'en remettre !

Plus de 10 ans pour intégrer les fonctionnalités
================================================
    
**C++11** ayant du faire l'impasse sur plusieurs fonctionnalités _majeures_, celles-ci étaient prévues d'être intégrées dans le standard avec la prochaine version _majeure_, **C++17**. Et effectivement, certaines fonctionnalités sont dans le tuyau depuis plus de dix ans : 
    
* [Fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math) depuis [2003](http://open-std.org/JTC1/SC22/WG21/docs/papers/2003/n1422.html) ;
* [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem) depuis [2004](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1576.html).

Par contre, d'autres fonctionnalités _majeures_ sont toujours dans le tuyau :
  

* [Concepts](http://en.cppreference.com/w/cpp/language/constraints) depuis [2003](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2003/n1510.pdf) ;  
* [Réflexion](https://fr.wikipedia.org/wiki/R%C3%A9flexion_(informatique)) statique (à la compilation) depuis [2005](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1775.pdf) ;
* [Intervalles *(Ranges)*](http://www.boost.org/libs/range/index.html) depuis [2005](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1871.html) ;
* [Modules](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4592.pdf) (pour remplacer `#include`) depuis [2005](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1736.pdf) ;
* [Réseau](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) depuis [2005](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1838.pdf) (qui a pris le nom définitif [*Networking* fin 2005](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1925.pdf)) ;
* [Mémoire transactionnelle](http://en.cppreference.com/w/cpp/language/transactional_memory) dont son objectif de [2012 était d'intégrer C++17](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3422.pdf) ;
* ...
    
Comme quoi, le comité de standardisation prend son temps pour bien s'assurer que chaque fonctionnalité soit *parfaite* et cela peut prendre une dizaine d'années ! L'objectif étant de ne pas dégrader d'avantage la complexité inhérente au C++, avec comme contre partie d'avoir un langage de programmation qui évolue doucement...

La suite...
===========    
    
La prochaine dépêche rentre enfin dans le vif du sujet.
    
Merci de nous donner un coup de main à la rédaction de trois dépêches **C++17** à venir en expliquant les nouvelles fonctionnalités ou en améliorant l'ébauche en cours de rédaction :-)

Pour participer ou lire en avance les prochaines dépêches :
    
* Se rendre sur l'espace de [rédaction LinuxFr.org](https://linuxfr.org/redaction) (recommandé pour la rédaction) ;
* Directement sur le [repo Git *materials*](https://github.com/cpp-frug/materials/tree/master/Cxx17) du C++FRUG (Groupe des utilisateurs C++ francophones).

