Ce répertoire contient des images sous licence libre a propos du C++

C++ Complexe
------------

Auteur    | Contribution           | License
----------|------------------------|----------
Oliver H  | Ébauche                | CC-BY-SA-3.0
AKP       | Dessin à la main       | CC-BY-SA-3.0
Oliver H  | Numérisation et textes | CC-BY-SA-3.0
[Dave](http://www.clker.com/profile-50312.html) | [Note repositionnable jaune](http://www.clker.com/clipart-top2.html) (post-it) | [CC0 Public Domain](https://pixabay.com/fr/post-it-m%C3%A9mo-rappel-note-jaune-296384/)
[thep](https://github.com/thep) | police de caractères [Purisa](https://github.com/tlwg/fonts-tlwg/commits/master/tlwg/Purisa.sfd) | [GPL v2](https://github.com/tlwg/fonts-tlwg/blob/master/GPL)

Deux collègues discutent :

- C++ est enfin sorti
- Trop top
- Va falloir se palucher les 1700 pages du nouveau standard
- Gloups

Une note repositionnable (post-it) à la fin du dessin indique :
_"Il y en a qui ne connaissent pas encore LinuxFr.org"_
(LinuxFr.org pourrait être remplacé par cppfrug.org...)

La réalisation de cette image s'est basée principalement sur deux logiciels :

- potrace (vectorisation) ;
- inkscape.

Trois versions :

1. L'ébauche originelle au crayon ;
2. La version SVG avec les balises `<text>` et donc nécessite de la présence de la police Purisa ;
3. Celle avec les textes remplacés par des chemins `<path>` donc ne peuvant plus être édités.

![ébauche au crayon](http://cpp-frug.github.io/materials/images/cpp-complexe-draft.png)

![Version originale avec les balises <text>](http://cpp-frug.github.io/materials/images/cpp-complexe-original.svg)

![Version insensible à la présence des polices de caractères](http://cpp-frug.github.io/materials/images/cpp-complexe-path.svg)

Évolution du langage C++
------------------------

Auteur    | Contribution           | License
----------|------------------------|----------
Jae-Zun   | Prototypage            | CC-BY-SA-3.0
Florent B | Dessin à la main       | CC-BY-SA-3.0
Oliver H  | Numérisation et textes | CC-BY-SA-3.0
[thep](https://github.com/thep) | police de caractères [Purisa](https://github.com/tlwg/fonts-tlwg/commits/master/tlwg/Purisa.sfd) | [GPL v2](https://github.com/tlwg/fonts-tlwg/blob/master/GPL)

Analogie entre chaque version C++ et l'évolution de l'homme.
Le singe est associé à "C with Classes", puis "C++2.0" et "C++98"
pour des ancetres plus proches de homo sapiens qui se redressent de plus en plus.
Après homo sapiens (C++03), les descendaants se courbent de plus en plus (C++11, C++14)
pour se retrouver devant un ordinateur (C++17).
Au dessus de ce dernier homme, un texte "Cool  On va pouvoir coder".

La réalisation de cette image s'est basée principalement sur quatre logiciels :

- potrace (vectorisation) ;
- inkscape ;
- meld (pour comprendre ce que inkscape rajoutait dans le SVG) ;
- geany (pour supprimer les parties inutiles du contenu SVG).

Deux versions :

1. L'originale avec les balises `<text>` et donc dépent si la police Purisa est installée sur la machine ;
2. Celle avec les texts remplacé par des chemins `<path>` donc on ne peut plus éditer les textes.

![Version originale avec les balises <text>](http://cpp-frug.github.io/materials/images/cpp-evolution-original.svg)

![Version insensible à la présence des polices de caractères](http://cpp-frug.github.io/materials/images/cpp-evolution-path.svg)

C++17 Président
---------------

Auteur    | Contribution                                | License
----------|---------------------------------------------|----------
Oliver H  | Dessin, textes, numérisation, vectorisation | CC-BY-SA-3.0

Analogie entre les fonctionnalités promises pour C++17
et les promesses des candidats à la présidentielle de 2017 en France.

La réalisation de cette image s'est basée principalement sur deux logiciels :

- potrace (vectorisation) ;
- inkscape.

![C++17 président](http://cpp-frug.github.io/materials/images/cpp-president-2017.svg)

Bjarne impatient pour les Concepts
----------------------------------

Auteur    | Contribution           | License
----------|------------------------|----------
Oliver H  | Idée, dessin et textes | CC-BY-SA-3.0
[H. Harendal](https://plus.google.com/118235370450570590297) ([ADF](http://arkandis.tuxfamily.org/)) | Police [Gillius N°2](http://arkandis.tuxfamily.org/adffonts.html) inspirée de [Gill Sans](https://fr.wikipedia.org/wiki/Gill_Sans) | GPL v2 (avec exception)
[thep](https://github.com/thep) | Police de caractères [Purisa](https://github.com/tlwg/fonts-tlwg/commits/master/tlwg/Purisa.sfd) | [GPL v2](https://github.com/tlwg/fonts-tlwg/blob/master/GPL)

En 2003, Bjarne Stroustrup propose la première version des Concepts.
Ce "comic strip" imagine alors Bjarne demander
l'intégration des Concepts pour chacune des versions de C++ :
C++03, C++11, C++14, C++17... et à chaque fois les Concepts ne sont pas intégrés.
Sur la dernière vignette, les Concepts sont enfins intégrés (de très nombreuses décennies plus tard).
Sur cette dernière vignette est dessinée une pierre tombale avec une voix qui sort "Ce n'est pas trop tôt !".

La réalisation de cette image s'est basée sur quatre logiciels :

- inkscape (pour le dessin vectoriel initial) ;
- geany (pour les améliorations manuelles dans le XML générés par inkscape) ;
- gimp & potrace (tentative de conversion des textes en path au lieu d'utiliser inkscape).

Deux versions :

1. L'originale avec les balises `<text>` nécessite l'installation des polices de caractères Purisa et Gillius, ainsi que le support des attributs `letter-spacing` et `word-spacing` ([firefox ne le supporte pas](https://bugzilla.mozilla.org/show_bug.cgi?id=371787), du moins pas en 2016) ;
2. Celle avec les balises `<text>` remplacées par des chemins `<path>` (10 foix plus volumineuse, mais les `<path>` de mêmes caractères ne sont pas réutilisés). 

![C++ Concepts et Bjarne (version originale avec les balises text)](http://cpp-frug.github.io/materials/images/cpp-concepts-bjarne-original.svg)

![C++ Concepts et Bjarne (version insensible aux polices de caractères)](http://cpp-frug.github.io/materials/images/cpp-concepts-bjarne-path.svg)

Chantons déçus C++17
--------------------

Auteur    | Contribution                                   | License
----------|------------------------------------------------|----------
Guss      | Idée d'un chaton triste *Concept & Réflexion*  |
Ziyue     | Dessin à la main (crayon)                      | CC-BY-SA-3.0
Oliver H  | Numérisation, changements importants et textes | CC-BY-SA-3.0

Deux chatons déçus du contenu de C++17 discutent :

- Sniff.. On n'a pas les Concepts
- Ni la Réflexion

La réalisation de cette image s'est basée principalement sur deux logiciels :

- GIMP ;
- G'MIC (Vector painting) .

![Chatons tristes C++17](http://cpp-frug.github.io/materials/images/cpp-chatons-tristes_copyright-Ziyue-OliverH-2016_CC-BY-SA-3.jpg)

Ci-dessous le dessin original dessinée par Ziyue avant les améliorations réalisées avec GIMP et G'MIC. Cette image est au format WebP afin de limiter les fichiers binaires dans le dépôt Git. Chromium supporte depuis longtemps le format WebP, et Firefox devrait bientôt [le supporter](https://bugzilla.mozilla.org/show_bug.cgi?id=1294490) aussi.

![Dessin original de Ziyue](http://cpp-frug.github.io/materials/images/cpp-chatons-tristes_copyright-Ziyue-2016_CC-BY-SA-3_original.webp)


C++17 sauve une écolière
------------------------

Auteur    | Contribution                                   | License
----------|------------------------------------------------|----------
Ziyue     | Dessin à la main (crayon)                      | CC-BY-SA-3.0
Oliver H  | Numérisation, changements importants et textes | CC-BY-SA-3.0

Une maîtresse est atterrée que son élève ait rédigé sa punition en C++ avec une boucle qui écrit 100 fois _"Je ne dois pas jeter d'avion en papier en classe"_. 
A teacher is appalled her student has written her punishment in C++ using a loop writing 100 times _"I do not throw paper plane in class"_ in French.

La réalisation de cette image s'est basée principalement sur deux logiciels :

- GIMP ;
- G'MIC (Vector painting) .

Le fichier *source* au format XCF pèse 104 Mo (8466 × 4505 pixels) :  
https://commons.wikimedia.org/wiki/File:Cpp-ecole-primaire_copyright-Ziyue-OliverH-2016_CC-BY-SA-3.xcf

Six images générées = deux format (JPEG et WebP) et trois codes C++ écrits sur le tableau :

* en utilisant ``int i=0`` (C++98) ;
* en utilisant ``auto i{0}`` (C++17) ;
* en utilisant ``std::fill_n()`` (idée de [devnewton](https://linuxfr.org/nodes/109739/comments/1670072)).

----------------

1. ![JPEG "int i=0"      ](http://cpp-frug.github.io/materials/images/cpp-ecole-primaire_copyright-Ziyue-OliverH-2016_CC-BY-SA-3.jpg)
2. ![WebP "int i=0"      ](http://cpp-frug.github.io/materials/images/cpp-ecole-primaire_copyright-Ziyue-OliverH-2016_CC-BY-SA-3.webp)
3. ![JPEG "auto i{0}"    ](http://cpp-frug.github.io/materials/images/cpp-ecole-primaire_copyright-Ziyue-OliverH-2016_CC-BY-SA-3_auto.jpg)
4. ![WebP "auto i{0}"    ](http://cpp-frug.github.io/materials/images/cpp-ecole-primaire_copyright-Ziyue-OliverH-2016_CC-BY-SA-3_auto.webp)
5. ![JPEG "std::fill_n()"](http://cpp-frug.github.io/materials/images/cpp-ecole-primaire_copyright-Ziyue-OliverH-2016_CC-BY-SA-3_fill.jpg)
6. ![WebP "std::fill_n()"](http://cpp-frug.github.io/materials/images/cpp-ecole-primaire_copyright-Ziyue-OliverH-2016_CC-BY-SA-3_fill.webp)

Compilé c'est Testé
-------------------

Auteur    | Contribution           | License
----------|------------------------|----------
Oliver H  | Idée, dessin et textes | CC-BY-SA-3.0

L'adage *"Compilé c'est Testé, Linké c'est Livré"*
est possible pour le C++ en codant sa lib en `constexpr`
et ses tests unitaires en `static_assert()`.

La réalisation de cette image s'est basée sur quatre logiciels :

- inkscape (pour le dessin vectoriel initial) ;
- scour (pour améliorer le fichier XML produit par inkscape) ;
- geany (pour finaliser les améliorations manuellement) ;
- meld (pour contrôler les changements à chaque étape).

Deux versions :

1. Le brouillon original matricielle ;
2. La version vectorielle. 

![Brouillon original](http://cpp-frug.github.io/materials/images/compiler-c-est-tester_copyright-OliverH-2016_CC-BY-SA-3.0_original.png)

![Version vectorielle](http://cpp-frug.github.io/materials/images/compiler-c-est-tester_copyright-OliverH-2016_CC-BY-SA-3.0.svg)

