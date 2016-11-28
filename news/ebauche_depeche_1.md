| Pour contribuer à ce document, merci de lire le [`README.md`](README.md)
|-------------------------------------------------------------------------

C++17 fixe l'ordre d'évaluation
===============================

Auteurs | [Oliver H](https://linuxfr.org/users/oliver_h), [Adrien Jeser](https://linuxfr.org/users/jeser), [Guillaume Dua "Guss"](https://github.com/GuillaumeDua), [olibre](https://github.com/olibre), [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid) et [Dua Guillaume "Guss"](https://github.com/GuillaumeDua)
--------|------------------------------
License | [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)
URL     | https://linuxfr.org/news/nouveautes-au-coeur-du-cpp17
Date    | 2016-07-22T00:53:12+02:00
Tags    | c++17, c++ et cpp
Score   |   0

L’ajout des fonctionnalités au **C++17** a été clôturé au premier semestre 2016. Depuis, nous nous efforçons à vous fournir des dépêches de qualité sur le sujet. Après deux dépêches de mise-en-bouche, cette troisième dépêche entre enfin dans le vif du sujet en décortiquant les deux [*TS*](Spécification Technique)](https://linuxfr.org/news/les-coulisses-du-standard-cpp#technical-specification-ts) concernant l'ordre d'évaluation des expressions. Allez c'est parti :-)

----

* [La précédente dépêche « C++17, Genèse d'une version mineure »](https://linuxfr.org/news/c-17-genese-d-une-version-mineure)
* [Contenu markdown de cette dépêche sur le dépôt C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md)
* [La prochaine dépêche « C++17 élargit la bliothèque standard »](https://linuxfr.org/news/cpp17-bibliotheque-standard-std)
* [Réunion du comité en mars 2016 racontée par Herb Sutter](https://isocpp.org/blog/2016/03/trip-report-jax-sutter)
* [Réunion du comité en juin 2016 racontée par Herb Sutter](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/)
* [Réunion du comité en mars 2016 détaillée par botondballo](https://botondballo.wordpress.com/2016/03/21/trip-report-c-standards-meeting-in-jacksonville-february-2016/)
* [Liste très complète des nouveautés C++17 (licence CC BY-SA 3.0) par Yakk et contributeurs](http://stackoverflow.com/a/38060437/938111)
* [Liste des nouveautés C++17 sur Meeting C++](https://meetingcpp.com/index.php/br/items/final-features)
* [Dépôts Git du comité de standardisation ISO C++](https://github.com/cplusplus))
* [Article Wikipédia C++17](https://en.wikipedia.org/wiki/C%2B%2B17)
* [Les principaux apports de C++11/14/17 (licence MIT) par Anthony Calandra et autres contributeurs ](https://github.com/AnthonyCalandra/modern-cpp-features/blob/master/README.md)

----

Série de dépêches C++
=====================
    
Cette dépêche fait partie de toute une série disponible également sur [le dépôt Git](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md) du [*Groupe des Utilisateurs C++ Francophone*](http://linuxfr.org/news/douzieme-rencontre-parisienne-c-mercredi-27-avril-2016#historique-des-rencontres-c-francophones) (C++FRUG). Alors que cet article restera figé sur le site *LinuxFr. org*, il continuera d’évoluer sur le dépôt Git. Merci de nous aider [à maintenir ce document à jour](https://github.com/cpp-frug/materials/blob/gh-pages/news/README.md#pour-contribuer) avec vos questions/suggestions/corrections.
        
Date              | Dépêche                        
------------------|-------------------------------------------------
[20 août 2016][L1]|[Les coulisses du standard][G1] de la naissance aux processus de normalisation.
[ 2 oct. 2016][L2]|[Genèse du C++17][G2] lors des deux réunions du comité de standardisation
1er déc. 2016     |[C++17 fixe l'ordre d'évaluation des expressions][G3]
[en 2017][LE]     |[Faut-il continuer à apprendre le C++ ?][GE] <br> Alternatives ? Intérêt du C++ dans le monde sans cesse mouvant de l’informatique ?
    
[L1]: https://linuxfr.org/news/les-coulisses-du-standard-cpp
[L2]: https://linuxfr.org/news/c-17-genese-d-une-version-mineure
[LE]: https://linuxfr.org/news/TODO
    
[G1]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md
[G2]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md
[G3]: https://github.com/cpp-frug/materials/blob/gh-pages/news/ebauche_depeche_1.md
[GE]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2017_n14_Faut-il-apprendre-le-Cpp.md

Spécifications Techniques
=========================

Deux [*TS*](https://linuxfr.org/news/les-coulisses-du-standard-cpp#technical-specification-ts) ont été amendés par le commité de normalisation du C++ afin de fixer l’ordre d’évaluation des expressions :
    
* [[P0145]](https://wg21.link/p0145) définit les changements nécessaires au standard C++ ; 
* [[P0400]](https://wg21.link/p0400) reformule une phrase de cette précédente *TS* P0145.

Anecdote
========


Le livre mythique [*The C++ Programming Language*](https://fr.wikipedia.org/wiki/The_C%2B%2B_Programming_Language) de l’inventeur du C++, [Bjarne Stroustrup](https://fr.wikipedia.org/wiki/Bjarne_Stroustrup) contient une erreur subtile à la [page 1046](http://www.ebooksbucket.com/the-c-programming-language-4th-edition-b198) du paragraphe *36.3.6 STL-like Operations* (quatrième édition publiée en 2013). Sauras-tu la retrouver ? Voici l’extrait en question :

>The `replace()` replaces  one  substring  with  another  and  adjusts  the
`string`’s  size  accordingly.   For example:
>
>```cpp
>void f()
>{
>  string s = "but I have heard it works even if you don't believe in it";
>  s.replace(0,4,"");                   // erase initial "but "
>  s.replace(s.find("even"),4,"only");
>  s.replace(s.find(" don't"),6,"");    // erase by replacing with ""
>  assert(s=="I have heard it works only if you believe in it");
>}
>```
>
> A `replace()` returns a reference to the object for which it was called.  This can be used for chaining operations:
>
>```cpp
>void f2()
>{
>  string s = "but I have heard it works even if you don't believe in it";
>  s.replace(0,4,"").replace(s.find("even"),4,"only").replace(s.find(" don't"),6,"");
>  assert(s=="I have heard it works only if you believe in it");
>}
>```
    


Pas trouvé ? Pas d’inquiétude, aucun humain n’avait trouvé cette erreur. Ce n’est que bien après la publication que cette erreur a été trouvée, pas par une nouvelle forme d’[Intelligence Artificielle](https://fr.wikipedia.org/wiki/Intelligence_artificielle), mais juste un [outil d’analyse statique de code source](https://fr.wikipedia.org/wiki/Analyse_statique_de_programmes) au nez et à la barbe des pointures C++ aguerries.


Explications
============


Pour des questions de performance, le standard C++ (avant C++17) indique que c’est le compilateur qui optimise l’ordre d’évaluation du chaînage et des paramètres de fonction. Le standard utilise le terme *unsequenced* (séquencement non défini). Le C et le C++ partagent ensemble cette règle.


Donc, l’expression `replace(find()). replace(find())` dans la fonction `f2()` peut être évaluée dans des ordres différents. En théorie, la variable `s` peut contenir différents résultats. Et en pratique aussi :


Compilateur                     | Résultat contenu par la variable `s`
--------------------------------|--------------
[GCC][g] et<br> [MSVC][v] | `I have heard it works evenonlyyou donieve in it`
[LLVM/Clang][c]                 | `I have heard it works only if you believe in it`
    
[g]: http://coliru.stacked-crooked.com/a/a6035cb6e64f038f
[c]: http://coliru.stacked-crooked.com/a/84408d788238bacd
[v]: http://rextester.com/VKFPX23982a

Détails
=======
    
Ci-dessous, la première ligne déclare et initialise un objet `std::string`. La seconde ligne cherche et remplace plusieurs caractères de cette `std::string` en utilisant le chaînage des fonctions [`replace`](http://en.cppreference.com/w/cpp/string/basic_string/replace).
    
```cpp
std::string s = "but I have heard it works even if you don't believe in it";
s.replace(0,4,"").replace(s.find("even"),4,"only").replace(s.find(" don't"),6,"");
``` 
    
Intuitivement, on s'attendrait à évaluer les arguments des fonctions comme `find("even")` juste avant d'appeler `replace(résultat,4,"only")`. Mais ce n’est pas le cas avant C++17, ces arguments peuvent être évalués dans différents ordres. Plus de détails sont donnés par [Shafik Yaghmour](http://stackoverflow.com/a/27158813/938111) (en Anglais).
    
Le tableau ci-dessous présente sur chacune des sept lignes, un ordre d'appel possible selon les standards C++ (avant C++17) et C (en supposant que ce soit une `struct string` avec des pointeurs de fonction).
    
1<sup>er</sup> appel|2<sup>e</sup> appel|3<sup>e</sup> appel|4<sup>e</sup> appel|5<sup>e</sup> appel
--------------|-------------|-------------|-------------|-------------
`find(" don't")`|`find("even")`|`replace(0,4,"")`|`replace(f,4,"only")`|`replace(f,6,"")`
`find("even")`|`find(" don't")`|`replace(0,4,"")`|`replace(f,4,"only")`|`replace(f,6,"")`
`find(" don't")`|`replace(0,4,"")`|`find("even")`|`replace(f,4,"only")`|`replace(f,6,"")`
`find("even")`|`replace(0,4,"")`|`find(" don't")`|`replace(f,4,"only")`|`replace(f,6,"")`
`replace(0,4,"")`|`find(" don't")`|`find("even")`|`replace(f,4,"only")`|`replace(f,6,"")`
`replace(0,4,"")`|`find("even")`, `find(" don't")`|`replace(f,4,"only")`|`replace(f,6,"")`
`replace(0,4,"")`|`find("even")`|`replace(f,4,"only")`|`find(" don't")`|`replace(f,6,"")`
    
C++17 n’autorise qu'une seule possibilité, la dernière, et correspond à :
    
```cpp
s.replace(0, 4, "");
auto p = s.find("even");
s.replace(p, 4, "only");
auto q = s.find(" don't");
s.replace(q, 6, "");
``` 
    
Pour info, cet exemple du livre [*The C++ Programming Language*](https://fr.wikipedia.org/wiki/The_C%2B%2B_Programming_Language) a justement été repris par le [standard C++ (brouillon de juillet 2016)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4606.pdf), au **§5.2.2 Function call** (page 107).

Autres exemples
===============
    
Par exemple dans l’expression `f().g(h())` les fonction `f()` peut-être appelée avant ou après `h()`. Le standard C++ fait la différence entre *unspecified* (non-spécifié) et *unsequenced* (non-séquencé). Ce comportement est bien spécifié, donc Avant C++17 c’est *unsequenced*. À partir de C++17, c’est `f()` avant `g()` *(sequenced before)*.
    
```cpp
// Avant C++17, f() peut être appelée avant ou après h()
f().g( h() ); 
// C++17 est plus intuitif : f() est toujours appelée avant h()
``` 
    
C’est aussi le cas de l’expression `std::cout << f() << g() << h()` qui peut appeler ces trois fonctions dans n’importe quel ordre.
    
```cpp
// Avant C++17, le compilateur décide l’ordre d’évaluation de f(), g() et h()
std::cout << f() << g() << h() << std::endl; 
// C++17 fixe l’ordre intuitif : d’abord f(), puis g() et enfin h()
``` 
    
Deux autres exemples que le C++ partage avec le langage C :
    
```cpp
std::map<int, int> m;
m[0] = m.size();
std::cout << m[0]; // Affiche 0 ou 1 ?
// Clang  : 0
// GCC    : 1
// MSVC++ : 0
``` 
    
```cpp
int i = 0;
std::cout << i << ' ' << i++; 
// Clang  : 0 0
// GCC    : 1 0
// MSVC++ : 1 0
``` 
    
Conséquence
===========
    
Donc, beaucoup de codes sont potentiellement truffés de ces pièges, ce qui est également le cas quand `std::future<T>` est utilisé. Tout le monde se fait avoir, débutants comme experts. Même les meilleurs experts C++ se font avoir avec ces règles pas toujours intuitives. Et le comité de normalisation C++ a donc décidé de fixer l’ordre d’évaluation avec ce *TS*.
        
Nouvelle règle
==============
    
L’évaluation est :
    
- De la gauche vers la droite pour les expressions suffixées. Ceci inclue les appels de fonction et la section des membres ;
- L’assignement de la droite vers la gauche (`a = b = c = d`) ;
- Les opérateurs de décalage (_shift operators_) de la gauche vers la droite.
    
Par contre, lorsque une surcharge d’opérateur est invoquée, la priorité arithmétique est utilisée. Peut-être que le code généré sera moins performant, mais le langage gagne grandement en simplicité.
    
Expression                                     | Résultat avant C++17 | Avec C++17
-----------------------------------------------|----------------------|-----------
`std::map<int,int> m;` <br> `m[0] = m.size();` | *unsequenced*        | `m[0] = ??`
`int i = 0, ++i++, ++i++, ++i++, ++i, i++;`    | `i = 8`              | `i = 8`
`int i = 0; i = i++ + 1;`                      | *unsequenced*        | *unsequenced*


Appel à participation
=====================
    
La précédente dépêche a reçu [227 commentaires](https://linuxfr.org/news/c-17-genese-d-une-version-mineure#droit-dauteur-licences-remerciements), soit un volume dix fois supérieur à la dépêche elle-même. Tous ces commentaires cachent tout de même quelques joyeux [trolls](https://fr.wikipedia.org/wiki/Troll_%28Internet%29) velus !

Quand on pense à toute cette énergie dépensée et toutes ces heures consacrées à rédiger ces 227 commentaires ! Avec le recul nous aurions pu concentrer tout cet investissement dans une dépêche collaborative du style *« Aujourd'hui, est-il pertinent de choisir le C++ pour une nouvelle application ? »*.

Mais il n'est jamais trop tard ! Aussi nous proposons vous de rédiger la dépêche *« Faut-il continuer à apprendre le C++ ? »* Les nombreux commentaires de la dépêche précédente méritent d'y être copiés. Malheureusement, ceux-ci sont rarement sous licence compatible CC-BY-SA-4.0. Ceci est donc un appel à tous leurs auteurs de les copier dans cette dépêche afin de la nourrir. Ainsi, nous pourrons les structurer et proposer des réponses concises, claires et utiles à tous.
    
Merci et à vos claviers ! ;-)

[![Panneau Please Do Not Feed the Trolls](https://upload.wikimedia.org/wikipedia/commons/1/19/Trolls.jpg)](https://commons.wikimedia.org/wiki/File:Trolls.jpg) | [![Panneau Troll barré](https://upload.wikimedia.org/wikipedia/commons/e/ea/DoNotFeedTroll.svg)](https://commons.wikimedia.org/wiki/File:DoNotFeedTroll.svg)
----|----

Réutilisation
=============
    
Le texte de cette dépêche est protégé par ~~le [droit d’auteur](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diﬀusion)~~ la [gauche d’auteur](https://fr.wikipedia.org/wiki/Gauche_d'auteur) et réutilisable sous licence [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr). Les images utilisées sont aussi sous licence libre (cliquer sur l'image pour plus de détails).
    
Donc n'hésitez pas à réutiliser ce contenu libre pour créer, par exemple, des supports de formation, des présentations _(Meetups)_, des publications sur d’autres blogs, des articles pour des magazines, et aussi un article C++17 sur Wikipédia dès que [Wikipédia passera de la licence CC-BY-SA-3.0 à la CC-BY-SA-4.0](https://meta.wikimedia.org/wiki/Terms_of_use/Creative_Commons_4.0) (le contenu de cette dépêche utilise la version la CC-BY-SA-4.0).
    
Les auteurs
-----------
    
Par respect de la licence, merci de [créditer](https://fr.wiktionary.org/wiki/cr%C3%A9diter#Verbe) les auteurs :
    
* Les principaux auteurs sont [Adrien Jeser](https://linuxfr.org/users/jeser) et [Oliver H](https://linuxfr.org/users/oliver_h) ;
* Les nombreux autres contributeurs dont l'ancêtre de cette dépêche ou via le [dépôt Git](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md) sont [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [olibre](https://github.com/olibre) et [Guillaume Dua "Guss"](https://github.com/GuillaumeDua).
    
Un immense merci à toutes ces personnes ayant rédigés bénévolement un article de très grande qualité. Merci aussi à Ziyue et Oliver H pour avoir dessiné spécialement pour cette dépêche l'[écolière sauvée par le C++](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#c17-sauve-une-%C3%A9coli%C3%A8re) et [« compilé c'est testé »](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#compil%C3%A9-cest-test%C3%A9) (tous deux sous licence [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.fr)). Merci aux auteurs des autres illustrations.
    
Continuer à corriger et à améliorer ce document
-----------------------------------------------
    
Malgré tout le soin apporté, il reste certainement des oublis, des ambiguïtés, des fôtes... Bien que cette dépêche restera figée sur le site *LinuxFr.org*, il est possible de continuer à l'enrichir sur le [dépôt Git](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md) du [**Groupe des Utilisateurs C++ Francophone**](http://linuxfr.org/news/douzieme-rencontre-parisienne-c-mercredi-27-avril-2016#historique-des-rencontres-c-francophones) (C++FRUG). C’est donc sur ce dépôt que se trouve les versions les plus à jour. Merci de nous aider à maintenir ce document à jour ;-)

La suite
========
    
Nous venons de découvrir un changement important au niveau du langage. La [dépêche suivante](https://linuxfr.org/news/TODO) nous dévoilera une autre fonctionnalité C++17.
    
Chère lectrice, cher lecteur _LinuxFr.org_. Tu souhaites apporter ta pierre à cet édifice ? Rejoins‐nous dans l’[espace de rédaction collaborative sur _LinuxFr.org_](https://linuxfr.org/redaction) (un [compte](https://linuxfr.org/compte/inscription) est nécessaire pour y accéder).
    
À suivre...
