| Pour contribuer à ce document, merci de lire le [`README.md`](README.md)
|-------------------------------------------------------------------------


Les coulisses du standard C++
=============================


Authors |Oliver H, olibre, duckie, Klaim, Benoît Sibaud, cracky, Lucas, palm123, Adrien Dorsaz, Martin Peres et RyDroid
--------|------------------------------
License |[CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)



La prochaine version C++ est en cours de rédaction afin de sortir une nouvelle version pour 2017. Profitons en pour rédiger une série de nouvelles sur le C++ afin de bien préparer la rentrée. Cette première dépêche nous amène dans les coulisses du C++, et donc peut intéresser tous les lecteurs LinuxFr.org. Les développeurs C++ sont invités à donner un coup de main à la rédaction/illustration des prochaines dépêches C++.

----

[Contenu Markdown de cette dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md)
[Contenu Markdown de la deuxième dépêche : C++17 - Genèse d'une version mineure](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md)
[Contenu Markdown de la troisième dépêche : C++17 - Nouveautés au niveau du langage](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md)
[Contenu Markdown de la quatrième dépêche : C++17 - Nouveautés au niveau de la bibliothèque standard](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n4_Cpp17_Nouveautes-de-la-bibliotheque.md)
[Contenu Markdown de la cinquième dépêche : Bilan C++17 et attentes C++20](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n5_Bilan-Cpp17-et-attentes-Cpp20.m)
[Article Wikipédia C++](https://fr.wikipedia.org/wiki/C%2B%2B)
[Site officiel du comité de standardisation du C++ - Page expliquant le fonctionnement du comité](https://isocpp.org/std/)
[Dépôt Git officiel du standard C++ en cours de rédaction](https://github.com/cplusplus/draft/)
[CppReference, wiki libre (CC-BY-SA-3.0 et GFDL) pour la documentation C et C++](http://fr.cppreference.com/w/Accueil)
[Dépêche 2012 par nazcafan : Codeurs, Traducteurs, CppReference a besoin de vous](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous)

----

Vous pouvez éditer cette partie en cliquant sur le crayon !

Dépêches estivales
==================


Chère lectrice, cher lecteur LinuxFr.org. Tes collègues sont partis en vacances, et tu cherches à t'occuper ? Ou alors, tu es en vacances et l'actualité informatique te manque déjà ? Et bien, voici une première dépêche C++ estivale d'une longue série. Les autres dépêches se consacreront aux évolutions apportées par la mouture **C++17**. Ainsi tu seras en avance technologique dès la rentrée.


Mais d'abord, commençons par un petit résumé de chacune de ces dépêches :


1. Les coulisses du C++
    
    Cette [première dépêche](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n1_Les-coulisses-du-standard.md) *dévoile la face cachée* du standard C++ : un standard non-libre et [payant](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=64029), un [brouillon](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf) _(draft)_ qui sert de référence, un standard C++ [ouvert](https://fr.wikipedia.org/wiki/Format_ouvert) (pas de brevet), des développeurs C++ (même expérimentés) n'ayant jamais lu le standard, des [livres](https://fr.wikipedia.org/wiki/The_C%2B%2B_Programming_Language) et [sites web](http://fr.cppreference.com/) utilisés comme référence, des fonctionnalités en discussion depuis plus de 12 ans...
    
2. Genèse du C++17
    
    La [deuxième dépêche](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n2_Cpp17_Genese-d-une-version-mineure.md) reviendra sur les dernières réunions du comité de standardisation.
    
3. Nouveautés du langage
    
    La [troisième dépêche](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n3_Cpp17_Nouveautes-du-langage.md) présentera les changements du langage : [déduction des arguments `template`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html) `std::array a{1,2,3};`, [décomposition `auto [x, y] = f();`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r2.html) équivalent à `char x; int y; std::tie(x,y)=f();`, [`namespace aa::bb`](http://en.cppreference.com/w/cpp/language/namespace) équivalent à `namespace aa{ namespace bb`, [`if constrexpr`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0128r1.html) (sélectionne du code à la compilation), Lambda `constexpr`, capture `*this`, [`if(init;condition)`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r0.html) comme `for(init;cond;inc)`, [variables `inline`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r0.pdf)...
    
    Snif, les fonctionnalités majeures très attendues comme les [Concepts](http://fr.cppreference.com/w/cpp/concept), les [Modules](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf), la [Syntaxe d'appel uniforme](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax#C.2B.2B_proposal) ou la [Réflexion](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0194r1.html) restent dans le tuyaux.
    
4. Nouveautés de la bibliothèque standard
    
    La [quatrième dépêche](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n4_Cpp17_Nouveautes-de-la-bibliotheque.md) présentera les changements au niveau de la bibliothèque standard. Avec les [algorithmes parallélisés](http://en.cppreference.com/w/cpp/experimental/parallelism#Parallelized_versions_of_existing_algorithms) et le [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view) qui pourraient bousculer notre petite vie de développeur. Mais aussi les composants [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem), [`std::variant`](http://en.cppreference.com/w/cpp/utility/variant), [`std::any`](http://en.cppreference.com/w/cpp/utility/any), [`std::optional`](http://en.cppreference.com/w/cpp/utility/optional) ayant fait leurs preuves au sein de [Boost](http://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)). Tout comme les [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math). Et bien plus...
    
    Snif, les [intervalles *(Ranges)*](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf) et le [réseau _(Networking)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) ne sont pas intégrés.


5. Bilan C++17 et attentes pour C++20
    
    Version mineure ou majeure ? D'un côté, les améliorations sont nombreuses et appréciables. Mais de l'autre, aucune fonctionnalité majeure n'est intégrée, exceptées celles qui sont déjà disponibles dans [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) (donc déjà supportées par un large panel d'anciens compilateurs). 
        
    * Conséquences sur le processus de standardisation ? 
    * Qu'attendre de C++20 ?
    * Comment s'impliquer ?


Partage
=======
    
Chère lectrice, cher lecteur LinuxFr.org. Tu souhaites nous donner un coup de main pour les dépêches suivantes en cours de rédaction ? Merci de [créer un compte LinuxFr.org](https://linuxfr.org/compte/inscription) et de rejoindre l'[espace de rédaction collaborative](https://linuxfr.org/redaction).
     
Après publication, les dépêches sont figées sur LinuxFr.org. Alors, pour continuer à améliorer ce contenu libre (fôtes, manques, tournures, franglais, maladresses...), n'hésite à pas à  aller sur le dépôt [Git C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/Cxx17). C'est là aussi que tu trouveras les versions de ces dépêches les plus à jour :
    
1. [Les coulisses du standard C++](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md) ;
2. [Genèse d'une version mineure](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md) ;
3. [Nouveautés du langage](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md) ;
4. [Nouveautés de la bibliothèque standard](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n4_Cpp17_Nouveautes-de-la-bibliotheque.md) ;
5. [Bilan et attentes pour C++20](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n5_Bilan-Cpp17-et-attentes-Cpp20.md).
    
Avec toutes nos contributions réunies, nous profiterons d'avantage de nos découvertes individuelles et nous offrirons un contenu CC-BY-SA de qualité pour créer, par exemple, un article Wikipédia C++17 en français :-)

[![Logo C++FRUG représenté par un gros "C++" au centre du cercle de la Francophonie][logoCppFRUG]][logoCppFRUG_WP]
    
[logoCppFRUG]:    http://upload.wikimedia.org/wikipedia/commons/9/91/Cpp-Francophonie.svg
[logoCppFRUG_WP]: http://commons.wikimedia.org/wiki/File:Cpp-Francophonie.svg



Le standard n'est pas libre
===========================
    
La mention de droit d'auteur ne laisse aucun doute, la spécification du standard C++ ne permet pas sa réutilisation :
    
> © ISO/IEC 2014 – All rights reserved  
> COPYRIGHT PROTECTED DOCUMENT  
> All rights reserved. Unless otherwise specified, no part of this publication may be reproduced or utilized otherwise in any form or by any means, electronic or mechanical, including photocopying, or posting on the internet or an intranet, without prior written permission.
> Permission can be requested from either ISO at the address below or ISO’s member body in the country of the requester.
    
L'organisme ISO empêche juridiquement la reproduction du contenu du standard, comme un paragraphe d'une règle ou un exemple de code. Heureusement, dans la pratique, l'organisme ISO ne poursuit personne qui [publie des extraits](http://stackoverflow.com/questions/2693199/do-destructors-have-names-according-to-the-standard) du document.


Le standard est payant
======================
    
De plus, obtenir le standard C++ coûte cher. Même la version PDF téléchargée :
    
* 182 € sur le [site de l'ISO](http://www.iso.org/iso/fr/catalogue_detail?csnumber=64029) (198 francs suisses) ;
* 238 € sur le [site de l'ANSI](http://webstore.ansi.org/RecordDetail.aspx?sku=ISO%2fIEC+14882%3a2014) (265 $ USA).
    
(voir aussi d'[autres site vendant le standard](http://stackoverflow.com/a/83763/938111))


Les anciens standards supprimés
===============================
    
Encore plus incroyable : chaque nouvelle publication du standard révoque/supprime _(withdraw)_ la version précédente :
    
* C++98 [ISO/IEC 14882:1998](http://www.iso.org/iso/fr/catalogue_detail?csnumber=25845) supprimé ;
* C++03 [ISO/IEC 14882:2003](http://www.iso.org/iso/fr/catalogue_detail?csnumber=38110) supprimé ;
* C++11 [ISO/IEC 14882:2011](http://www.iso.org/iso/fr/catalogue_detail?csnumber=50372) supprimé.
    
Ce qui est embêtant est le fait que la plupart des projets C++ actuellement utilisés sont codés en C++03. Et la plupart des entreprises utilisent encore aujourd'hui des versions de compilateurs qui ne supportent pas (ou partiellement) le standard C++11.
    
Alors comment s'informer du standard C++ utilisé par le bon vieux compilateur que l'on est obligé d'utiliser ? Aller les [consulter à l'INRIA](http://opac.inria.fr/search*frf/a?searchtype=Y&searcharg=14882) ? Par exemple, cet [utilisateur a besoin d'acheter le standard C++03 mais celui-ci n'est plus à la vente](http://programmers.stackexchange.com/questions/190294/about-ansi-c-2003-standard).


Et les brouillons du comité ?
=============================
        
Les documents en cours de rédaction _(draft)_ du comité de standardisation sont gratuitement accessibles :
    
* [open-std.org/jtc1/sc22/wg21](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/)
* [github.com/cplusplus/draft](https://github.com/cplusplus/draft/tree/master/papers)
       
Quand le comité de standardisation C++ valide un brouillon (nouvelle version C++), ce brouillon bénéficie [de dernières corrections](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3338.html). Puis, le comité le fournit à l'ISO qui change la mise en forme pour en faire une version officielle.
    
Mais que fait une dépêche qui prône un langage non libre sur un site comme LinuxFr.org ? Chère lectrice, cher lecteur de LinuxFr.org, Devrait on poser un ultimatum à l'ISO et interdire les dépêches C++ tant que l'on n'a pas le droit de copier-coller un bout de code du standard ?


Un standard ouvert tout de même !
=================================
    
Néanmoins, le C++ est bien un [standard ouvert](https://fr.wikipedia.org/wiki/Format_ouvert), sans brevet logiciel, sans propriété intellectuelle. C'est à dire que le langage et sa bibliothèque standard (API) peuvent être implémentés librement. Ce qui n'est pas le cas des langages comme [Java](http://www.lemonde.fr/technologies/article/2014/05/10/brevets-la-bataille-entre-oracle-et-google-sur-java-relancee_4414517_651865.html) ou [C#](https://digitalcitizen.info/2014/11/12/while-open-source-leads-to-patent-traps-free-software-warns-and-liberates/) (troll).
    
De même, le nom **"C++"** n'est pas une marque, ni aucun type de propriété intellectuelle. À la différence de la marque [**JavaScript®**](https://developer.mozilla.org/fr/docs/Web/JavaScript/A_propos#Ressources_JavaScript) déposée par Oracle, ou des marques non déposées [**Rust™**](https://www.mozilla.org/en-US/foundation/trademarks/list/), [**Go™**](https://www.google.fr/intl/fr/permissions/trademark/trademark-list.html) (et une [autre **Go™**](https://www.thoughtworks.com/news/innova-using-thoughtworks-studios-go)).
    
Et même si C++ n'est pas encore aussi ouvert que peut l'être Rust™, de nombreux membres du comité améliorent constamment la façon de travailler pour plus de transparence, plus de proximité avec les utilisateurs C++, comme pour le [compte GitHub du comité](https://github.com/cplusplus).


[![Illustration C++ de Dominic Alves sous license CC-BY-SA 2.0][CppVisImg]][CppVisWeb]
    
[CppVisImg]: http://c2.staticflickr.com/2/1116/785982209_b0da7b4380_o.jpg
[CppVisWeb]: http://www.flickr.com/photos/dominicspics/785982209



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
        
Attention, ce dernier lien est celui du brouillon **C++17** le plus récent lors de la rédaction de cette dépêche. Cette version sera certainement obsolète quelques mois après la publication de cette dépêche.
     
Ceux qui ont l'œil aiguisé remarqueront que le brouillon N3376 représentant la version C++11 a été publiée (2012-02-28) après la norme officielle 14882:2011 (2011-09-01). Ce N3376 correspond en fait à des corrections éditoriales mineures apportées au brouillon [N3291](http://www.joshuaburkholder.com/documents/n3291.pdf) fourni à l'ISO. En anglais, c'est le *first post-publication draft*.


![Analogie entre chaque version C++ et l'évolution depuis le singe jusqu'à homo sapiens puis homo sapiens se courbe de plus en plus pour se retrouver devant un ordinateur qui correspond à la version C++17 et ce dernier homme moderne dit "Cool  On va pouvoir coder"](http://cpp-frug.github.io/materials/images/Cpp-Evolution-Path.svg)


Technical Specification (TS)
============================
    
Les spécifications techniques notées **TS** pour _**T**echnical **S**pecification_ sont les documents de travail les plus importants du comité de standardisation. Ces documents sont la base de discussion des évolutions du standard.
    
Généralement, les spécifications techniques sont composés de deux parties :
    
* La première partie donne les motivation du changement (l'avantage d'avoir telle fonctionnalité dans le C++ avec des exemples de code) ;
* La seconde partie liste toutes les modifications à appliquer au standard C++ en cours de rédaction (au _"draft"_).



Numérotation des documents
==========================
    
A partir de 1990, le comité numérote ses documents officiels sur 4 chiffres en commençant par le n°[`0000`](http://open-std.org/JTC1/SC22/WG21/docs/papers/1990/WG21%201990/X3J16_90-0000%20WG21.pdf). Ce numéro est incrémenté pour chaque nouveau document, ou nouvelle révision d'un document.
    
En 1991, le préfixe **N** est adoptée, et le premier document à en profiter est le [`N0007`](http://open-std.org/JTC1/SC22/WG21/docs/papers/1991/WG21%201991/X3J16_91-0089%20WG21_N0007.pdf). **N** comme _**N**umber_ (Numéro).

Ces numéros **`xxxx`** peuvent paraître obscures, mais sont très importants car ils sont utilisés comme références rigoureuses aux fonctionnalités C++ :
    
* dans les échanges entre membres du comité ;
* par de nombreux [sites web](https://cmake.org/cmake/help/latest/prop_gbl/CMAKE_CXX_KNOWN_FEATURES.html).



Pour faire le lien entre principales spécifications techniques _(TS)_ et leur numéro **`xxxx`** de la révision la plus récente, une astuce est d'utiliser la page [*experimental* sur cppreference.com](http://en.cppreference.com/w/cpp/experimental).


Voici, en exemple, l'historique des TS a propos des "Modules" :
    
Année| Numéro  | Titre | Révision
-----|---------|-------|---
2004 | [`N1736`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1736.pdf) | Modules in C++ | 1
2005 | [`N1778`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1778.pdf) | Modules in C++ | 2
2006 | [`N1964`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1964.pdf) | Modules in C++ | 3
2006 | [`N2073`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n2073.pdf) | Modules in C++ | 4
2007 | [`N2316`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2316.pdf) | Modules in C++ | 5
2012 | [`N3347`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3347.pdf) | Modules in C++ | 6
2014 | [`N4047`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4047.pdf) | A Module System for C++ | 1
2014 | [`N4214`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4214.pdf) | A Module System for C++ | 2
2015 | [`N4465`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4465.pdf) | A Module System for C++ | 3
2016 | [`P0142R0`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf) | A Module System for C++ | 4


Remarquons le changement de nommage pour la révision de 2016. Le nouveau nommage **`PxxxxRx`** a été mis en place en septembre 2015 avec un **P** comme _**P**roposal_ (**P**roposition). Progressivement, les **`PxxxxRx`** doivent remplacer les **`Nxxxx`**. L'avantage est de conserver le même numéro **`xxxx`** pour toutes les révision du document.
    
Comme en C++, on commence par compter la première **R**évision à partir de **`R0`**. L'exemple ci-dessus est un cas particulier : **`R0`** est bien la première révision du nouveau format, mais la quatrième révision des documents _"A Module System for C++"_.


Defect Report (DR)
==================
    
Même après moult relectures par les meilleurs experts C++ au monde, avec toutes les précautions prises par les institutions officielles, les publications des standards C++ contenaient 5000 anomalies ayant fait l'objet, chacune, d'un [rapport d'anomalie _(Defect Report)_](https://isocpp.org/std/submit-issue) !
     
* 2200 rapports d'anomalie au niveau du [langage](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_toc.html) ;
* 2750 rapports d'anomalie au niveau de la [bibliothèque standard](http://www.open-std.org/jtc1/sc22/wg21/docs/lwg-toc.html).
    
Lors des ses réunions, le comité discute des rapports d'anomalie et devrait publier régulièrement des rectificatifs techniques _(Technical Corrigendum)_. Mais le comité n'a jamais publié aucun rectificatif technique à ce jour !
    
Par exemple, le comité avait approuvé un [rectificatif technique en 2003](http://www.open-std.org/jtc1/sc22/wg21/docs/standards). Et finalement, le comité publie comme étant une nouvelle version du standard => **C++03** :
    
> A technical corrigendum was approved in 2003, . and the standard was published again as the ISO/IEC 14882:2003 edition, published 2003-10-16.
    
Bon, c'est vrai, à la décharge du comité, ce rectificatif technique de 2003 contenait une nouvelle fonctionnalité : [*Value  initialization*](http://en.cppreference.com/w/cpp/language/value_initialization#Notes). C'était la dernière fois, que le comité avait travaillé sur un rectificatif technique.


Néanmoins, même si le comité ne publie aucun rectificatif technique, les rapports d'anomalie approuvés doivent être [pris en compte par les compilateurs](http://clang.llvm.org/cxx_dr_status.html). Des sites comme cppreference.com listent les changements induits par ces rapports d'anomalie : 
    
* Quatre rapports d'anomalie pour l'[opérateur ternaire `cond ? a : b`](http://en.cppreference.com/w/cpp/language/operator_other#Defect_reports) ;
* Trois rapports d'anomalie pour les [variables membres](http://en.cppreference.com/w/cpp/language/data_members#Defect_reports) ;
* Trois rapports d'anomalie pour [`return`](http://en.cppreference.com/w/cpp/language/return#Defect_reports) ;
* Deux rapports d'anomalie pour [`throw`](http://en.cppreference.com/w/cpp/language/throw#Defect_reports) ;
* ...
    
Donc, les versions officielles du C++ deviennent vite obsolètes après leur publication car ces documents sont figés et ne bénéficient pas des corrections apportées par les rapports d'anomalie. Par conséquence, celui qui achète une version officielle du standard C++, devrait aussi suivre tous les rapports d'anomalie approuvés par le comité...
    
Pour terminer, notons aussi que des rapports d'anomalie approuvés lors d'une réunion du comité, se retrouvent ne plus être approuvés lors de la réunion suivante.
    
Alors, chère lectrice, cher lecteur LinuxFr.org, es-tu étonné(e) par ce fonctionnement. Connais-tu d'autre façons de maintenir un tel document ? Comment cela se passe dans d'autres langages de programmation ? As-tu des idées d'amélioration ?


Un langage compliqué qui se simplifie
=====================================
    
Par rapport à tous les langages utilisés en production, avouons que le C++ est peut être le langage le plus complexe que l'humanité ait pu inventer ! Les développeurs C++ en ont bien conscience. C'est peut-être la raison pour laquelle les participants aux _meetups_ se montrent souvent bienveillants à l'égard des autres langages. Les développeurs C++ aimeraient un langage plus simple, à condition de **"ne pas sacrifier la sacro-sainte performance"**.
    
Le C++ est tellement vaste et semé de subtilités que les développeurs C++ n'en connaissent bien souvent qu'une petite portion (10%). Ceux qui connaissent vraiment le C++ sur le bout des doigts sont appelés des juristes du C++, ou plus généralement *"language lawyers"* en anglais.
    
Pour inverser la tendance, certains membres du comité de standardisation, comme [Bjarne Stroustrup](https://fr.wikipedia.org/wiki/Bjarne_Stroustrup) (le créateur du C++) souhaitent accélérer l'évolution du langage vers un C++ plus intuitif, plus sûr, et toujours plus performant.

Un process de standardisation qui s'ouvre d'avantage
====================================================
    
C'est dans ce cadre que l'initiative [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines) (Recommandations C++) a été lancée. A la fois pour proposer un sous-ensemble du C++ plus sûr, plus simple et sans sacrifier les performances. Mais aussi pour faire pression sur les membres du comité pour adopter les idées de la *Guidelines Support Library* (Bibliothèque de support des recommandations) [activement implémentée sur le dépôt Git de Microsoft](https://github.com/Microsoft/GSL), mais aussi sur le [dépôt Git de Martin Moene](https://github.com/martinmoene/gsl-lite) qui est compatible avec beaucoup plus de compilateurs.
    
Pour faciliter les contributions au standard, le comité a aussi migré sur [GitHub](https://github.com/cplusplus). Le standard en cours de rédaction/maintenance est sur le dépôt Git [draft](https://github.com/cplusplus/draft) (brouillon). L'intégration d'une fonctionnalité au brouillon (standard en cours de rédaction) est souvent formalisée par une fusion *(merge)* d'une branche **Nxxxx** vers la branche **master**.


Cycle de publication [triannuel](http://www.universalis.fr/dictionnaire/triannuel/)
================================


Après la version majeure **C++98** (et son correctif **C++03**), un nouveau standard C++ devait être publié dans les années suivantes. Comme sa date de publication n'était pas fixée, cette version a été nommée temporairement **C++0x**.
    
Mais, avec le manque de maturité de certaines fonctionnalités et les requêtes continuelles d'ajout de nouvelles fonctionnalités, le comité de standardisation n'arrivait pas à stabiliser le standard. Et finalement **C++0x** a été publié en 2011 ! Ne perdons pas la face, `0x = 11` est correct mathématiquement avec `x = A` en [hexadécimal](https://fr.wikipedia.org/wiki/Syst%C3%A8me_hexad%C3%A9cimal) :-)


Afin d'éviter tout nouveau glissement, le comité a alors décidé de publier un nouveau standard C++ tous les 3 ans, en figeant les fonctionnalités l'année N-1. Avec un cycle d'une version majeure (**C++11**) suivie d'une version mineure (**C++14**).



Malgré des dates de publication figées, les appellations **C++1y** (pour **C++14**) et **C++1z** (pour **C++17**) perdurent. Par exemple, l'[option de compilation `-std=c++1z`](https://gcc.gnu.org/projects/cxx-status.html) ou le [tag c++1z sur stackoverflow](http://stackoverflow.com/tags/c%2b%2b1z/info).


Les membres du comité de standardisation utilisent le terme **C++17** (et non pas C++1z). Soyons confiants, **C++1z** verra bien le jour en 2017 (et non pas en 2018, ni après).



Implémentation de référence
===========================
    
Le comité ne fournit ~~pas~~ plus d'implémentation de référence ou de preuve de concept. Mais les membres du comité travaillent en étroite collaboration avec les éditeurs de compilateurs (notamment GCC et LLVM/Clang).
    
Néanmoins, en 1999, des membres du comité ont quand même créé le projet [Boost.org](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) afin de proposer et valider des implémentations de fonctionnalités candidates de la bibliothèque standard. Ainsi, dès 2005, la publication du brouillon [C++ TR1](https://en.wikipedia.org/wiki/C%2B%2B_Technical_Report_1) est en lien direct avec les développements fournis par le projet Boost.org.
    
D'ailleurs, c'est devenu le parcours classique pour les nouveaux composants de la bibliothèque standard. C'est par exemple le cheminement de `std::filesystem`. Et plus récemment, quand le Français [Joël Falcou](http://www.slideshare.net/SergeyPlatonov/joel-falcou-boostsimd) a [proposé](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3571.pdf) la fonctionnalité [SIMD](https://github.com/NumScale/boost.simd), les membres du comité l'ont invité à [intégrer Boost](http://lists.boost.org/Archives/boost/2014/02/211609.php) dans un premier temps. Cela permet également de vérifier de la popularité d'un composant.


La suite...
===========    
    
La prochaine dépêche va nous permettre d'entrer enfin dans le vif du sujet **C++17**.
    
Merci de nous donner un coup de main à la rédaction des prochaines dépêches **C++17**. Pour participer ou lire en avance les prochaines dépêches :
    
* Se rendre sur l'espace de [rédaction LinuxFr.org](https://linuxfr.org/redaction) (recommandé pour la rédaction) ;
* Directement sur le [dépôt Git *materials*](https://github.com/cpp-frug/materials/tree/gh-pages/Cxx17) du C++FRUG (Groupe des utilisateurs C++ francophones).


Mercis
======



Merci aux nombreux contributeurs sur LinuxFr.org pour avoir traqué les coquilles : Benoît Sibaud, cracky, Lucas, palm123, Adrien Dorsaz, Martin Peres et RyDroid. Merci aussi à rewind, David Demelier et à gasche pour leurs pertinents commentaires.


Merci à Klaim pour avoir identifié des tournures/allusions/erreurs qui pourraient agacer/irriter des lecteurs LinuxFr.org.
    
Merci à [duckie](https://github.com/duckie) pour [ses]((https://github.com/cpp-frug/materials/pull/1)) [contributions](https://github.com/cpp-frug/materials/pull/3) sur le [dépôt Git](https://github.com/cpp-frug/materials/tree/gh-pages/Cxx17).
    
Mais surtout, un immense merci à mes collègues développeurs, qui à défaut de m'aider à la rédaction, ont illustré cette dépêche avec des dessins humoristiques (à prendre au second degré) : Ziyue, AKP, Florent B, et Jae-Zun. Merci aussi à Dominic Alves pour son [dessin C++](https://www.flickr.com/photos/dominicspics/785982209) sous licence libre. Merci à Benjamin, Imen et Youenn pour m'avoir aidé à trouver un dialogue amusant entre les collègues qui ne savent pas que LinuxFr.org parle de C++17.


Merci d'avance de l'aide apportée sur les prochaines dépêches C++17 en cours de préparation : Micka pour ses exemples *utiles* et AMB007 pour les bogues trouvé dans le code C++.


Droit d'auteur et licence
=========================



Le texte est protégé par ~~le [droit d'auteur](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diffusion)~~ la [gauche d'auteur](https://fr.wikipedia.org/wiki/Gauche_d'auteur) et réutilisable sous licence [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr). Les auteurs sont : Oliver H, olibre, duckie, Klaim, Benoît Sibaud, cracky, Lucas, palm123, Adrien Dorsaz, Martin Peres et RyDroid.


Pour les illustrations :
    
* Le logo C++ Francophonie [(disponible sur commons.wikimedia.org)](https://commons.wikimedia.org/wiki/File:Cpp-Francophonie.svg) est dans le [domaine public](https://fr.wikipedia.org/wiki/Domaine_public) (même si ce n'est [pas possible en droit d'auteur](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diffusion)) ;
* Le dessin du [C++ vissé sur de l'électronique](https://www.flickr.com/photos/dominicspics/785982209) est de Dominic Alves sous licence [CC BY-SA 2.0](https://creativecommons.org/licenses/by-sa/2.0/deed.fr) (2007) ;
* L'[évolution du langage C++](https://github.com/cpp-frug/materials/blob/gh-pages/images/Cpp-Evolution-Original.svg) est inspirée d'une œuvre dont les droits de réutilisation n'ont pas été identifiés. La réalisation sous licence [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.fr) est de Florent B. d'après une première ébauche de Jae-Zun (2016) ;
* La police de caractères utilisée par l'illustration sur l'évolution du C++ est la [Purisa](https://github.com/tlwg/fonts-tlwg/commits/master/tlwg/Purisa.sfd) maintenue par [Theppitak Karoonboonyanan](https://github.com/thep) sous licence [GPL-2](https://github.com/tlwg/fonts-tlwg/blob/master/GPL).
