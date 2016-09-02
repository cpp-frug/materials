
| Pour contribuer à ce document, merci de lire le [`README.md`](README.md)
|-------------------------------------------------------------------------


C++17 - Partie 1 sur 4 - Genèse d'une version mineure
=====================================================


Authors |Oliver H, olibre, duckie, Benoît Sibaud, cracky, Lucas, palm123, Adrien Dorsaz, Martin Peres et RyDroid
--------|------------------------------
License |[CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)


Pour la rentrée, la série de dépêches C++ continue. Cette seconde dépêche nous amène dans les réunions du comité de standardisation en vue de publier la prochaine version **C++17** et nous permettra de vérifier ce titre provocateur _(comment ça mineure ?)_ Cette dépêche peut intéresser tous les lecteurs LinuxFr.org. Les prochaines dépêches seront plus techniques.

![Deux collègues discutent : "C++ est enfin sorti", "Trop top", "Va falloir se palucher les 1700 pages du nouveau standard", "Gloups". Une note repositionnable sur le dessin indique : "Il y en a qui ne connaissent pas encore LinuxFr.org"](http://cpp-frug.github.io/materials/images/cpp-complexe-path.svg)

----

* [Journal de rewind  : C++17 est sur les rails](https://linuxfr.org/users/rewind/journaux/c-17-est-sur-les-rails)
* [Contenu Markdown de la première dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md)
* [Contenu Markdown de cette seconde dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md)
* [Contenu Markdown de la troisième dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md)
* [Contenu Markdown de la quatrième dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n4_Cpp17_Nouveautes-de-la-bibliotheque.md)
* [Contenu Markdown de la ciquième dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n5_Bilan-Cpp17-et-attentes-Cpp20.md)
* [Article Wikipédia C++14](https://fr.wikipedia.org/wiki/C%2B%2B14)
* [Article Wikipédia C++17](https://en.wikipedia.org/wiki/C%2B%2B17)
* [Mars 2016 - Rencontre du comité C++ - Intégration des fonctionnalités C++17 - par Herb Sutter](https://isocpp.org/blog/2016/03/trip-report-jax-sutter)
* [Mars 2016 - Bilan des premières fonctionnalités C++17 - par botondballo](https://botondballo.wordpress.com/2016/03/21/trip-report-c-standards-meeting-in-jacksonville-february-2016/)
* [Juin 2016 - Rencontre du comité C++ - Clôture de l'ajout de fonctionnalités C++17 - par Herb Sutter](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/)
* [Liste très complète des nouveautés C++17 sur StackOverflow](http://stackoverflow.com/a/38060437/938111)
* [Liste des nouveautés C++17 sur Meeting C++](https://meetingcpp.com/index.php/br/items/final-features-of-c17.html)
* [Site officiel du comité de standardisation du C++ - Page expliquant le fonctionnement du comité](https://isocpp.org/std/)
* [Dépôt Git officiel du standard C++ en cours de rédaction](https://github.com/cplusplus/draft/)
* [Dépêche "Codeurs, Traducteurs, CppReference a besoin de vous" par nazcafan (2012)](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous)
* [CppReference, wiki libre (CC-BY-SA-3.0 et GFDL) pour la documentation C et C++ ](http://fr.cppreference.com/w/Accueil)

----

C++1z ou C++17 ?
================


Historiquement, les versions C++ n'étaient pas publiées à date fixe. De plus, la version C++ qui devait suivre **C++03** avait été reportée à maintes reprises. Cette version a été nommée temporairement **C++0x**. Et, finalement, **C++0x** a été publié en 2011 ! (mais bon en [hexadécimal](https://fr.wikipedia.org/wiki/Syst%C3%A8me_hexad%C3%A9cimal) `0x = 11` est correct avec `x = B`)


Afin d’éviter tout nouveau glissement, le comité a alors décidé de publier un nouveau standard C++ tous les trois ans, en figeant les fonctionnalités l’année _n_ - 1. Avec un cycle d’une version majeure (**C++11**) suivie d’une version mineure (**C++14**).


Malgré des dates de publication figées, les appellations **C++1y** (pour **C++14**) et **C++1z** (pour **C++17**) perdurent. Par exemple, l’[option de compilation `-std=c++1z`](https://gcc.gnu.org/projects/cxx-status.html) ou l’[étiquette _c++1z_ sur _stackoverflow_](http://stackoverflow.com/tags/c%2b%2b1z/info).


Donc, **C++1z** est utilisé par les sceptiques pour désigner la version qui succédera à **C++14**. Et **C++17** est utilisé pour désigner la version qui sortira en **2017**.


Les membres du comité de normalisation utilisent le terme **C++17** (et non pas _C++1z_). Soyons confiants, **C++1z** verra bien le jour en 2017 (et non pas en 2018, ni après).


Des racines C++17 très profondes
================================
    
Les fonctionnalités pour **C++17** n'ont pas commencé à être créés au lendemain de la publication du **C++14**. Mais dès le début des années 2000, avec la réflexion sur des fonctionnalités qui n'avaient pas pu être intégrées à **C++11**.
    
Pour ne pas retarder davantage la sortie de **C++11**, les fonctionnalités majeures insuffisamment matures devaient être publiées pour **C++17**

Deux sommets pour délimiter le périmètre C++17
==============================================


D'après le cycle de publication [triannuel](http://www.universalis.fr/dictionnaire/triannuel/), c'est en 2016 (année *N*-1) que le comité de normalisation du C++ doit délimiter le périmètre fonctionnel du **C++17**. Ainsi, les membres du comité se sont réunis à deux reprises pour l'ajout des nouvelles fonctionnalités :
    
1. [Une semaine début mars](https://isocpp.org/blog/2016/03/trip-report-jax-sutter), à Jacksonville (Floride), pour adopter beaucoup de fonctionnalités, mais aussi pour rejeter plusieurs fonctionnalités majeures très attendues ;
2. [Une semaine fin juin](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/), à Oulu (Finlande), pour intégrer pas mal d'autres fonctionnalités et ainsi clore l'ajout des fonctionnalités.
    
La semaine se déroule sur six jours, du lundi au samedi. Pas de grasse matinée car les premières réunions débutent à 8:30. Ces réunions permettent de débattre et voter l'intégration de chacune des spécifications techniques (*Technical Specification)*. Plusieurs réunions se déroulent en parallèle, et les membres rejoignent les réunions selon leur centre d'intérêt. Après ces réunions *officielles*, les membres se retrouvent pour continuer à échanger ou pour améliorer les spécifications techniques.  
    
Mais à Oulu, un phénomène naturel a eu un impact direct sur la productivité : le [soleil se couche après minuit en juin](http://dateandtime.info/fr/citysunrisesunset.php?id=643492&month=6&year=2016) ! Si bien, que la plupart des membres ne se rendaient pas compte de l'heure et ont veillé bien plus tard que d'habitude. En plus du soleil qui *dort* seulement deux heures par nuit, le [décalage horaire _(jetlag)_](https://fr.wikipedia.org/wiki/D%C3%A9calage_horaire_(syndrome)) a achevé les non-européens qui ont eu besoin de plusieurs jours de repos pour s'en remettre !

![Deux chatons déçus du contenu de C++17 "Sniff.. On n'a pas les Concepts. Ni la Réflexion."](http://cpp-frug.github.io/materials/images/cpp-chatons-tristes_copyright-Ziyue-OliverH-2016_CC-BY-SA-3.jpg)

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

![Analogie entre les fonctionnalités promises pour C++17 et les promesses des candidats à la présidentielle de 2017 en France](http://cpp-frug.github.io/materials/images/cpp-president-2017.svg)

La suite...
===========    
    
La prochaine dépêche va nous permettre d'entrer enfin dans le vif du sujet **C++17**.
    
Merci de nous donner un coup de main à la rédaction des prochaines dépêches **C++17**. Pour participer ou lire en avance les prochaines dépêches :
    
* Se rendre sur l'espace de [rédaction LinuxFr.org](https://linuxfr.org/redaction) (recommandé pour la rédaction) ;
* Directement sur le [dépôt Git *materials*](https://github.com/cpp-frug/materials/tree/gh-pages/Cxx17) du C++FRUG (Groupe des utilisateurs C++ francophones).

Droit d’auteur, licences, remerciements
=======================================
    
Le texte de cette dépêche est protégé par ~~le [droit d’auteur](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diffusion)~~ la [gauche d’auteur](https://fr.wikipedia.org/wiki/Gauche_d'auteur) et réutilisable sous licence [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr). Merci aux nombreux auteurs sur le [dépôt Git](https://github.com/cpp-frug/materials/graphs/contributors) et sur _LinuxFr.org_ : [olibre](https://github.com/olibre), [duckie](https://github.com/duckie), [rom1v](https://github.com/rom1v), [Oliver H](https://linuxfr.org/users/oliver_h), [Benoît Sibaud](https://linuxfr.org/users/oumph), [cracky](https://linuxfr.org/users/cracky), [palm123](https://linuxfr.org/users/palm123), [Lucas](https://linuxfr.org/users/george), [Adrien Dorsaz](https://linuxfr.org/users/trim), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid) et [M5oul](https://linuxfr.org/users/m5oul).
    
Merci aussi à [Klaim](https://github.com/klaim), [Édouard A](https://github.com/edouarda), [rewind](https://linuxfr.org/users/rewind), et [gasche](https://linuxfr.org/users/bluestorm) pour leurs commentaires pertinents.
    
Aussi un immense merci à mes collègues développeurs qui, à défaut de m’aider à la rédaction, ont illustré cette dépêche (et les dépêches suivantes) avec des dessins humoristiques sous licence libre : Ziyue, AKP, Florent B et Jae-Zun :
    
* Les [deux collègues qui discutent sur la sortie du C++17](https://github.com/cpp-frug/materials/blob/gh-pages/images/Cpp-Complexe-Original.svg) sous licence [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.fr) est de AKP, et le texte de Oliver H. (2016). La [note repositionnable jaune](http://www.clker.com/clipart-top2.html) (post-it tout à droite du [comic strip](https://fr.wikipedia.org/wiki/Comic_strip)) sous licence [CC0](https://pixabay.com/fr/post-it-m%C3%A9mo-rappel-note-jaune-296384/) est de [Dave](http://www.clker.com/profile-50312.html) (2010) ;
* Le logo C++ Francophonie [(disponible sur commons.wikimedia.org)](https://commons.wikimedia.org/wiki/File:Cpp-Francophonie.svg) est dans le [domaine public](https://fr.wikipedia.org/wiki/Domaine_public) (même si ce n’est théoriquement [pas possible en droit d’auteur français](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diffusion)) ;
* Les [deux chatons déçus](https://github.com/cpp-frug/materials/blob/gh-pages/images/chatons-tristes-Cpp17_Copyright-Ziyue-OliverH-2016_CC-BY-SA-3.jpg) sous licence [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.fr) ont été dessinés au crayon par Ziyue et retouchés (avec GIMP) par Oliver H. (2016) ;
* L'analogie entre la [présidentielle 2017 et C++17](https://github.com/cpp-frug/materials/blob/gh-pages/images/Cpp-President-2017.svg) sous licence [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.fr) est de Oliver H. (2016) ;
* La police de caractères utilisée par deux des illustrations est la [Purisa](https://github.com/tlwg/fonts-tlwg/commits/master/tlwg/Purisa.sfd) maintenue par [Theppitak Karoonboonyanan](https://github.com/thep) sous licence [GPL-2](https://github.com/tlwg/fonts-tlwg/blob/master/GPL).
    
Merci d’avance de l’aide apportée sur les prochaines dépêches C++17 en cours de préparation : Micka pour ses exemples *utiles* et AMB007 pour les bogues trouvés dans les codes C++ d’exemple.
