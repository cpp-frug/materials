| Pour contribuer à ce document, merci de lire le [`README.md`](README.md)
|-------------------------------------------------------------------------


Les coulisses du standard C++
=============================


Auteurs |[olibre](https://github.com/olibre), [duckie](https://github.com/duckie), [rom1v](https://github.com/rom1v), [Oliver H](https://linuxfr.org/users/oliver_h), [cracky](https://linuxfr.org/users/cracky), [Lucas](https://linuxfr.org/users/george), [palm123](https://linuxfr.org/users/palm123), [Adrien Dorsaz](https://linuxfr.org/users/trim), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [Davy Defaud](https://linuxfr.org/users/davy78), [ZeroHeure](https://linuxfr.org/users/andrianarivony), [Benoît Sibaud](https://linuxfr.org/users/oumph), [tankey](https://linuxfr.org/users/tankey), [M5oul](https://linuxfr.org/users/m5oul) et [Anthony Jaguenaud](https://linuxfr.org/users/capello)
--------|------------------------------
License | [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)
URL     | https://linuxfr.org/news/les-coulisses-du-standard-cpp
Date    | 2016-08-08T09:10:16+02:00 (publication sur LinuxFr.org)
Tags    | c++, c++14 et c++17
Score   | 84


Le C++ a bientôt la quarantaine et pourtant très actif en ce moment avec la finalisation de la prochaine version C++17. Profitons‐en pour faire le point avec une série d’articles sur le C++. Cette première dépêche nous dévoile la face cachée du C++, et donc peut intéresser tous les lecteurs _LinuxFr.org_. :-)

