
| Pour contribuer à ce document, merci de lire le [`README.md`](README.md)
|-------------------------------------------------------------------------

C++17 - Genèse d'une version mineure
====================================


Auteurs |[olibre](https://github.com/olibre), [duckie](https://github.com/duckie), [rom1v](https://github.com/rom1v), [Oliver H](https://linuxfr.org/users/oliver_h), [cracky](https://linuxfr.org/users/cracky), [Lucas](https://linuxfr.org/users/george), [palm123](https://linuxfr.org/users/palm123), [Adrien Dorsaz](https://linuxfr.org/users/trim), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [Davy Defaud](https://linuxfr.org/users/davy78), [ZeroHeure](https://linuxfr.org/users/andrianarivony), [Benoît Sibaud](https://linuxfr.org/users/oumph), [tankey](https://linuxfr.org/users/tankey), [M5oul](https://linuxfr.org/users/m5oul) et [Anthony Jaguenaud](https://linuxfr.org/users/capello)
--------|------------------------------
Licence | [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)
URL     | https://linuxfr.org/news/c-17-genese-d-une-version-mineure
Date    | 2016-06-27T00:11:42+02:00 (publication sur LinuxFr.org)
Tags    | c++ et c++17
Score   | 

La série de dépêches C++ continue. Cette seconde dépêche nous amène dans les réunions du comité de standardisation en vue de publier la prochaine version **C++17** et nous permettra de vérifier ce titre provocateur _(comment ça mineure ?)_ Cette dépêche peut intéresser tous les lecteurs LinuxFr.org, pas seulement les développeurs. Les prochaines dépêches seront plus techniques.

[![Deux collègues discutent : « C++ est enfin sorti », « Trop top », « Va falloir se palucher les 1700 pages du nouveau standard », « Gloups ». Une note repositionnable sur le dessin indique : « Il y en a qui ne connaissent pas encore LinuxFr.org »](http://cpp-frug.github.io/materials/images/cpp-complexe-path.svg)](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#c-complexe)

----

[Journal de rewind  : C++17 est sur les rails](https://linuxfr.org/users/rewind/journaux/c-17-est-sur-les-rails)
[Contenu Markdown de la première dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md)
[Contenu Markdown de cette seconde dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md)
[Contenu Markdown de la troisième dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md)
[Contenu Markdown de la quatrième dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n4_Cpp17_Nouveautes-de-la-bibliotheque.md)
[Contenu Markdown de la ciquième dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n5_Bilan-Cpp17-et-attentes-Cpp20.md)
[Article Wikipédia C++14](https://fr.wikipedia.org/wiki/C%2B%2B14)
[Article Wikipédia C++17](https://en.wikipedia.org/wiki/C%2B%2B17)
[Mars 2016 - Rencontre du comité C++ - Intégration des fonctionnalités C++17 - par Herb Sutter](https://isocpp.org/blog/2016/03/trip-report-jax-sutter)
[Mars 2016 - Bilan des premières fonctionnalités C++17 - par botondballo](https://botondballo.wordpress.com/2016/03/21/trip-report-c-standards-meeting-in-jacksonville-february-2016/)
[Juin 2016 - Rencontre du comité C++ - Clôture de l'ajout de fonctionnalités C++17 - par Herb Sutter](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/)
[Liste très complète des nouveautés C++17 sur StackOverflow](http://stackoverflow.com/a/38060437/938111)
[Liste des nouveautés C++17 sur Meeting C++](https://meetingcpp.com/index.php/br/items/final-features-of-c17.html)
[Site officiel du comité de standardisation du C++ - Page expliquant le fonctionnement du comité](https://isocpp.org/std/)
[Dépôt Git officiel du standard C++ en cours de rédaction](https://github.com/cplusplus/draft/)
[Dépêche "Codeurs, Traducteurs, CppReference a besoin de vous" par nazcafan (2012)](https://linuxfr.org/news/codeurs-traducteurs-cppreference-a-besoin-de-vous)
[CppReference, wiki libre (CC-BY-SA-3.0 et GFDL) pour la documentation C et C++ ](http://fr.cppreference.com/w/Accueil)

----

[LogoCppFRUG]:        http://upload.wikimedia.org/wikipedia/commons/9/91/Cpp-Francophonie.svg
[LogoCppFRUG_sur_WP]: http://commons.wikimedia.org/wiki/File:Cpp-Francophonie.svg

Dépêches C++
============


Cette dépêche est la deuxième d’une série de cinq dépêches sur le C++. La première dépêche [*Les coulisses du standard C++*](https://linuxfr.org/news/les-coulisses-du-standard-cpp) a été publié le mois dernier.

1. La dépêche précédente, [_Les coulisses du C++_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n1_Les-coulisses-du-standard.md), présente la naissance du langage, puis du standard, sa spécification non libre, [payant](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=64029), [ouvert](https://fr.wikipedia.org/wiki/Format_ouvert), délaissé au profit de son [brouillon](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf) _(draft)_, peu lu par les développeurs C++, évoluant lentement mais sûrement…
    
2. Cette dépêche, [_Genèse du C++17_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n2_Cpp17_Genese-d-une-version-mineure.md), raconte les dernières réunions du comité de normalisation et donne des éléments pour expliquer ce long processus de normalisation.
    
3. La troisième dépêche, [_Nouveautés C++17 du langage_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n3_Cpp17_Nouveautes-du-langage.md), présentera les changements du au niveau du langage : [déduction des arguments `template`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r2.html) `std::array a{1,2,3};`, [décomposition du retour de fonction](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r2.html) `auto [x, y] = f();` , [`namespace aa::bb{}`](http://en.cppreference.com/w/cpp/language/namespace) équivalent à `namespace aa{ namespace bb{}}`, [`if constexpr`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0128r1.html) sélectionne du code à la compilation, lambda `constexpr`, lambda capture `*this`, [`if(init;condition)`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r0.html) comme `for(init;cond;inc)`, [variables `inline`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r0.pdf)… Mais il faudra encore attendre pour l’intégration des [Concepts](http://fr.cppreference.com/w/cpp/concept), [Modules](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf), [Syntaxe d’appel uniforme](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax#C.2B.2B_proposal) et [Réflexion](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0194r1.html).
    
4. La quatrième dépêche, [_Nouveautés C++17 de la bibliothèque standard_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-08_n4_Cpp17_Nouveautes-de-la-bibliotheque.md), présentera les changements au niveau de la bibliothèque standard qui pourraient bien bousculer notre petite vie de développeur : [algorithmes parallélisés](http://en.cppreference.com/w/cpp/experimental/parallelism#Parallelized_versions_of_existing_algorithms), [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view), [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem), [`std::variant`](http://en.cppreference.com/w/cpp/utility/variant), [`std::any`](http://en.cppreference.com/w/cpp/utility/any), [`std::optional`](http://en.cppreference.com/w/cpp/utility/optional), les [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math)… Mais, les [intervalles (_ranges_)](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf), le [réseau (_networking_)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) seront intégrés pour une version ultérieure.
    
5. [_Bilan C++17 et attentes pour C++20_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n5_Bilan-Cpp17-et-attentes-Cpp20.md). Version mineure ou majeure ? D’un côté, les améliorations sont nombreuses et appréciables. Mais de l’autre, aucune fonctionnalité majeure n’est intégrée, exceptées celles qui sont déjà disponibles dans [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) (donc déjà supportées par un large panel d’anciens compilateurs). Conséquences sur le processus de normalisation ? Qu’attendre de C++20 ? Intérêt du C++ aujourd’hui ? Et les langages alternatifs ? Comment s’impliquer ?
    
6. … d’autres dépêches à venir. :-)

[![Logo C++FRUG représenté par un gros "C++" au centre du cercle de la Francophonie][logoCppFRUG]][logoCppFRUG_WP]
    
[logoCppFRUG]:    http://upload.wikimedia.org/wikipedia/commons/9/91/Cpp-Francophonie.svg
[logoCppFRUG_WP]: http://commons.wikimedia.org/wiki/File:Cpp-Francophonie.svg



Partage
=======
    
Chère lectrice, cher lecteur _LinuxFr.org_. Tu souhaites donner un coup de main pour les dépêches suivantes ? Rejoins‐nous dans l’[espace de rédaction collaborative sur _LinuxFr.org_](https://linuxfr.org/redaction). Un [compte](https://linuxfr.org/compte/inscription) est nécessaire pour y accéder.
    
Après publication, les dépêches sont figées sur _LinuxFr.org_. Alors, pour continuer à améliorer ce contenu libre (fôtes, oublis, franglais, maladresses…), n’hésite à pas à  aller sur le dépôt [Git C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/Cxx17). Tu y trouveras les versions de ces dépêches les plus à jour :
    
1. [_Les coulisses du standard C++_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md) ;
2. [_Genèse d’une version mineure_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md) ;
3. [_Nouveautés du langage_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md) ;
4. [_Nouveautés de la bibliothèque standard_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n4_Cpp17_Nouveautes-de-la-bibliotheque.md) ;
5. [_Bilan et attentes pour C++20_](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n5_Bilan-Cpp17-et-attentes-Cpp20.md).
    
Avec toutes nos contributions réunies, nous profiterons davantage de nos découvertes individuelles et nous offrirons un contenu CC BY-SA de qualité pour créer, par exemple, un article Wikipédia C++17 en français. :-)

Deux sommets pour délimiter le périmètre C++17
==============================================


Comme le prévoit le cycle de publication [triannuel](http://www.universalis.fr/dictionnaire/triannuel/), c’est en 2016 (année N-1) que le comité de normalisation du C++ vote le périmètre fonctionnel du **C++17**. Ainsi, les membres du comité se sont réunis à deux reprises pour intégrer de nouvelles fonctionnalités au C++ :


1. [Une semaine début mars](https://isocpp.org/blog/2016/03/trip-report-jax-sutter), à Jacksonville (Floride), pour adopter beaucoup de fonctionnalités, mais aussi pour rejeter plusieurs fonctionnalités majeures très attendues ;
2. [Une semaine fin juin](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/), à Oulu (Finlande), pour intégrer pas mal d’autres fonctionnalités et ainsi clore l’ajout des fonctionnalités.


La semaine se déroule sur six jours, du lundi au samedi. Pas de grasse matinée car les premières réunions débutent à 8 :30. Ces réunions permettent de débattre et voter l’intégration de chacune des spécifications techniques _(Technical Specification)_. Plusieurs réunions se déroulent en parallèle, et les membres rejoignent les réunions selon leur centre d’intérêt. Après ces réunions *officielles*, les membres se retrouvent pour continuer à échanger ou pour améliorer les spécifications techniques.


Mais à Oulu, un phénomène naturel a eu un impact direct sur la productivité : le [soleil se couche après minuit en juin](http://dateandtime.info/fr/citysunrisesunset.php?id=643492&month=6&year=2016) ! Si bien, que la plupart des membres ne se rendaient pas compte de l’heure et ont veillé bien plus tard que d’habitude. En plus du soleil qui *dort* seulement deux heures par nuit, le [décalage horaire _(jetlag)_](https://fr.wikipedia.org/wiki/Décalage_horaire_(syndrome)) a achevé les non-européens qui ont eu besoin de plusieurs jours de repos pour s’en remettre !

![Analogie entre les fonctionnalités promises pour C++17 et les promesses des candidats à la présidentielle de 2017 en France](http://cpp-frug.github.io/materials/images/cpp-president-2017.svg)

Des racines C++17 très profondes
================================


Les membres du comité de standardisation C++ n’avaient pas pu intégrer toutes les fonctionnalités qu’ils souhaitaient dans **C++11** car cela aurait retardé d’autant plus la publication de cette version (déjà que la publication était prévue avant 2010…). Les membres avaient donc prévu d’intégrer les fonctionnalités _mineures_ dans **C++14** et continuer à mûrir les fonctionnalités _majeures_ pour les intégrer dans **C++17**.


Par conséquent, **C++17** n’a pas commencé à être construit au lendemain de la publication de **C++14**, mais bien avant : certaines parties datent du début des années 2000 !

[![Deux chatons déçus du contenu de C++17 "Sniff.. On n'a pas les Concepts. Ni la Réflexion."](http://cpp-frug.github.io/materials/images/cpp-chatons-tristes_copyright-Ziyue-OliverH-2016_CC-BY-SA-3.jpg)](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#chantons-d%C3%A9%C3%A7us-c17)


Plus de 10 ans pour intégrer les fonctionnalités
================================================
    
Effectivement, certaines fonctionnalités sont dans le tuyau depuis plus de dix ans : 
    
* [Fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math) depuis [2003](http://open-std.org/JTC1/SC22/WG21/docs/papers/2003/n1422.html) ;
* [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem) depuis [2004](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1576.html).

Par contre, d’autres fonctionnalités _majeures_ sont toujours dans le tuyau :


* [Concepts](http://en.cppreference.com/w/cpp/language/constraints) depuis [2003](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2003/n1510.pdf) ;
* [Réflexion](https://fr.wikipedia.org/wiki/R%C3 %A9flexion_(informatique)) statique (à la compilation) depuis [2005](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1775.pdf) ;
* [Intervalles *(Ranges)*](http://www.boost.org/libs/range/index.html) depuis [2005](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1871.html) ;
* [Modules](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4592.pdf) (pour remplacer `#include`) depuis [2005](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1736.pdf) ;
* [Réseau](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) depuis [2005](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1838.pdf) (qui a pris le nom définitif [*Networking* fin 2005](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1925.pdf)) ;
* [Mémoire transactionnelle](http://en.cppreference.com/w/cpp/language/transactional_memory) dont son objectif de 2012 était d'[intégrer **C++17**](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3422.pdf) ;
* …


Comme quoi, le comité de standardisation prend son temps pour bien s’assurer que chaque fonctionnalité soit *parfaite* et cela peut prendre une dizaine d’années ! L’objectif étant de ne pas dégrader d’avantage la complexité inhérente au C++, avec comme contre partie d’avoir un langage de programmation qui évolue doucement…

[![En 2003, Bjarne Stroustrup propose la première version des Concepts. Ce "comic strip" imagine alors Bjarne demander l'intégration des Concepts pour chacune des versions de C++ : C++03, C++11, C++14, C++17... et à chaque fois les Concepts ne sont pas intégrés. Sur la dernière vignette, les Concepts sont enfin intégrés (de très nombreuses décennies plus tard). Sur cette dernière vignette est dessinée une pierre tombale avec une voix qui sort "Ce n'est pas trop tôt !".](http://cpp-frug.github.io/materials/images/cpp-concepts-bjarne-path.svg)](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#bjarne-impatient-pour-les-concepts)

Mais pourquoi autant de temps ?
===============================


Avant de répondre à cette question, voici un petit exercice. Il faut trouver la correction pour que le code C++ suivant compile :

```cpp
struct MaClasse
{
    template<class T>
    void fait() { }
};

template<class T>
void mafonction(T& t)
{
    t.fait<int>(); //error: expected primary-expression before 'int'
}

int main()
{
    MaClasse maclasse;
    mafonction(maclasse);
}
```


Quelques compilateurs en ligne pour tester tes idées :
    
* [gcc.godbolt.org](http://gcc.godbolt.org/#compilers:!((source:%27struct+MaClasse%0A{%0A++++template%3Cclass+T%3E%0A++++void+fait()+{+}%0A}%3B%0A%0Atemplate%3Cclass+T%3E%0Avoid+mafonction(T%26+t)%0A{%0A++++t.fait%3Cint%3E()%3B+//error:+expected+primary-expression+before+!%27int!%27%0A}%0A%0Aint+main()%0A{%0A++++MaClasse+maclasse%3B%0A++++mafonction(maclasse)%3B%0A}%27)),filterAsm:(commentOnly:!t,directives:!t,labels:!t),version:3) de [Matt Godbolt](https://github.com/mattgodbolt) propulsé par [GCC Explorer](https://github.com/mattgodbolt/gcc-explorer) sous licence [BSD-2-Clause](https://github.com/mattgodbolt/gcc-explorer/blob/master/LICENSE) ;
* [coliru.stacked-crooked.com](http://coliru.stacked-crooked.com/a/71c3371692723de1) (tu peux aussi remplacer `g++` par `clang++`) ;
* [cpp.sh](http://www.cpp.sh/22av) ;
* [codepad.org](http://codepad.org/XYy3ZoXw) ;
* [ideone.com](http://ideone.com/cDnejN) ;
* [rextester.com](http://rextester.com/XYSX22503) ;
* [tutorialspoint.com/compile_cpp11_online.php](https://goo.gl/9rqwoy) ;
* [webcompiler.cloudapp.net](http://webcompiler.cloudapp.net/) (permet de tester Visual C++ sans installer Windows) ;
* [repl.it](https://repl.it/DfuG/1).

Le message d'erreur du compilateur GCC-5.4 ou GCC-6.2 :
    
    $ g++ enigme.ccp                                                     
    enigme.ccp: In function ‘void mafonction(T&)’:
    enigme.ccp:10:12: error: expected primary-expression before ‘int’
         t.fait<int>(); //error: expected primary-expression before 'int'
                ^
    enigme.cc:10:12: error: expected ‘;’ before ‘int’
    

Allez une grosse image pour ne pas être tenté de lire la réponse tout de suite.

![logo "The C++ Programming Language"](https://isocpp.org/files/img/logo1.PNG)


Allez, deux indices : Primo, c’est du vieux **C++98** ; Secundo, voici le message d’erreur fourni par le compilateur Clang-3.8.
    
    $ clang++ enigme.cc                                                    
    enigme.cc:10:7: error: use 'template' keyword to treat 'fait' as a dependent
          template name
        t.fait<int>(); //error: expected primary-expression before 'int'
          ^
          template 
    
Encore une grosse image. On joue le jeu, on ne triche pas !

[![le texte "C++" sur un fond de type "écran du film Matrix" (Copyright webblaster48 2009 CC-BY-NC-ND-3.0)](http://sdtimes.com/wp-content/uploads/2015/06/0622.sdt-microsoft-facebook-c-.jpg)](http://webblaster48.deviantart.com/art/CODE-C-114384381)


Réponse
=======
    
Il manquait juste le mot clef `template` à un endroit un peu inattendu :
    
```cpp
struct MaClasse
{
    template<class T>
    void fait() { }
};

template<class T>
void mafonction(T& t)
{
    t.   template   fait<int>();
}

int main()
{
    MaClasse maclasse;
    mafonction(maclasse);
}
```

Avouons que c’est moche, non ?


Ceux qui ont décidé de cette syntaxe doivent s’en mordre les doigts.


**Mais pourquoi autant de temps ?** Je pense que ce type de choix du passé a traumatisé les membres du comité de normalisation du C++ : ne pas recommencer la même erreur, prenons le temps de bien mûrir les nouvelles fonctionnalités…

C++1z ou C++17 ?
================
    
Historiquement, les versions C++ n'étaient pas publiées à date fixe. De plus, la version C++ qui devait suivre **C++03** avait été reportée à maintes reprises. Cette version a été nommée temporairement **C++0x**. Et, finalement, **C++0x** a été publié en 2011 ! (mais bon en [hexadécimal](https://fr.wikipedia.org/wiki/Syst%C3%A8me_hexad%C3%A9cimal) `0x = 11` est correct avec `x = B`)
    
Afin d’éviter tout nouveau glissement, le comité a alors décidé de publier un nouveau standard C++ tous les trois ans, en figeant les fonctionnalités l’année _n_ - 1. Avec un cycle d’une version majeure (**C++11**) suivie d’une version mineure (**C++14**).
    
Malgré des dates de publication figées, les appellations **C++1y** (pour **C++14**) et **C++1z** (pour **C++17**) perdurent. Par exemple, l’[option de compilation `-std=c++1z`](https://gcc.gnu.org/projects/cxx-status.html) ou l’[étiquette _c++1z_ sur _stackoverflow_](http://stackoverflow.com/tags/c%2b%2b1z/info).
    
Donc, **C++1z** est utilisé par les sceptiques pour désigner la version qui succédera à **C++14**. Et **C++17** est utilisé pour désigner la version qui sortira en **2017**.
    
Les membres du comité de normalisation utilisent le terme **C++17** (et non pas _C++1z_). Soyons confiants, **C++1z** verra bien le jour en 2017 (et non pas en 2018, ni après).

La suite…
=========
    
La prochaine dépêche va nous permettre d’entrer enfin dans le vif du sujet **C++17**.
    
Merci de nous donner un coup de main à la rédaction des prochaines dépêches **C++17**. Pour participer ou lire en avance les prochaines dépêches :
    
* se rendre sur l’espace de [rédaction LinuxFr.org](https://linuxfr.org/redaction) ;
* ou sur le [dépôt Git *materials*](https://github.com/cpp-frug/materials/tree/gh-pages/Cxx17) du C++FRUG (Groupe des utilisateurs C++ francophones).

Droit d’auteur, licences, remerciements
=======================================
    
Le texte de cette dépêche est protégé par ~~le [droit d’auteur](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diffusion)~~ la [gauche d’auteur](https://fr.wikipedia.org/wiki/Gauche_d'auteur) et réutilisable sous licence [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr).
    
Merci aux nombreux auteurs sur le [dépôt Git](https://github.com/cpp-frug/materials/graphs/contributors) et sur _LinuxFr.org_ : [olibre](https://github.com/olibre), [duckie](https://github.com/duckie), [rom1v](https://github.com/rom1v), [Oliver H](https://linuxfr.org/users/oliver_h), [Benoît Sibaud](https://linuxfr.org/users/oumph), [cracky](https://linuxfr.org/users/cracky), [palm123](https://linuxfr.org/users/palm123), [Lucas](https://linuxfr.org/users/george), [Adrien Dorsaz](https://linuxfr.org/users/trim), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid) et [M5oul](https://linuxfr.org/users/m5oul). Cette dépêche fut commencée fin juin et contient plus de 1300 révisions !
    
Merci à [Klaim](https://github.com/klaim), [Édouard A](https://github.com/edouarda), [rewind](https://linuxfr.org/users/rewind), et [gasche](https://linuxfr.org/users/bluestorm) pour leurs commentaires pertinents.
    
Merci à mes collègues développeurs qui, à défaut de m’aider à la rédaction, ont illustré cette série de dépêches avec des dessins humoristiques sous licence libre :
    
* Les [deux collègues qui discutent sur la sortie du C++17](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#c-complexe) sous licence [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.fr) est de AKP, et le texte de Oliver H. (2016). La [note repositionnable jaune](http://www.clker.com/clipart-top2.html) (post-it tout à droite du [comic strip](https://fr.wikipedia.org/wiki/Comic_strip)) sous licence [CC0](https://pixabay.com/fr/post-it-mémo-rappel-note-jaune-296384/) est de [Dave](http://www.clker.com/profile-50312.html) (2010) ;
* Le logo C++ Francophonie [(disponible sur commons.wikimedia.org)](https://commons.wikimedia.org/wiki/File:Cpp-Francophonie.svg) est dans le [domaine public](https://fr.wikipedia.org/wiki/Domaine_public) (même si ce n’est théoriquement [pas possible en droit d’auteur de France](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diffusion)) ;
* L’analogie entre la [présidentielle 2017 et C++17](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#c17-pr%C3%A9sident) sous licence [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.fr) est de Oliver H. (2016) ;
* Les [deux chatons déçus](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#chantons-d%C3%A9%C3%A7us-c17) sous licence [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.fr) ont été dessinés au crayon par Ziyue et retouchés (avec GIMP) par Oliver H. (2016) ;
* La fonctionnalité des [*Concepts* repoussée de version en version](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#bjarne-impatient-pour-les-concepts) sous licence [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.fr) est de Oliver H. (2016).
    
Et merci à ceux qui permettent de réutiliser leur travail :
    
* L’image [*"C++ sur un fond de type Matrix"*](http://webblaster48.deviantart.com/art/CODE-C-114384381) a été réalisé par [Marek Dekys (anciennement webblaster48)](http://marek-dekys.deviantart.com/) et publié sous licence [CC BY-NC-ND 3.0](https://creativecommons.org/licenses/by-nc-nd/3.0/) en 2009 ;
* La police de caractères [Purisa](https://github.com/tlwg/fonts-tlwg/commits/master/tlwg/Purisa.sfd) utilisée par deux des illustrations est maintenue par [Theppitak Karoonboonyanan](https://github.com/thep) sous licence [GPL-2](https://github.com/tlwg/fonts-tlwg/blob/master/GPL) ;
* La police de caractères [Gillius N°2](http://arkandis.tuxfamily.org/adffonts.html) utilisée par la dernière illustration est de [H. Harendal](https://plus.google.com/118235370450570590297) [(Arkandis Digital Foundry)](http://arkandis.tuxfamily.org/) sous licence GPL v2 avec une exception permettant d’inclure la police de caractères dans un document sans que ce document doive lui aussi être sous licence compatible GPL.

    
Merci d’avance de l’aide apportée sur les prochaines dépêches C++17 en cours de préparation : Micka pour ses exemples *utiles* et AMB007 pour les bogues trouvés dans les codes C++ d’exemple.
