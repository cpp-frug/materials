C++17 branche à la compilation (`if constexpr`)
===============================================

Auteurs | [Oliver H](https://linuxfr.org/users/oliver_h), [Adrien Jeser](https://linuxfr.org/users/jeser), [Guillaume Dua](https://github.com/GuillaumeDua), [olibre](https://github.com/olibre), [Julien HENRY](https://github.com/henryju), [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [Xavier Claude](http://linuxfr.org/users/claudex), [ZeroHeure](http://linuxfr.org/users/andrianarivony), [Bruno Michel](http://linuxfr.org/users/nono) et [Nils Ratusznik](http://linuxfr.org/users/nils--2).
--------|------------------------------
License | [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)
URL     | http://linuxfr.org/news/cpp17-branche-a-la-compilation-if-constexpr
Date    | 2016-12-02
Tags    | c++17 et c++
Score   | 30


Chaque jour de décembre a droit à sa surprise. Après la [fixation de l’ordre d’évaluation des expressions](https://linuxfr.org/news/cpp-17-indique-la-disponibilite-des-entetes-header), aujourd’hui, le **calendrier de l’Avent du C++** présente la Spécification Technique [P0292](https://wg21.link/p0292) concernant les conditions à la compilation, grâce à `if constexpr`.


[![Logo C++FRUG représenté par un gros "C++" au centre du cercle de la Francophonie][logoCppFRUG]][logoCppFRUG_WP]
    
[logoCppFRUG]:    http://upload.wikimedia.org/wikipedia/commons/9/91/Cpp-Francophonie.svg
[logoCppFRUG_WP]: http://commons.wikimedia.org/wiki/File:Cpp-Francophonie.svg

----

[Dépêche préliminaire dans « Les coulisses du standard C++ » (CC BY-SA 4.0)](https://linuxfr.org/redirect/98710)
[Dépêche de mise bouche racontant la genèse du C++17 (CC BY-SA 4.0)](https://linuxfr.org/redirect/98711)
[Dépêche du 2 décembre "C++17 indique la disponibilité des entêtes (header)" (CC BY-SA 4.0)](https://linuxfr.org/news/cpp-17-indique-la-disponibilite-des-entetes-header)
[Article détaillé sur la fonctionnalité "if constexpr" par LoopPerfect (droit d'auteur non mentionné)](https://medium.com/@LoopPerfect/c-17-vs-c-14-if-constexpr-b518982bb1e2#.fsapor21v)

----

Plusieurs nommages
==================


Cette fonctionnalité a connu plusieurs nommages au fil des discussions entre les membres du comité de standardisation :
 


[![Chronologie du nommage de la fonctionnalité](https://cpp-frug.github.io/materials/schemas/if-constexpr/chrono.svg)](https://github.com/cpp-frug/materials/blob/gh-pages/schemas/if-constexpr/chrono.svg)


* **2011** : le nommage [original](https://wg21.link/n3322) était `static_if` et `static_else`.
* **2015** : l’avènement du mot-clé `constexpr` apporte une nouvelle terminologie qui se différencie à `static`. Le nommage devient [`constexpr_if`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0128r0.html) et `constexpr_else`.
* **Mars 2016** : lors de la première [réunion du comité de normalisation](https://linuxfr.org/news/cpp-17-genese-d-une-version-mineure#deux-sommets-pour-d%C3%A9limiter-le-p%C3%A9rim%C3%A8tre-c17), les deux mots ont été détachés pour donner `constexpr if`, et `constexpr_else` devient juste `else`.
* **Juin 2016** : à la seconde réunion, les deux mots sont inversés pour donner `if constexpr`.


Simplification du code générique
================================


Cette fonctionnalité est un outil puissant pour écrire du code générique compact. On combine plusieurs patrons (`template`). 


### Sans `if constexpr`


```cpp
void fonction()
{ std::cout << std::endl; }

template <class T>
void fonction (const T& t)
{ std::cout << t; }

template <class T, class... R>
void fonction (const T& t, const R&... r)
{
  fonction(t);    // Gère un argument
  fonction(r...); // Gère le reste
}
```




### Avec `if constexpr`


```cpp
template <class T, class... R>
void fonction (const T& t, const R&... r)
{
  std::cout << t;    // Gère un argument
  if constexpr (sizeof...(r))
    fonction(r...);  // Gère le reste
  else
    std::cout << std::endl;
}
```




Remplacement du SFINAE
======================


Brève explication sur le SFINAE
-------------------------------


D'après [Wikipédia en français](https://fr.wikipedia.org/wiki/C%2B%2B#SFINAE) :


> Le mécanisme décrit par l'abréviation SFINAE (Substitution Failure Is Not an Error) permet de surcharger un template par plusieurs classes (ou fonctions), même si certaines spécialisations, par exemple, ne peuvent pas être utilisées pour tous les paramètres de templates. Le compilateur, lors de la substitution, ignore alors les instanciations inapplicables, au lieu d'émettre une erreur de compilation.



C’est une technique de [métaprogrammation](https://fr.wikipedia.org/wiki/M%C3%A9taprogrammation) qui permet de sélectionner une fonction générique surchargée à la compilation. Plus spécifiquement, le SFINAE signifie que le compilateur ne considère pas comme une erreur un problème d’instanciation. Le compilateur va alors essayer de trouver une autre instanciation similaire possible.


Voir aussi l’[article sur Wikipédia en anglais](https://en.wikipedia.org/wiki/SFINAE) ou sur [cppreference.com](http://en.cppreference.com/w/cpp/language/sfinae). Un article en français mais non libre est également disponible sur [developpez.com](http://www.developpez.com/actu/94611/SFINAE-Interlude-moins-Cplusplus-avance-exemple-d-implementation/).


Chère lectrice, cher lecteur *LinuxFr.org*. Souhaites-tu une dépêche consacrée au SFINAE ? Alors exprime-toi dans les commentaires, et de nombreuses personnes vont certainement unir leur forces pour t’offrir un superbe article sous licence libre. Bon, si tu n’oses pas demander, personne n’aura l’impulsion pour se lancer…


Revenons au `if constexpr`
--------------------------


Dans certains cas, le `if constexpr` peut avantageusement remplacer la technique du SFINAE.


### Sans `if constexpr`
    
Voir sur [gcc.godbolt.org](https://godbolt.org/g/gCRNuq).


```cpp
template<class T>
auto f(T x) -> decltype(std::enable_if_t<   std::is_function_v<decltype(T::f)>,int>{})
{                                      // ^---true si T::f existe et que c'est une fonction
  return x.f();
}
    
template<class T>
auto f(T x) -> decltype(std::enable_if_t< ! std::is_function_v<decltype(T::f)>,int>{})
{                                      // ^---le contraire
  return 0;
}
```


### Trait
    
L’exemple précédent utilise [`enable_if`](http://en.cppreference.com/w/cpp/types/enable_if) et [`is_function`](http://en.cppreference.com/w/cpp/types/is_function) qui sont des [traits](https://fr.wikipedia.org/wiki/Trait_(programmation)) de la bibliothèque standard. Ce sont des classes `template` qui réalisent un petit traitement à la compilation nécessaire au SFINAE.
    
Par simplification, nous avons utilisé les suffixes `…_t` et `…_v` dans [`std::enable_if_t`](http://en.cppreference.com/w/cpp/types/enable_if) (C++14) et [`std::is_function_v`](http://en.cppreference.com/w/cpp/types/is_function) (C++17) qui correspondent respectivement au type d’aide `std::enable_if<…>::type` et à la variable d’aide `std::is_function<…>::value`.
    
La bibliothèque standard de GCC-7 implémente enfin la variable d’aide `…_v` (C++17). Par contre, cela ne semble pas encore être le cas pour Clang-3.8.


### Avec `if constexpr`
    
Voir sur [gcc.godbolt.org](https://godbolt.org/g/7ki6Ap).
    
```cpp
template<class T>
int f (T x)
{
  if constexpr( std::is_function_v<decltype(T::f)> )
    return x.f();
  else
    return 0;
}
```




Mixer `if constexpr` et `if` classique
======================================


Il est possible de mixer les deux syntaxes. La convention actuelle est de commencer par `if constexpr`. La inférence du type de retour peut aussi être utilisée. Un exemple vaut mieux qu’un long discours :


```cpp
template <bool B>
auto f (std::string const & s)
{
  if constexpr (B)
    return std::string("top");
  else if (s.size() > 42)
    return true;
  else
    return false;
}
```




Notons que la fonction `f()` n’a pas besoin d’être `constexpr` pour utiliser `if constexpr`, tout comme pour utiliser `static_assert()`. Même les lambdas peuvent utiliser cette fonctionnalité, que du bonheur. &emsp; **\o/**


Remplacement du `#if` ?
=======================
 


`if constexpr` peut, dans certains cas, remplacer le [`#if`](http://en.cppreference.com/w/cpp/preprocessor/conditional) du [préprocesseur](https://fr.wikipedia.org/wiki/Pr%C3 %A9processeur) mais ce n’est pas l’objectif. Après, selon l’usage qui en sera fait…
 


À ce propos, qui veut se lancer dans des expérimentations ? Merci de publier vos trouvailles dans les commentaires ;-)


Faut-il continuer à apprendre le C++ ?
======================================
 


[![Panneau Please Do Not Feed the Trolls](https://upload.wikimedia.org/wikipedia/commons/1/19/Trolls.jpg)](https://commons.wikimedia.org/wiki/File :Trolls.jpg)
 


Merci de continuer à nous aider à structurer et consolider les différentes idées sur l’espace de rédaction collaboratif de *LinuxFr.org* : [*« Faut-il continuer à apprendre le C++ ? »*](https://linuxfr.org/news/faut-il-continuer-a-apprendre-le-c)
 


[![Panneau Troll barré](https://upload.wikimedia.org/wikipedia/commons/e/ea/DoNotFeedTroll.svg)](https://commons.wikimedia.org/wiki/File :DoNotFeedTroll.svg)


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
    
Malgré tout le soin apporté, il reste certainement des oublis, des ambiguïtés, des fôtes… Bien que cette dépêche restera figée sur le site *LinuxFr.org*, il est possible de continuer à l'enrichir sur le [dépôt Git](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md) du [**Groupe des Utilisateurs C++ Francophone**](http://linuxfr.org/news/douzieme-rencontre-parisienne-c-mercredi-27-avril-2016#historique-des-rencontres-c-francophones) (C++FRUG). C’est donc sur ce dépôt que se trouvent les versions les plus à jour. &emsp; **(ღ˘⌣˘ღ)**



Alors que cet article restera figé sur le site *LinuxFr.org*, il continuera d’évoluer sur le dépôt Git. Merci de nous aider [à maintenir ce document à jour][md] avec vos questions/suggestions/corrections. L’idée est de partager ce contenu libre et de créer/enrichir des articles Wikipédia quand la licence [sera CC BY-SA 4.0](https://meta.wikimedia.org/wiki/Terms_of_use/Creative_Commons_4.0/fr). &emsp; **٩(•‿•)۶**



La suite
========
    
La dépêche suivante nous dévoilera une autre nouveauté du C++17.
    
Chère lectrice, cher lecteur _LinuxFr.org_. Tu souhaites apporter ta pierre à cet édifice ? Rejoins‐nous dans l’[espace de rédaction collaborative sur _LinuxFr.org_](https://linuxfr.org/redaction) (un [compte](https://linuxfr.org/compte/inscription) est nécessaire pour y accéder).
    
À suivre…