![Évolution du langage C++](https://cpp-frug.github.io/materials/images/cpp-evolution-path.svg)

----

* [Contenu Markdown de cette dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md)
* [Contenu Markdown de la deuxième dépêche : C++17 — Genèse d’une version mineure](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md)
* [Contenu Markdown de la troisième dépêche : C++17 — Nouveautés au niveau du langage](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md)
* [Contenu Markdown de la quatrième dépêche : C++17 — Nouveautés au niveau de la bibliothèque standard](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n4_Cpp17_Nouveautes-de-la-bibliotheque.md)
* [Contenu Markdown de la cinquième dépêche : Bilan C++17 et attentes C++20](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n5_Bilan-Cpp17-et-attentes-Cpp20.md)
* [Article Wikipédia C++](https://fr.wikipedia.org/wiki/C%2B%2B)
* [Site officiel du comité de normalisation du C++ — Page expliquant le fonctionnement du comité](https://isocpp.org/std/)
* [Dépôt Git officiel du standard C++ en cours de rédaction](https://github.com/cplusplus/draft/)
* [CppReference, wiki libre (CC-BY SA 3.0 et GFDL) pour la documentation C et C++](http://fr.cppreference.com/w/Accueil)
* [Dépêche 2012 par nazcafan : Codeurs, traducteurs, CppReference a besoin de vous](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous)
* [Journal 2016 par serge_sans_paille : [C++14 ] Expressions template pour les nuls](https://linuxfr.org/users/serge_ss_paille/journaux/c-14-expressions-template-pour-les-nuls)

----

![logo "The C++ Programming Language"](https://isocpp.org/files/img/logo1.PNG)


Dépêches C++
============
    
Chère lectrice, cher lecteur de _LinuxFr.org_. Tes collègues sont en vacances et tu cherches à t’occuper ? Ou alors, tu es en vacances et l’actualité informatique te manque déjà ? Eh bien, voici une première dépêche d’une longue série sur le C++. Ainsi, tu seras en avance technologique dès la rentrée.

Résumé des dépêches :
    
1. Cette première dépêche, [_Les coulisses du C++_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n1_Les-coulisses-du-standard.md), présente la naissance du langage, puis du standard, sa spécification non libre, [payant](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=64029), [ouvert](https://fr.wikipedia.org/wiki/Format_ouvert), délaissé au profit de son [brouillon](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf) _(draft)_, peu lu par les développeurs C++, évoluant lentement mais sûrement…
    
2. La deuxième dépêche, [_Genèse du C++17_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n2_Cpp17_Genese-d-une-version-mineure.md), reviendra sur les dernières réunions du comité de normalisation.
    
3. La troisième dépêche, [_Nouveautés C++17 du langage_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n3_Cpp17_Nouveautes-du-langage.md), présentera des changements du langage très intéressants : [déduction des arguments `template`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html) `std::array a{1,2,3};`, [décomposition du retour de fonction](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r2.html) `auto [x, y] = f();` , [`namespace aa::bb{}`](http://en.cppreference.com/w/cpp/language/namespace) équivalent à `namespace aa{ namespace bb{}}`, [`if constexpr`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0128r1.html) sélectionne du code à la compilation, lambda `constexpr`, lambda capture `*this`, [`if(init;condition)`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r0.html) comme `for(init;cond;inc)`, [variables `inline`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r0.pdf)… Mais il faudra encore attendre pour l’intégration des [Concepts](http://fr.cppreference.com/w/cpp/concept), [Modules](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf), [Syntaxe d’appel uniforme](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax#C.2B.2B_proposal) et [Réflexion](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0194r1.html).
    
4. La quatrième dépêche, [_Nouveautés C++17 de la bibliothèque standard_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n4_Cpp17_Nouveautes-de-la-bibliotheque.md), présentera les changements au niveau de la bibliothèque standard qui pourraient bousculer notre petite vie de développeur : [algorithmes parallélisés](http://en.cppreference.com/w/cpp/experimental/parallelism#Parallelized_versions_of_existing_algorithms), [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view), [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem), [`std::variant`](http://en.cppreference.com/w/cpp/utility/variant), [`std::any`](http://en.cppreference.com/w/cpp/utility/any), [`std::optional`](http://en.cppreference.com/w/cpp/utility/optional), les [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math)… Mais, les [intervalles (_ranges_)](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf), le [réseau (_networking_)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) seront intégrés pour une version ultérieure.
    
5. [_Bilan C++17 et attentes pour C++20_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n5_Bilan-Cpp17-et-attentes-Cpp20.md). Version mineure ou majeure ? D’un côté, les améliorations sont nombreuses et appréciables. Mais de l’autre, aucune fonctionnalité majeure n’est intégrée, exceptées celles qui sont déjà disponibles dans [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) (donc déjà supportées par un large panel d’anciens compilateurs). Conséquences sur le processus de normalisation ? Qu’attendre de C++20 ? Intérêt du C++ aujourd’hui ? Et les langages alternatifs ? Comment s’impliquer ?
    
6. … d’autres dépêches à venir. :-)

[![Logo C++FRUG représenté par un gros "C++" au centre du cercle de la Francophonie][logoCppFRUG]][logoCppFRUG_WP]
    
[logoCppFRUG]:    http://upload.wikimedia.org/wikipedia/commons/9/91/Cpp-Francophonie.svg
[logoCppFRUG_WP]: http://commons.wikimedia.org/wiki/File:Cpp-Francophonie.svg


Partage
=======
    
Chère lectrice, cher lecteur _LinuxFr.org_. Tu souhaites donner un coup de main pour les dépêches suivantes ? Rejoins‐nous dans l’[espace de rédaction collaborative sur _LinuxFr.org_](https://linuxfr.org/redaction). Un [compte](https://linuxfr.org/compte/inscription) est nécessaire pour y accéder.
    
Après publication, les dépêches sont figées sur _LinuxFr.org_. Alors, pour continuer à améliorer ce contenu libre (fôtes, oublis, franglais, maladresses…), n’hésite à pas à  aller sur le dépôt [Git C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/Cxx17). C’est là aussi que tu trouveras les versions de ces dépêches les plus à jour :
    
1. [_Les coulisses du standard C++_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md) ;
2. [_Genèse d’une version mineure_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md) ;
3. [_Nouveautés du langage_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md) ;
4. [_Nouveautés de la bibliothèque standard_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n4_Cpp17_Nouveautes-de-la-bibliotheque.md) ;
5. [_Bilan et attentes pour C++20_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n5_Bilan-Cpp17-et-attentes-Cpp20.md).
    
Avec toutes nos contributions réunies, nous profiterons davantage de nos découvertes individuelles et nous offrirons un contenu CC BY-SA de qualité pour créer, par exemple, un article Wikipédia C++17 en français. :-)

Naissance d’un nouveau langage
==============================
    
À la fin des années 70, dans la cadre de sa thèse en Angleterre, le Danois Bjarne Stroustrup [étudiait](http://www.stroustrup.com/hopl2.pdf) le [paradigme de la programmation objet](https://fr.wikipedia.org/wiki/Programmation_orient%C3%A9e_objet) (avec le langage [Simula](https://fr.wikipedia.org/wiki/Simula)). En 1979, aux [Laboratoires Bell](https://fr.wikipedia.org/wiki/Laboratoires_Bell) (États‐Unis), Bjarne propose de rajouter ce paradigme objet au langage C qu’il appela « _C with Classes_ ».
    
Durant les années 80, les nouvelles fonctionnalités qui sont progressivement intégrées au tout nouveau C++ provoque un schisme entre les fans du C classique et les enthousiastes du C++.

![Bjarne Stroustrup](https://upload.wikimedia.org/wikipedia/commons/d/da/BjarneStroustrup.jpg)

Création du comité de normalisation C++
=======================================
    
Dans la seconde moitié des années 80, le [_usenet_](https://fr.wikipedia.org/wiki/Usenet) **comp.lang.c++** bouillonne, les premiers compilateurs C++ commencent à diverger, les développeurs ont du mal à écrire du C++ portable et dix ans après la création du _C with Classes_, des événements majeurs se produisent :
    
* avril 1989, le groupe de travail [WG14](http://www.open-std.org/jtc1/sc22/wg14/) (comité du C) souhaite une normalisation du C++ ;
* mai 1989, à la demande du WG14, Andrew Koenig et Bjarne Stroustrup rédigent [_C++: as close as possible to C — but no closer_](http://isotc.iso.org/livelink/livelink/fetch/-8919800/8919823/16475317/16849788/C%2B%2B_as_close_as_possible_to_C_but_no_closer.pdf?nodeid=16849089), pour expliquer les divergences (incompatibilités) du **C++** par rapport au **C** (ce qui est valide en C et qui ne l’est pas en C++) ;
* juillet 1989, Dmitry Lenkov explique la [création d’un groupe de travail C++ officiel](http://open-std.org/JTC1/SC22/WG21/docs/papers/1989/X3_89-738R%20Programming%20Language%20C++%20Proposal.pdf) et d’y inclure d’office Bjarne Stroustrup ;
* février 1990, première réunion du comité [ANSI](https://fr.wikipedia.org/wiki/American_National_Standards_Institute) C++ ;
* juin 1991, la réunion du comité ANSI C++ réunit de très nombreux participants non états‐uniens et la décision est prise de travailler conjointement avec le groupe de travail [WG21](http://www.open-std.org/jtc1/sc22/wg21/) international.

![Organisation du WG21](https://isocpp.org/files/img/wg21-structure.png)

Sigle &emsp; | Définition
-------|------------------------
ISO    | [Organisation internationale de normalisation](https://fr.wikipedia.org/wiki/Organisation_internationale_de_normalisation)
IEC    | [Commission électrotechnique internationale](https://fr.wikipedia.org/wiki/Commission_%C3%A9lectrotechnique_internationale)
JTC 001| [_Joint Technical Committee_ 001](https://fr.wikipedia.org/wiki/Joint_Technical_Committee_1)
SC 22  | [_Subcommittee 22_](https://en.wikipedia.org/wiki/ISO/IEC_JTC_1/SC_22) (sous‐comité 22) dédié aux langages de programmation, leur environnement et les interfaces avec les logiciels système
WG 14  | _Working Group 14_ (groupe de travail 14) dédié au langage C ([WG 14 sur le site de l’ISO](http://isotc.iso.org/livelink/livelink?func=ll&objId=8919800))
WG 21  | _Working Group 21_ dédié au C++ ([WG 21 sur le site de l’ISO](http://isotc.iso.org/livelink/livelink?func=ll&objId=8918410))

La puissance du C++
===================
    
En 1991, un nouveau paradigme, la [programmation générique](https://fr.wikipedia.org/wiki/G%C3%A9n%C3%A9ricit%C3%A9) (`template`) est ajouté, ainsi que les [exceptions](https://fr.wikipedia.org/wiki/Syst%C3%A8me_de_gestion_d%27exceptions).
    
Le C++ devient alors un formidable langage alliant un découplage puissant et la performance du code exécutable optimisé par les compilateurs C adaptés (cette flexibilité est très bien illustrée dans l’excellent journal [_Expressions template pour les nuls_](https://linuxfr.org/users/serge_ss_paille/journaux/c-14-expressions-template-pour-les-nuls) de [_serge_sans_paille_](http://serge.liyun.free.fr/serge/)). Mais cette compatibilité avec le langage C contraint à utiliser une grammaire pas toujours simple et un temps de compilation souvent long.
    
En 1994, Erwin Unruh présente au comité C++ un [code source qui permet de calculer les nombres premiers à la compilation](http://www.erwin-unruh.de/primorig.html). Pour une partie des membres du comité, c’était une curiosité. Tandis que les autres membres se grattaient la tête et prirent conscience que l’on venait de découvrir, par hasard, que les _templates_ du C++ permettaient le paradigme de la [métaprogrammation](https://fr.wikipedia.org/wiki/M%C3%A9taprogrammation) !
    
Cette découverte ouvre la voie à d’extraordinaires optimisations en permettant au compilateur de réaliser des calculs **à la compilation** (à ne pas confondre avec la réalisation de calculs à l’initialisation ou durant l’exécution). Ces techniques atteignent des sommets avec [`boost::mpl`](http://www.boost.org/libs/mpl) (2002), [`boost::proto`](http://www.boost.org/libs/proto) (2008) et le futur [`boost::simd`](https://github.com/NumScale/boost.simd).
    
Au détriment d’une grammaire difficile, des erreurs faciles, d’une compilation lente et d’un débogage laborieux. Mais c’est un des rares langages qui offre au développeur autant d’abstraction et de performance en même temps. La passion de ce langage l’emporte. Avec le temps, les pièges sont connus, les techniques maîtrisés, et le C++ devient un vrai bonheur. :-)
    
De plus, ce langage bien vivant continue d’évoluer dans le bon sens. Les très nombreux outils qui orbitent autour de ce formidable langage continuent aussi d’apporter plein de nouvelles fonctionnalités. :-D

![C++ entouré d'autres langages de programmation](https://isocpp.org/files/img/C++14.jpg)


Les membres du comité de normalisation
======================================
    
En 1998, les membres finalisent le premier standard C++ : **C++98**. Soit une vingtaine d’années après la création du langage, et une dizaine d’années après l’initiative de normaliser celui‐ci.
    
Pour [devenir](http://www.boost.org/community/committee.html) membre du [comité](https://isocpp.org/std/the-committee) international de normalisation du C++, appelé officiellement **ISO/IEC JTC 001/SC 22/WG 14/WG 21**, il faut être membre d’une [représentation ISO de son pays](http://www.iso.org/iso/fr/home/about/iso_members.htm). Une dizaine de pays est représentée :
    
* États‐Unis ([Task Group PL22.16](http://www.incits.org/committees/pl22.16) de l’ANSI) ;
* France ([Comité de Normalisation Cpp](http://norminfo.afnor.org/structure/commid=119670) de l’AFNOR) ;
* Allemagne  ([DIN](https://fr.wikipedia.org/wiki/Deutsches_Institut_f%C3%BCr_Normung)) ;
* Royaume‐Uni ([BSI](http://www.iso.org/iso/fr/home/about/iso_members/iso_member_body.htm?member_id=2064)) ;
* Canada ([SCC](http://www.iso.org/iso/fr/home/about/iso_members/iso_member_body.htm?member_id=1619)) ;
* Finlande 	[SFS](http://www.iso.org/iso/fr/home/about/iso_members/iso_member_body.htm?member_id=1734) ;
* Pays-Bas 	([NEN](http://www.iso.org/iso/fr/home/about/iso_members/iso_member_body.htm?member_id=2027)) ;
* Espagne ([AENOR](http://www.iso.org/iso/fr/home/about/iso_members/iso_member_body.htm?member_id=1717)) ;
* Suisse 	([SNV](http://www.iso.org/iso/fr/home/about/iso_members/iso_member_body.htm?member_id=2106)) ;
* Italie 	([UNI](http://www.iso.org/iso/fr/home/about/iso_members/iso_member_body.htm?member_id=1823)).
    
C’était IBM qui payait les frais de représentation du *Comité de Normalisation Cpp* de l’AFNOR. Mais, au départ à la retraite des employés IBM membres C++, plus personne ne payait les frais de représentation et la France n’était plus officiellement représentée. Depuis peu, les choses sont rentrés dans l’ordre.
    
Une centaine de [membres](https://isocpp.org/wiki/faq/wg21) actifs se rencontrent quelque fois par an dans le cadre de la normalisation du C++ (essentiellement pour voter). Le plus gros du travail se fait à distance. Les membres C++ et les autres passionnés du C++ se rencontrent également lors des grandes rencontres du C++ : [_CppCon_](http://cppcon.org/), [_C++Now_](http://cppnow.org/), [_Meeting C++_](https://meetingcpp.com/)…

&nbsp; |   |
-------|---|---
![Logo CppCon](https://meetingcpp.com/tl_files/mcpp/sponsoren/cppcon-logo-250.png) | ![Logo C++Now](https://isocpp.org/files/img/cppnow-logo.PNG) |


Dans l’intérêt des utilisateurs du C++, les membres du comité [accordent au comité et à l’ISO une licence](https://isocpp.org/home/terms-of-use) *mondiale, non exclusive, irrévocable, permettant l’octroi d’une sous‐licence transférable pour l’affichage du contenu, la reproduction, l’adaptation, la distribution, la création de travaux dérivés à des fins commerciales ou non commerciales*. En 2012, cette règle a notamment été rappelée à IBM, Intel et  Oracle (voir [N3423 §2.4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3423.pdf)).

Le standard ne peut être reproduit
==================================
    
Comme la plupart des documents publiés par l’ISO, la mention de droit d’auteur indique que la reproduction n’est pas autorisée :
    
> ![Logo ISO](https://isocpp.org/files/img/iso.png)  
> © ISO/IEC 2014 — All rights reserved  
> COPYRIGHT PROTECTED DOCUMENT  
> _All rights reserved. Unless otherwise specified, no part of this publication may be reproduced or utilized otherwise in any form or by any means, electronic or mechanical, including photocopying, or posting on the internet or an intranet, without prior written permission.
> Permission can be requested from either ISO at the address below or ISO’s member body in the country of the requester._
    
Cette position est la même pour les autres langages gérés par l’ISO (Fortran, C…). Mais aussi pour [Java](https://docs.oracle.com/javase/specs/jls/se8/html/jls-0-front.html), [C#](https://github.com/KvanTTT/CSharp-Minifier/blob/master/CSharp%20Language%20Specification.docx) et de nombreux autres.
    
Dans la pratique, cela ne gène pas les développeurs de ces langages. Ce type de mention empêche juridiquement la reproduction du standard (même un paragraphe ou un code d’exemple). Des sites qui respectent à la lettre le droit d’auteur, comme Wikipédia, refusent de contenir la reproduction même partielle d’un tel document. D’autres sites, comme _stackoverflow_, sont [plus pragmatiques](http://stackoverflow.com/questions/2693199/do-destructors-have-names-according-to-the-standard).
    
Notons que d’autres langages de programmation ont des spécifications libres :
    
* les [documentations officielles de Rust](https://doc.rust-lang.org/) sont sous licence Apache 2.0 ou licence MIT ;
* la [spécification de Go](https://golang.org/ref/spec) est sous licence CC-BY 3.0 ;
* celle de Python… c’est un peu plus compliqué, simplifions en mentionnant juste la [licence PSF (_Python Software Foundation_)](https://docs.python.org/3/license.html#psf-license-agreement-for-python-release).

Le standard est payant
======================
    
De plus, obtenir le standard C++ coûte cher. Même la version PDF téléchargée :
    
* 182 € sur le [site de l’ISO](http://www.iso.org/iso/fr/catalogue_detail?csnumber=64029) (198 francs suisses) ;
* 238 € sur le [site de l’ANSI](http://webstore.ansi.org/RecordDetail.aspx?sku=ISO%2fIEC+14882%3a2014) (265 US$).
    
(voir aussi d’[autres sites vendant le standard](http://stackoverflow.com/a/83763/938111))

![Logo C++ en forme hexadécimal](https://isocpp.org/files/img/logo-hex.png)


Les anciens standards supprimés
===============================
    
Encore plus incroyable : chaque nouvelle publication du standard révoque ou supprime (_withdraw_) la version précédente :
    
* C++98 [ISO/IEC 14882:1998](http://www.iso.org/iso/fr/catalogue_detail?csnumber=25845) supprimé ;
* C++03 [ISO/IEC 14882:2003](http://www.iso.org/iso/fr/catalogue_detail?csnumber=38110) supprimé ;
* C++11 [ISO/IEC 14882:2011](http://www.iso.org/iso/fr/catalogue_detail?csnumber=50372) supprimé.
    
L’embêtant est que la plupart des projets C++ actuellement utilisés sont codés en C++03. Et la plupart des entreprises utilisent encore aujourd’hui des versions de compilateurs qui ne supportent pas (ou partiellement) le standard C++11.
    
Alors, comment s’informer du standard C++ utilisé par le bon vieux compilateur que l’on est obligé d’utiliser ? Aller les [consulter à l’INRIA](http://opac.inria.fr/search*frf/a?searchtype=Y&searcharg=14882) ? Par exemple, cet [utilisateur a besoin d’acheter le standard C++03 qui n’est plus à la vente](http://programmers.stackexchange.com/questions/190294/about-ansi-c-2003-standard).

Ouf, les brouillons du comité
=============================
        
Les documents en cours de rédaction (_draft_) du comité de normalisation sont gratuitement accessibles :
    
* [open-std.org/jtc1/sc22/wg21](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/) ;
* [github.com/cplusplus/draft](https://github.com/cplusplus/draft/tree/master/papers).
       
Quand le comité de normalisation C++ valide un brouillon (nouvelle version C++), ce brouillon bénéficie de [dernières corrections](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3338.html). Puis, le comité le fournit à l’ISO qui change la mise en forme pour en faire une version officielle.

Documentations C++ de référence
===============================
    
Les standards C++ (officiels ou brouillons) ne sont pas simples à lire. Ces documents utilisent une terminologie très spécifique pour une spécification très rigoureuse. En fait, ces documents sont surtout utiles aux développeurs des compilateurs et à ceux qui implémentent des bibliothèques standards (`std::`).
    
Les utilisateurs du C++ (langage et bibliothèque standard) utilisent historiquement des livres (souvent ceux écrits par Bjarne Stroustrup et Scott Meyers) et plus récemment des sites Web :
    
* [_fr.cppreference.com_](http://fr.cppreference.com) en français sous double licence CC BY-SA 3.0 et GFDL (disponible en différentes langues, la [version en anglais](http://en.cppreference.com) est la plus à jour) ;
* [cplusplus.com](http://cplusplus.com/) seulement en anglais et n’autorisant pas la reproduction (pas de licence libre) ;
* … liste à compléter dans les commentaires.


&nbsp;  |   |   |   |
--------|---|---|---|---
![livre _The C++ Programming Language_](https://isocpp.org/files/img/tcpl4e.png) | ![livre _A Tour of C++_](https://isocpp.org/files/img/tour.jpg) | ![livre _The C++ Programming Language (Special 3rd Edition)_](http://www.pdfdrive.net/assets/thumbs/069/069cb03b9970368939ef71f49534cc4b-s.jpg) |  ![logo cppreference.com](http://cppcon.org/wp-content/uploads/2014/08/community-cppreference.png) |

Un standard ouvert
==================
    
**Note des auteurs de cette dépêche :** _Nous avons un profil plutôt technique (développeurs) et non pas juriste. Ce chapitre contient peut‐être des erreurs importantes, mais nous avons tenté de rédiger ce qui nous semble correct… Nous n’avons pas pris le risque de nous aventurer à comparer C++ avec [Java](http://www.lemonde.fr/technologies/article/2014/05/10/brevets-la-bataille-entre-oracle-et-google-sur-java-relancee_4414517_651865.html), [C#](https://digitalcitizen.info/2014/11/12/while-open-source-leads-to-patent-traps-free-software-warns-and-liberates/)… Celles et ceux qui connaissent bien le sujet, merci de nous éclairer dans les commentaires. :-)_

Le C++ est bien un [standard ouvert](https://fr.wikipedia.org/wiki/Format_ouvert), sans brevet logiciel, sans propriété intellectuelle. C’est‐à‐dire que le langage et sa bibliothèque standard (API) peuvent être implémentés librement.
    
De même, le nom _C++_ n’est pas une marque, ni aucun type de propriété intellectuelle. À la différence de la marque [**JavaScript®**](https://developer.mozilla.org/fr/docs/Web/JavaScript/A_propos#Ressources_JavaScript) déposée par Oracle, ou des marques non déposées [**Rust™**](https://www.mozilla.org/en-US/foundation/trademarks/list/), [**Go™**](https://www.google.fr/intl/fr/permissions/trademark/trademark-list.html) (et une [autre **Go™**](https://www.thoughtworks.com/news/innova-using-thoughtworks-studios-go)).
    
Et, même si C++ n’est pas encore aussi ouvert que peut l’être Rust™, de nombreux membres du comité améliorent constamment la façon de travailler pour plus de transparence et plus de proximité avec les utilisateurs C++, comme l’utilisation d’un [compte GitHub](https://github.com/cplusplus).

Les versions C++
================
    
Même si le langage [naît à la fin des années 1970](http://en.cppreference.com/w/cpp/language/history), il n’est normalisé que vingt ans plus tard, afin d’arrêter la profusion de [versions C++ incompatibles](http://open-std.org/JTC1/SC22/WG21/docs/papers/1989/X3_89-738R%20Programming%20Language%20C++%20Proposal.pdf).
    
Le tableau suivant liste les différentes versions C++ normalisées, ainsi que le brouillon **C++17** en cours de consolidation. Nous pouvons remarquer le saut considérable du nombre de pages entre **C++03** et **C++11**.
              
Version   | Pages
----------|-------
C++98 [ISO/IEC 14882:1998 1998-09-01](http://www.lirmm.fr/~ducour/Doc-objets/ISO+IEC+14882-1998.pdf) | 776 pages
C++03 [ISO/IEC 14882:2003 2003-10-15](https://github.com/hstefan/htlib/blob/master/res/INCITS%2BISO%2BIEC%2B14882-2003.pdf) | 786 pages (+ 1 %)
C++11 [ISO/IEC 14882:2011 2011-09-01](http://new.vk.com/doc100509572_160085962?hash=6801602629449dfa59&dl=27c32949114b3322a2)| 1356 pages (+ 73 %)
C++11 [Draft N3376 2012-02-28](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3376.pdf)| 1 324 pages
C++14 [Draft N4296 2014-11-19](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf) | 1 368 pages (+ 3 %)
C++17 [Draft N4606 2016-07-12](https://github.com/cplusplus/draft/blob/master/papers/n4606.pdf)| 1 586 pages (+ 16 %)
        
Attention, ce dernier lien est celui du brouillon **C++17** le plus récent lors de la rédaction de cette dépêche. Cette version sera certainement obsolète quelques mois après la publication de cette dépêche.
     
Ceux qui ont l’œil aiguisé remarqueront que le brouillon N3376 représentant la version C++11 a été publiée (28/02/2012) après la norme officielle 14882:2011 (1/09/2011). Ce N3376 correspond en fait à des corrections éditoriales mineures apportées au brouillon [N3291](http://www.joshuaburkholder.com/documents/n3291.pdf) fourni à l’ISO. C’est le premier brouillon de post‐publication, le _first post‐publication draft_ en anglais.

![Analogie entre chaque version C++ et l'évolution depuis le singe jusqu'à homo sapiens puis homo sapiens se courbe de plus en plus pour se retrouver devant un ordinateur qui correspond à la version C++17 et ce dernier homme moderne dit Cool  On va pouvoir coder](http://cpp-frug.github.io/materials/images/cpp-evolution-path.svg)

Technical Specification (TS)
============================
    
Les spécifications techniques, notées **TS** pour _**T**echnical **S**pecification_, sont les documents de travail les plus importants du comité de normalisation. Ces documents sont la base de discussion des évolutions du standard.
    
Généralement, les spécifications techniques sont composées de deux parties :
    
* la première partie donne les motivation du changement (l’avantage d’avoir telle fonctionnalité dans le C++ avec des exemples de code) ;
* la seconde partie liste toutes les modifications à appliquer au standard C++ en cours de rédaction (au _draft_).

[![Illustration C++ de Dominic Alves sous license CC-BY-SA 2.0][CppVisImg]][CppVisWeb]
    
[CppVisImg]: http://c2.staticflickr.com/2/1116/785982209_b0da7b4380_o.jpg
[CppVisWeb]: http://www.flickr.com/photos/dominicspics/785982209

Numérotation des documents
==========================
    
À partir de 1990, le comité numérote ses documents officiels sur quatre chiffres en commençant par le n°[`0000`](http://open-std.org/JTC1/SC22/WG21/docs/papers/1990/WG21%201990/X3J16_90-0000%20WG21.pdf). Ce numéro est incrémenté pour chaque nouveau document ou nouvelle révision d’un document.
    
En 1991, le préfixe **N** est adoptée, et le premier document à en profiter est le [`N0007`](http://open-std.org/JTC1/SC22/WG21/docs/papers/1991/WG21%201991/X3J16_91-0089%20WG21_N0007.pdf). **N** comme _**N**umber_ (numéro).

Ces numéros **`xxxx`** peuvent paraître obscurs, mais sont très importants, car ils sont utilisés comme références rigoureuses aux fonctionnalités C++ :
    
* dans les échanges entre membres du comité ;
* par de nombreux [sites Web](https://cmake.org/cmake/help/latest/prop_gbl/CMAKE_CXX_KNOWN_FEATURES.html).

Pour faire le lien entre les principales spécifications techniques _(TS)_ et leur numéro **`xxxx`** de révision la plus récente, une astuce est d’utiliser la page [_experimental_ sur _cppreference.com_](http://en.cppreference.com/w/cpp/experimental).

Voici, en exemple, l’historique des TS à propos des _Modules_ :
    
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

Remarquons le changement de nommage pour la révision de 2016. Le nouveau nommage **`PxxxxRx`** a été mis en place en septembre 2015. Le **P** signifie en anglais _**P**aper_. Progressivement, les **`PxxxxRx`** doivent remplacer les **`Nxxxx`**. L’avantage est de conserver le même numéro **`xxxx`** pour toutes les révisions du document.
    
Comme en C++, on commence par compter la première **R**évision à partir de **`R0`**. L’exemple ci‐dessus est un cas particulier : **`R0`** est bien la première révision du nouveau format, mais la quatrième révision des documents _A Module System for C++_.

Defect Report (DR)
==================
    
Même après moult relectures par les meilleurs experts C++ au monde, avec toutes les précautions prises par les institutions officielles, les publications des standards C++ contenaient 5 000 anomalies ayant fait l’objet, chacune, d’un [rapport d’anomalie (_Defect Report_)](https://isocpp.org/std/submit-issue) !
     
* 2 200 rapports d’anomalie au niveau du [langage](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_toc.html) ;
* 2 750 rapports d’anomalie au niveau de la [bibliothèque standard](http://www.open-std.org/jtc1/sc22/wg21/docs/lwg-toc.html).
    
Lors de ses réunions, le comité discute des rapports d’anomalie et devrait publier régulièrement des rectificatifs techniques (_Technical Corrigendum_). Mais le comité n’a jamais publié aucun rectificatif technique à ce jour !
    
Par exemple, le comité avait approuvé un [rectificatif technique en 2003](http://www.open-std.org/jtc1/sc22/wg21/docs/standards). Et, finalement, le comité publie comme étant une nouvelle version du standard, le **C++03** :
    
> _A technical corrigendum was approved in 2003, and the standard was published again as the ISO/IEC 14882:2003 edition, published 2003-10-16._
    
Bon, c’est vrai, à la décharge du comité, ce rectificatif technique de 2003 contenait une nouvelle fonctionnalité : [_Value initialization_](http://en.cppreference.com/w/cpp/language/value_initialization#Notes). C’était la dernière fois, que le comité avait travaillé sur un rectificatif technique.

Néanmoins, même si le comité ne publie aucun rectificatif technique, les rapports d’anomalie approuvés doivent être [pris en compte par les compilateurs](http://clang.llvm.org/cxx_dr_status.html). Des sites comme _cppreference.com_ listent les changements induits par ces rapports d’anomalie :
    
* quatre rapports d’anomalie pour l’[opérateur ternaire `cond ? a : b`](http://en.cppreference.com/w/cpp/language/operator_other#Defect_reports) ;
* trois rapports d’anomalie pour les [variables membres](http://en.cppreference.com/w/cpp/language/data_members#Defect_reports) ;
* trois rapports d’anomalie pour [`return`](http://en.cppreference.com/w/cpp/language/return#Defect_reports) ;
* deux rapports d’anomalie pour [`throw`](http://en.cppreference.com/w/cpp/language/throw#Defect_reports)…
    
Les versions officielles du C++ deviennent donc vite obsolètes après leur publication, car ces documents sont figés et ne bénéficient pas des corrections apportées par les rapports d’anomalie. Par conséquence, celui qui achète une version officielle du standard C++, devrait aussi suivre tous les rapports d’anomalie approuvés par le comité…
    
Pour terminer, notons aussi que des rapports d’anomalie approuvés lors d’une réunion du comité se retrouvent ne plus être approuvés lors de la réunion suivante.
    
Alors, chère lectrice, cher lecteur de _LinuxFr.org_, es‐tu étonné(e) par ce fonctionnement. Connais‐tu d’autres façons de maintenir un tel document ? Comment cela se passe‐t‐il dans d’autres langages de programmation ? As‐tu des idées d’amélioration ?

Un langage compliqué qui se simplifie
=====================================
    
Par rapport à tous les langages utilisés en production, avouons que le C++ est peut‐être le langage le plus complexe que l’humanité ait pu inventer ! Les développeurs C++ en ont bien conscience. C’est peut‐être la raison pour laquelle les participants aux _meetups_ se montrent souvent bienveillants à l’égard des autres langages. Les développeurs C++ aimeraient un langage plus simple, à condition de « **ne pas sacrifier la sacro‐sainte performance** ».
    
Le C++ est tellement vaste et semé de subtilités, que les développeurs C++ n’en connaissent bien souvent qu’une petite portion. Ainsi, lors d’un entretien de Bjarne Stroustrup (un des experts C++ les plus actifs du comité), celui‐ci avait indiqué qu’il connaissait seulement 60 % du standard. Ceux qui maîtrisent vraiment le C++ sur le bout des doigts sont appelés des juristes du C++, ou plus généralement « _language lawyers_ » en anglais (ils ne sont pas forcément de bons développeurs).
    
![Bjarne Strouput](https://isocpp.org/files/img/bigthink-stroustrup.PNG)
    
Pour inverser la tendance, certains membres du comité de normalisation, comme [Bjarne Stroustrup](https://fr.wikipedia.org/wiki/Bjarne_Stroustrup) (le créateur du C++) souhaitent accélérer l’évolution du langage vers un C++ plus intuitif, plus sûr, et toujours plus performant.

Un processus de normalisation qui s’ouvre davantage
==================================================
    
C’est dans ce cadre que l’initiative [_C++ Core Guidelines_](https://github.com/isocpp/CppCoreGuidelines) (Recommandations C++) a été lancée. A la fois pour proposer un sous‐ensemble du C++ plus sûr, plus simple et sans sacrifier les performances. Mais aussi pour faire pression sur les membres du comité pour adopter les idées de la _Guidelines Support Library_ (Bibliothèque de support des recommandations) [activement implémentée sur le dépôt Git de Microsoft](https://github.com/Microsoft/GSL), mais aussi sur le [dépôt Git de Martin Moene](https://github.com/martinmoene/gsl-lite) qui est compatible avec beaucoup plus de compilateurs.
    
Pour faciliter les contributions au standard, le comité a aussi migré sur [GitHub](https://github.com/cplusplus). Le standard en cours de rédaction/maintenance est sur le dépôt Git [_draft_](https://github.com/cplusplus/draft) (brouillon). L’intégration d’une fonctionnalité au brouillon (standard en cours de rédaction) est souvent formalisée par une fusion (_merge_) d’une branche **Nxxxx** vers la branche **master**.

Cycle de publication [triannuel](http://www.universalis.fr/dictionnaire/triannuel/)
================================
Après la version majeure **C++98** (et son correctif **C++03**), un nouveau standard C++ devait être publié dans les années suivantes. Comme sa date de publication n’était pas fixée, cette version a été nommée temporairement **C++0x**.
    
Mais, avec le manque de maturité de certaines fonctionnalités et les requêtes continuelles d’ajout de nouvelles fonctionnalités, le comité de normalisation n’arrivait pas à stabiliser le standard. Et, finalement, **C++0x** a été publié en 2011 ! Ne perdons pas la face, `0x = 11` est correct mathématiquement avec `x = B` en [hexadécimal](https://fr.wikipedia.org/wiki/Syst%C3%A8me_hexad%C3%A9cimal) :-)

Afin d’éviter tout nouveau glissement, le comité a alors décidé de publier un nouveau standard C++ tous les trois ans, en figeant les fonctionnalités l’année _n_ - 1. Avec un cycle d’une version majeure (**C++11**) suivie d’une version mineure (**C++14**).

Malgré des dates de publication figées, les appellations **C++1y** (pour **C++14**) et **C++1z** (pour **C++17**) perdurent. Par exemple, l’[option de compilation `-std=c++1z`](https://gcc.gnu.org/projects/cxx-status.html) ou l’[étiquette _c++1z_ sur _stackoverflow_](http://stackoverflow.com/tags/c%2b%2b1z/info).

Les membres du comité de normalisation utilisent le terme **C++17** (et non pas _C++1z_). Soyons confiants, **C++1z** verra bien le jour en 2017 (et non pas en 2018, ni après).

Implémentation de référence
===========================
    
Le comité ne fournit ~~pas~~ plus d’implémentation de référence ou de preuve de concept. Mais les membres du comité travaillent en étroite collaboration avec les éditeurs de compilateurs (notamment GCC et LLVM/Clang).


&nbsp;  |   |
--------|---|---
![logo GCC](https://upload.wikimedia.org/wikipedia/commons/thumb/a/af/GNU_Compiler_Collection_logo.svg/200px-GNU_Compiler_Collection_logo.svg.png) | ![logo LLVM](https://isocpp.org/files/img/llvm.png) |
   

Néanmoins, en 1999, des membres du comité ont quand même créé le projet [_Boost.org_](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) afin de proposer et valider des implémentations de fonctionnalités candidates de la bibliothèque standard. Ainsi, dès 2005, la publication du brouillon [_C++ TR1_](https://en.wikipedia.org/wiki/C%2B%2B_Technical_Report_1) est en lien direct avec les développements fournis par le projet _Boost.org_.
    
![logo Boost.org](https://isocpp.org/files/img/boost.png)
    
D’ailleurs, c’est devenu le parcours classique pour les nouveaux composants de la bibliothèque standard. C’est, par exemple, le cheminement de `std::filesystem`. Et plus récemment, quand le Français [Joël Falcou](http://www.slideshare.net/SergeyPlatonov/joel-falcou-boostsimd) a [proposé](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3571.pdf) la fonctionnalité [SIMD](https://github.com/NumScale/boost.simd "Single instruction, multiple data"), les membres du comité l’ont invité à [intégrer Boost](http://lists.boost.org/Archives/boost/2014/02/211609.php) dans un premier temps. Cela permet également de vérifier la popularité d’un composant.

La suite...
===========
    
La prochaine dépêche va nous permettre d’entrer enfin dans le vif du sujet **C++17**.
    
Merci de nous donner un coup de main à la rédaction des prochaines dépêches **C++17**. Pour participer ou lire en avance les prochaines dépêches :
    
* se rendre sur l’espace de [rédaction _LinuxFr.org_](https://linuxfr.org/redaction) (recommandé pour la rédaction) ;
* directement sur le [dépôt Git *materials*](https://github.com/cpp-frug/materials/tree/gh-pages/Cxx17) du C++FRUG (Groupe des utilisateurs C++ francophones).

Droit d’auteur, remerciements et licences
=========================================
Le texte de cette dépêche est protégé par ~~le [droit d’auteur](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diffusion)~~ la [gauche d’auteur](https://fr.wikipedia.org/wiki/Gauche_d'auteur) et réutilisable sous licence [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr). Merci aux nombreux auteurs sur le [dépôt Git](https://github.com/cpp-frug/materials/graphs/contributors) et sur _LinuxFr.org_ : [olibre](https://github.com/olibre), [duckie](https://github.com/duckie), [rom1v](https://github.com/rom1v), [Oliver H](https://linuxfr.org/users/oliver_h), [cracky](https://linuxfr.org/users/cracky), [Lucas](https://linuxfr.org/users/george), [palm123](https://linuxfr.org/users/palm123), [Adrien Dorsaz](https://linuxfr.org/users/trim), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [Davy Defaud](https://linuxfr.org/users/davy78), [ZeroHeure](https://linuxfr.org/users/andrianarivony), [Benoît Sibaud](https://linuxfr.org/users/oumph), [tankey](https://linuxfr.org/users/tankey), [M5oul](https://linuxfr.org/users/m5oul) et [Anthony Jaguenaud](https://linuxfr.org/users/capello).

Merci aussi à [Klaim](https://github.com/klaim), [Édouard A](https://github.com/edouarda), [rewind](https://linuxfr.org/users/rewind), [David Demelier](https://linuxfr.org/users/markand), [gasche](https://linuxfr.org/users/bluestorm), [freem](https://linuxfr.org/users/freem) et [®om](https://linuxfr.org/users/rom1v) pour leurs commentaires pertinents.
    
    
Aussi un immense merci à mes collègues développeurs qui, à défaut de m’aider à la rédaction, ont illustré cette dépêche (et les dépêches suivantes) avec des dessins humoristiques sous licence libre : Ziyue, AKP, Florent B, et Jae-Zun. Merci aussi à Dominic Alves pour son [dessin C++](https://www.flickr.com/photos/dominicspics/785982209) sous licence libre. Merci à [Theppitak Karoonboonyanan](https://github.com/thep) pour maintenir la police de caractères [Purisa](https://github.com/tlwg/fonts-tlwg/commits/master/tlwg/Purisa.sfd).
    
* L’[évolution du langage C++](https://github.com/cpp-frug/materials/blob/gh-pages/images/Cpp-Evolution-Original.svg) est inspirée d’une œuvre dont les droits de réutilisation n’ont pas été identifiés. La réalisation sous licence [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.fr) est de Florent B (d’après une première ébauche de Jae-Zun) et utilise la police de caractères [Purisa](https://github.com/tlwg/fonts-tlwg/commits/master/tlwg/Purisa.sfd) maintenue par [Theppitak Karoonboonyanan](https://github.com/thep) sous licence [GPL v2](https://github.com/tlwg/fonts-tlwg/blob/master/GPL) ;
* Le logo C++ Francophonie [(disponible sur commons.wikimedia.org)](https://commons.wikimedia.org/wiki/File:Cpp-Francophonie.svg) est dans le [domaine public](https://fr.wikipedia.org/wiki/Domaine_public) (même si ce n’est théoriquement [pas possible en droit d’auteur français](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diffusion)) ;
* Le dessin du [C++ vissé sur de l’électronique](https://www.flickr.com/photos/dominicspics/785982209) est de Dominic Alves sous licence [CC BY-SA 2.0](https://creativecommons.org/licenses/by-sa/2.0/deed.fr) (2007).
    
Merci d’avance de l’aide apportée sur les prochaines dépêches C++17 en cours de préparation : Micka pour ses exemples *utiles* et AMB007 pour les bogues trouvés dans les codes C++ d’exemple.
