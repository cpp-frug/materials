TITRE DE LA DÉPÊCHE
===============================

Auteurs | [Oliver H](https://linuxfr.org/users/oliver_h), [Adrien Jeser](https://linuxfr.org/users/jeser), [Guillaume Dua](https://github.com/GuillaumeDua), [olibre](https://github.com/olibre), [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky) et [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid)
--------|------------------------------
License | [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)
URL     | https://linuxfr.org/news/...
Date    | YYYY-MM-DD
Tags    | c++17, c++ et cpp
Score   |   0

Le C++ est un langage bien présent et depuis longtemps dans les logiciels libres (environnements de bureau, outils bureautiques, navigateurs web…). 2017 approche à grands pas avec la promesse d’un tout nouveau **C++17**.
    
Pour finir l’année, voici le [calendrier de l’Avent][avent] du C++ avec des dépêches pédagogiques sur ce qui nous attend en 2017++. Après [deux][1] [dépêches][2] de mise-en-bouche, nous entrons enfin dans le vif du sujet avec deux [Spécifications Techniques][TS] concernant l’*ordre d’évaluation des expressions*. Allez, c’est parti ! &emsp; **ᕕ(ᐛ)ᕗ**
    
[avent]: https://fr.wikipedia.org/wiki/Calendrier_de_l'Avent
[1]: https://linuxfr.org/news/les-coulisses-du-standard-cpp
[2]: https://linuxfr.org/news/c-17-genese-d-une-version-mineure
[TS]: https://linuxfr.org/news/les-coulisses-du-standard-cpp#technical-specification-ts


[![Bjarne propose de changer le C++ pour corriger son livre qu'il tient dans ses mains](http://cpp-frug.github.io/materials/images/cpp17-bjarne-ordre-evaluation.png)](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#un-bogue-dans-le-livre-de-bjarne)
 

----

* [Dépêche préliminaire dans « Les coulisses du standard C++ » (CC BY-SA 4.0)](https://linuxfr.org/news/les-coulisses-du-standard-cpp)
* [Dépêche de mise bouche racontant la genèse du C++17 (CC BY-SA 4.0)](https://linuxfr.org/news/c-17-genese-d-une-version-mineure)
* [Contenu markdown de cette dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-12-01_Cpp17-ordre-evaluation.md)
* [Mars 2016 : Réunion pour dresser un premier contour du C++17 (Herb Sutter)](https://isocpp.org/blog/2016/03/trip-report-jax-sutter)
* [Mars 2016 : Détail de cette même réunion du comité de normalisation du C++ (Botondballo)](https://botondballo.wordpress.com/2016/03/21/trip-report-c-standards-meeting-in-jacksonville-february-2016/)
* [Juin 2016 : Réunion pour finaliser le périmètre C++17 (Herb Sutter)](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/)
* [Liste concise des nouveautés C++17 sur StackOverflow (Yakk, CC BY-SA 3.0)](http://stackoverflow.com/a/38060437/938111)
* [Liste partielle des nouveautés C++17 sur MeetingC++ (Jens Weller)](https://meetingcpp.com/index.php/br/items/final-features-of-c17.html)
* [Article Wikipédia C++17 (CC BY-SA 3.0)](https://en.wikipedia.org/wiki/C%2B%2B17)
* [Principaux apports des C++11/14/17 (Anthony Calandra, MIT)](https://github.com/AnthonyCalandra/modern-cpp-features/blob/master/README.md)

----

Série de dépêches C++
=====================
    
Cette dépêche fait partie de toute une série disponible également sur [le dépôt Git][dG] du [*Groupe des Utilisateurs C++ Francophone*][CppFRUG]. Alors que cet article restera figé sur le site *LinuxFr.org*, il continuera d’évoluer sur le dépôt Git. Merci de nous aider [à maintenir ce document à jour][md] avec vos questions/suggestions/corrections. L’idée est de partager ce contenu libre et de créer/enrichir des articles Wikipédia quand la licence [sera CC BY-SA 4.0](https://meta.wikimedia.org/wiki/Terms_of_use/Creative_Commons_4.0/fr). &emsp; **٩(•‿•)۶**
    
[dG]: https://github.com/cpp-frug/materials
[CppFRUG]: http://linuxfr.org/news/douzieme-rencontre-parisienne-c-mercredi-27-avril-2016#historique-des-rencontres-c-francophones
[md]: https://github.com/cpp-frug/materials/blob/gh-pages/news/README.md#pour-contribuer
    
Publication       | Dépêche                        
------------------|-------------------------------------------------
[20 août 2016][L1]|[Les coulisses du standard C++][G1]
[ 2 oct. 2016][L2]|[Genèse du C++17][G2]
1ᵉʳ déc. 2016     |[C++17 fixe l’ordre d’évaluation des expressions][G3]
à venir…          |… d’autres dépêches … 
[en 2017][LE]     |[Faut-il continuer à apprendre le C++ ?][GE]
    
Initialement, nous allions publier [une grosse dépêche super trop longue](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md). Puis, fin novembre, nous prenions conscience que les lecteurs apprécieraient plutôt une petite dépêche par jour, d’où l’idée de faire le calendrier de l’Avent du C++. &emsp; **(ღˇ◡ˇ)~♥**
    
[L1]: https://linuxfr.org/news/les-coulisses-du-standard-cpp
[L2]: https://linuxfr.org/news/cpp17-ameliore-les-lambdas-et-attribut-s
[LE]: https://linuxfr.org/news/faut-il-continuer-a-apprendre-le-cpp
    
[G1]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md
[G2]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md
[G3]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-12-01_Cpp17-ordre-evaluation.md
[GE]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2017_n14_Faut-il-apprendre-le-Cpp.md

Spécifications Techniques
=========================
    
* [**DRAFT**](https://wg21.link/DRAFT) Titre du brouillion ; 

TITRE
========

Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod
tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At
vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren,
no sea takimata sanctus est Lorem ipsum dolor sit amet.

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

La suite
========
    
Nous venons de découvrir un changement important au niveau du langage. La dépêche suivante nous dévoilera une autre nouveauté du C++17.
    
Chère lectrice, cher lecteur _LinuxFr.org_. Tu souhaites apporter ta pierre à cet édifice ? Rejoins‐nous dans l’[espace de rédaction collaborative sur _LinuxFr.org_](https://linuxfr.org/redaction) (un [compte](https://linuxfr.org/compte/inscription) est nécessaire pour y accéder).
    
À suivre...
