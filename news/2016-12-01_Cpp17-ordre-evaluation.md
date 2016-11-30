C++17 fixe l'ordre d'évaluation
===============================

Auteurs | [Oliver H](https://linuxfr.org/users/oliver_h), [Adrien Jeser](https://linuxfr.org/users/jeser), [Guillaume Dua](https://github.com/GuillaumeDua), [olibre](https://github.com/olibre), [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky) et [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid)
--------|------------------------------
License | [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)
URL     | https://linuxfr.org/news/cpp17-fixe-l-ordre-d-evaluation-des-expressions
Date    | 2016-12-01
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
    
Deux [*TS*](https://linuxfr.org/news/les-coulisses-du-standard-cpp#technical-specification-ts) ont été amendés par le comité de normalisation du C++ afin de fixer l’ordre d’évaluation des expressions :
    
* [**P0145**](https://wg21.link/p0145) définit les changements nécessaires au standard C++ ; 
* [**P0400**](https://wg21.link/p0400) reformule une phrase de cette précédente *TS* P0145.

Anecdote
========
    
Le livre mythique [*The C++ Programming Language*][CppPL] de l’inventeur du C++, [Bjarne Stroustrup][BS] contient une erreur subtile à la [page 1046][p1046] du paragraphe **36.3.6 STL-like Operations** (quatrième édition publiée en 2013). Sauras-tu la retrouver ? Voici l’extrait en question :
    
[CppPL]: https://fr.wikipedia.org/wiki/The_C%2B%2B_Programming_Language
[BS]:    https://fr.wikipedia.org/wiki/Bjarne_Stroustrup
[p1046]: http://www.ebooksbucket.com/the-c-programming-language-4th-edition-b198

>The `replace()` replaces one substring with another and adjusts the `string`’s size accordingly. For example:
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


Pas trouvé ? Pas d’inquiétude, aucun humain n’avait trouvé cette erreur. Bien après la publication de ce livre, cette erreur a été trouvée, non pas par une nouvelle forme d’[Intelligence Artificielle][IA], mais juste par un [outil d’analyse statique de code source][as] au nez et à la barbe des pointures C++ aguerries.
    
[IA]: https://fr.wikipedia.org/wiki/Intelligence_artificielle
[as]: https://fr.wikipedia.org/wiki/Analyse_statique_de_programmes

Explications
============
    
Pour des questions de performance, le standard C++ (avant C++17) indique que c’est le compilateur qui optimise l’ordre d’évaluation du chaînage et des paramètres de fonction. Le standard utilise le terme *unsequenced* (séquencement non défini). Le C et le C++ partagent ensemble cette règle.
    
Donc, l’expression `replace(find()).replace(find())` dans la fonction `f2()` peut être évaluée dans des ordres différents. En théorie, la variable `s` pourrait donc contenir différents résultats. Et c'est aussi le cas en pratique :

Compilateur              | Résultat contenu par la variable `s`
-------------------------|------------------------------------------
[GCC][g] et<br> [MSVC][v]| `I have heard it works evenonlyyou donieve in it`
[LLVM/Clang][c]          | `I have heard it works only if you believe in it`
    
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



Intuitivement, on s’attendrait à évaluer les arguments des fonctions comme `find("even")` juste avant d’appeler `replace(resultat,4,"only")`. Mais ce n’est pas le cas avant C++17, ces arguments peuvent être évalués dans différents ordres. Plus de détails sont donnés par [Shafik Yaghmour](http://stackoverflow.com/a/27158813/938111) (en Anglais).
    
Le tableau ci-dessous présente sur chacune des sept lignes, un ordre d’appel possible selon les standards C++ (avant C++17) et C (en supposant que ce soit une `struct string` avec des pointeurs de fonction).

1ᵉʳ appel     | 2ᵉ appel    | 3ᵉ appel    | 4ᵉ appel    | 5ᵉ appel
--------------|-------------|-------------|-------------|-------------
`find(" don't")`|`find("even")`|`replace(0,4,"")`|`replace(f,4,"only")`|`replace(f,6,"")`
`find("even")`|`find(" don't")`|`replace(0,4,"")`|`replace(f,4,"only")`|`replace(f,6,"")`
`find(" don't")`|`replace(0,4,"")`|`find("even")`|`replace(f,4,"only")`|`replace(f,6,"")`
`find("even")`|`replace(0,4,"")`|`find(" don't")`|`replace(f,4,"only")`|`replace(f,6,"")`
`replace(0,4,"")`|`find(" don't")`|`find("even")`|`replace(f,4,"only")`|`replace(f,6,"")`
`replace(0,4,"")`|`find("even")`|`find(" don't")`|`replace(f,4,"only")`|`replace(f,6,"")`
`replace(0,4,"")`|`find("even")`|`replace(f,4,"only")`|`find(" don't")`|`replace(f,6,"")`

C++17 n’autorise qu’une seule possibilité, la dernière du tableau, et correspond à celle de la fonction `f()` du livre :

```cpp
s.replace(0, 4, "");
s.replace(s.find("even"), 4, "only");
s.replace(s.find(" don't"), 6, "");
```



Autres exemples
===============
    
Par exemple, dans l’expression `f().g(h())` la fonction `f()` peut-être appelée avant ou après `h()`. Le standard C++ fait la différence entre *unspecified* (non-spécifié) et *unsequenced* (non-séquencé). Ce comportement est bien spécifié, donc jusqu’à C++14 c’est *unsequenced*. À partir de C++17, c’est `f()` avant `g()` *(sequenced before)*.

```cpp
// Avant C++17, f() peut être appelée avant ou après h()
f().g( h() ); 
// C++17 est plus intuitif : f() est toujours appelée avant h()
```



C’est aussi le cas de l’expression `std::cout << f() << g() << h();` dont les trois fonctions peuvent être appelées dans n’importe quel ordre.

```cpp
// Avant C++17, le compilateur décide l’ordre d’évaluation de f(), g() et h()
std::cout << f() << g() << h() << std::endl; 
// C++17 fixe l’ordre intuitif : d’abord f(), puis g() et enfin h()
```



Encore d’autres exemples que le C++ partage avec le C :

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
std::cout << i << ' ' << i++; // Affiche 0 0 ou 1 0 ?
// Clang  : 0 0
// GCC    : 1 0
// MSVC++ : 1 0
``` 
    
```cpp
int i = 0;
i = i++ + 1;    // unsequenced
std::cout << i; // Quelle valeur ?
// Clang   : 1  mais avertit : multiple unsequenced modifications to 'i'
// GCC-6.2 : 1  mais avertit : operation on 'i' may be undefined
```



Ci-dessus, pour toutes les versions du C++ et du C, l’opération est *unsequeced* et non pas *undefined* comme GCC-6.2 le laisse supposer.
 

```cpp
int i = 0;
i = ++i, i++, i++, ++i, ++i, ++i, i++;
std::cout << i; // Quelle valeur ?
// Piège, toujours 7 car c'est "sequenced before"
// GCC-6.2 avertit : operation on 'i' may be undefined
```



Notons que GCC-6.2 suppose encore que l’opération est *undefined* alors que dans ce dernier cas, l’opération est *sequenced before* quelque soit la version du C++ (et même du C).

Conséquence
===========
    
Donc, beaucoup de codes sont potentiellement truffés de ces pièges, ce qui est également le cas quand `std::future<T>` est utilisé. Tout le monde se fait avoir, débutants comme experts. Et le comité de normalisation du C++ a donc amendé sans trop discuter ce *TS* afin de fixer l’ordre d’évaluation dans certains cas.
    
Et c’est justement cet exemple du livre [*The C++ Programming Language*](https://fr.wikipedia.org/wiki/The_C%2B%2B_Programming_Language) qui illustre le paragraphe **5.2.2 Function call** (page 107) du [standard C++ (brouillon de juillet 2016)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4606.pdf).
    
Nouvelle règle
==============
    
L’évaluation est :
    
* De la gauche vers la droite pour les expressions suffixées. Ceci inclue les appels de fonction et la section des membres ;
* L’assignement de la droite vers la gauche (`a = b = c = d`) ;
* Les opérateurs de décalage *(shift operators)* de la gauche vers la droite.
    
Par contre, lorsque une surcharge d’opérateur est invoquée, la priorité arithmétique est utilisée.
    
Peut-être que le code généré sera moins performant, et que les standards C et C++ divergent un peu plus, mais au moins, le langage C++ devient un peu plus intuitif.
**¯\\_(ツ)_/¯**

[L1]: https://linuxfr.org/news/les-coulisses-du-standard-cpp
[L2]: https://linuxfr.org/news/cpp17-ameliore-les-lambdas-et-attribut-s
[LE]: https://linuxfr.org/news/faut-il-continuer-a-apprendre-le-cpp
    
[G1]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md
[G2]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md
[G3]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-12-01_Cpp17-ordre-evaluation.md
[GE]: https://github.com/cpp-frug/materials/blob/gh-pages/news/2017_n14_Faut-il-apprendre-le-Cpp.md

Appel à participation
=====================
    
La précédente dépêche a reçu [227 commentaires](https://linuxfr.org/news/c-17-genese-d-une-version-mineure#droit-dauteur-licences-remerciements), soit un volume dix fois supérieur à la dépêche elle-même. Tous ces commentaires cachent tout de même quelques joyeux [trolls](https://fr.wikipedia.org/wiki/Troll_%28Internet%29) velus !
    
Quand on pense à toute cette énergie dépensée et toutes ces heures consacrées à rédiger ces 227 commentaires ! Avec le recul nous aurions pu concentrer tout cet investissement dans une dépêche collaborative du style *« Aujourd’hui, est-il pertinent de choisir le C++ pour une nouvelle application ? »*.
    
[![Panneau Please Do Not Feed the Trolls](https://upload.wikimedia.org/wikipedia/commons/1/19/Trolls.jpg)](https://commons.wikimedia.org/wiki/File:Trolls.jpg) | [![Panneau Troll barré](https://upload.wikimedia.org/wikipedia/commons/e/ea/DoNotFeedTroll.svg)](https://commons.wikimedia.org/wiki/File:DoNotFeedTroll.svg)
----|----
    
Mais il n’est jamais trop tard ! Aussi nous proposons vous de rédiger la dépêche [*« Faut-il continuer à apprendre le C++ ? »*](https://linuxfr.org/news/faut-il-continuer-a-apprendre-le-c) Les nombreux commentaires de la dépêche précédente méritent d’y être copiés. Malheureusement, ceux-ci sont rarement sous licence compatible CC BY-SA 4.0. Ceci est donc un appel à tous leurs auteurs pour les copier dans cette dépêche afin de la nourrir. Ainsi, nous pourrons les structurer et proposer des réponses concises, claires et utiles à tous.
    
Merci et à vos claviers ! &emsp; **( ͡° ͜ʖ ͡°)**

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
