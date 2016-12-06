C++17 exprime la virgule flottante en hexadécimal
=================================================

Auteurs | [Oliver H](https://linuxfr.org/users/oliver_h), [Adrien Jeser](https://linuxfr.org/users/jeser), [Guillaume Dua](https://github.com/GuillaumeDua), [olibre](https://github.com/olibre), [Julien HENRY](https://github.com/henryju), [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [Xavier Claude](http://linuxfr.org/users/claudex), [ZeroHeure](http://linuxfr.org/users/andrianarivony), [Bruno Michel](http://linuxfr.org/users/nono) et [Nils Ratusznik](http://linuxfr.org/users/nils--2).
--------|------------------------------
License | [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr)
URL     | https://linuxfr.org/news/cpp17-exprime-la-virgule-flottante-en-hexadecimal-et-offre-des-cadeaux-aux-lecteurs-linuxfr-org
Date    | 2016-12-06
Tags    | c++17 et c++
Score   | 30

Chaque jour (ouvré) de décembre a droit à sa surprise. Après le [`if constexpr`](http://linuxfr.org/news/cpp17-branche-a-la-compilation-if-constexpr), aujourd’hui, le calendrier de l’Avent du C++ présente la spécification technique [P0245](http://wg21.link/p0245) concernant le littéral pour exprimer la virgule flottante en hexadécimal.

[![Les Nerdettes s'entraînent pour le concours des littéraux hexadécimaux sur LinuxFr.org](https://cpp-frug.github.io/materials/images/nerdettes_litteral_hexa.svg)](https://github.com/cpp-frug/materials/blob/gh-pages/images/nerdettes_litteral_hexa.svg)

----

* [1ᵉʳ décembre « C++17 fixe l’ordre d’évaluation des expressions »](http://linuxfr.org/news/cpp17-fixe-l-ordre-d-evaluation-des-expressions)
* [2 décembre « C++17 indique la disponibilité des entêtes »](http://linuxfr.org/news/cpp17-indique-la-disponibilite-des-entetes-header)
* [5 décembre « C++17 branche à la compilation »](http://linuxfr.org/news/cpp17-branche-a-la-compilation-if-constexpr)
* [Cette dépêche sur le dépôt Git du C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-12-06_cpp17-exprime-la-virgule-flottante-en-hexadecimal.md)

----

Spécification technique
=======================


La réunion de Jacksonville en février 2016 a amendé le *TS* [P0245](http://wg21.link/p0245) qui permet d’exprimer les [virgules flottantes (IEEE 754)](https://fr.wikipedia.org/wiki/Virgule_flottante#Norme_IEEE_754) en hexadécimal. Enfin, le C++ permet d’avoir une représentation exacte des [virgules flottantes](http://en.cppreference.com/w/cpp/language/floating_literal). Cette fonctionnalité était déjà présente depuis longtemps dans d’autres langages : C99, Java 5 (2004)…

Représentation exacte
=====================


La représentation hexadécimale a l’avantage d’être celle du registre (mémoire binaire). Attention à la notation décimale des virgules flottantes. Par exemple, `0.1f` ne vaut pas exactement `0.1` mais `0.10000000149…`. Un [exemple](http://coliru.stacked-crooked.com/a/7b70c88142f28581) :

```cpp
#include <stdint.h> // int64_t
#include <iostream> // std::cout
int main()
{
  float un_dixieme = 0.1f;
  float f_1e11 = un_dixieme * 1e12f; // Erreur d'arrondi
  int64_t i_1e11 = 0.1 * 1e12; // Pas d'erreur d'arrondi
  double  diff = f_1e11;
  diff -= i_1e11;  // soustraction f_1e12 - i_1e11
    
  std::cout.precision(99);
  std::cout << 
   "un_dixieme = "<< un_dixieme << "\n"
   "f_1e12     = "<< f_1e11     << "\n"
   "i_1e12     = "<< i_1e11     << "\n"
   "diff       = "<< diff       << '\n';
}
``` 

Qui donne le résultat :


    un_dixieme = 0.100000001490116119384765625
    f_1e12     = 99999997952
    i_1e12     = 100000000000
    diff       = -2048


Les hexadécimaux permettent d’écrire la représentation exacte des virgules flottantes en s’affranchissant de ces erreurs d’arrondis.

La pratique
===========
    
Passons à la pratique des fractions hexadécimales :

```cpp
float  v = 0xa.bp3f;
assert(v == 85.5f);
```


    
* `0xA.B = 0xA*16^0 + 0xB*16^-1`
* `0xA   = 10`
* `0x.B  = 11/16 = 0,6875`
* `0xA.B = 10,6875`
* `p3 = 2^3 = 8`
* `v = 10,6875*8 = 85,5`
* `'f' final = type 'float'`
    
```cpp
double w = 0xC0DE2017.1CAFEp-1;
assert(w == 1617891339.55602931976318359375);
```


    
* `0xC0DE2017 = 3235782679`
* `0x1CAFE    = 117502`
* `0xFFFFF    = 1048576`
* `p-1        = 2^-1 = 1/2`
* `w = (3235782679 + 117502/1048576) / 2`

Concours
========


Chère lectrice, cher lecteur *LinuxFr. org*, as-tu d’autres idées de jeux de mots avec cette notation hexadécimale ? Alors défoule-toi dans les commentaires ;-)


Les plus beaux jeux de mots seront récompensés avec des cadeaux de la part de *LinuxFr. org*. Alors tu as un peu de temps disponible aujourd'hui ? Fait comme les *Nerdettes* (les deux filles sur l’illustration), bogue du cerveau et propose ton code source de folie pour tenter de remporter un des lots.

Les modalités :


* Les jeux de mots peuvent utiliser le nom des variable, la forme des caractères et symboles, les opérateurs ;
* Il faut au moins un littéral hexadécimal à virgule flottante ;
* Le code source doit pouvoir être compilable par un compilateur C++17 ;
* Le code source doit être sous licence libre (licence de ton choix) ;
* Les meilleures réponses seront sélectionnées parmi celles qui auront le plus de points *« pertinents »* et le moins de points *« inutiles »* ;
* La liste des gagnants sera diffusée quelques jours plus tard dans une autre dépêche C++ ;
* Les vainqueurs auront un livre à choisir parmi ceux des éditions Eyrolles et ENI ;
* Réception des récompenses par courrier ~~électronique~~ postal.

Notation
========


Remarquons le `p` à la fin. Celui-ci représente l’exposant binaire et il est suivi par un entier décimal (et non pas hexadécimal). Cet exposant binaire est obligatoire pour plusieurs raisons :


* Évite l’ambiguïté du `f` final dans `0xA.Bf` (`float` ou le chiffre `F` hexadécimal ?) ;
* Évite l’ambiguïté du `E` dans `0xa.bE-12` (exposant `-12` ou `0xA.BE – 12` ?) ;
* Correspond à la norme [IEEE 754](https://fr.wikipedia.org/wiki/IEEE_754) (puissance de deux) ;
* 100 % compatible avec la notation C99 (et celle d’autres langages).

Tentons de représenter cette notation hexadécimale en [regex](https://fr.wikipedia.org/wiki/Expression_rationnelle) :


* `0[xX][0-9a-fA-F]+[.] ?[pP][+-] ?[0-9]+[fFlL] ?`
* `0[xX][0-9a-fA-F]*[.][0-9a-fA-F]+[pP][+-] ?[0-9]+[fFlL] ?`

Termes du standard
==================


Allez, soyons curieux, regardons comment le standard C++ spécifie cette notation avec un extrait du chapitre **§ 2.13.4 Floating literals** du [brouillon C++17](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4606.pdf) :

> *hexadecimal-floating-literal:*
>   &emsp; *hexadecimal-prefix hexadecimal-fractional-constant binary-exponent-part floating-suffix<sub>opt</sub>*
>   &emsp; *hexadecimal-prefix hexadecimal-digit-sequence binary-exponent-part floating-suffix<sub>opt</sub>*
> *hexadecimal-fractional-constant:*
>   &emsp; *hexadecimal-digit-sequence<sub>opt</sub> . hexadecimal-digit-sequence*
>   &emsp; *hexadecimal-digit-sequence .*
> *binary-exponent-part:*
>   &emsp; `p` *sign<sub>opt</sub> digit-sequence*
>   &emsp; `P` *sign<sub>opt</sub> digit-sequence*
> *sign:* one of
>   &emsp; `+` `-`
> *digit-sequence:*
>   &emsp; *digit*
>   &emsp; *digit-sequence ’<sub>opt</sub> digit*
> *floating-suffix:* one of
>   &emsp; `f` `l` `F` `L`


Et l’équivalent chez [cppreference.com](http://en.cppreference.com/w/cpp/language/floating_literal) :

> `0x | 0X hex-digit-sequence`
> `0x | 0X hex-digit-sequence .`
> `0x | 0X hex-digit-sequence(optional) . hex-digit-sequence`
>
> Hexadecimal digit-sequence representing a whole number without a radix separator. The exponent is never optional for hexadecimal floating-point literals: `0x1ffp10`, `0X0p-1`, `0x1.p0`, `0xf.p-1`, `0x0.123p-1`, `0xa.bp10l`
>
> The exponent syntax for hexadecimal floating-point literal has the form
> `p | P exponent-sign(optional) digit-sequence`
>
> exponent-sign, if present, is either + or -
>
> suffix, if present, is one of `f`, `F`, `l`, or `L`. The suffix determines the type of the floating-point literal:
>
>  * (no suffix) defines double
>  * `f F` defines float
>  * `l L` defines long double

Utilisation de `strtof()` et `std::hexfloat`
============================================


En attendant C++17, il est possible d’utiliser [`strtof()`](http://en.cppreference.com/w/cpp/string/byte/strtof) et [`std::hexfloat`](http://en.cppreference.com/w/cpp/io/manip/fixed) pour jouer avec les virgules flottantes hexadécimales :

```cpp
#include <iostream>
#include <cstdlib>
#include <cstdio>
int main (int argc, char *argv[])
{
  if (argc != 2) {
    std::cout <<"Usage: "<< argv[0] <<" 0xA.Bp-1  => Decode hexfloat" "\n";
    return 1;
  }
    
  std::cout <<"Decode floating point hexadecimal = "<< argv[1];
  long double l = std::strtold(argv[1],NULL); if(errno==ERANGE)std::cout<<"\nstrtold() erreur";
  double      d = std::strtod (argv[1],NULL); if(errno==ERANGE)std::cout<<"\nstrtod() erreur";
  float       f = std::strtof (argv[1],NULL); if(errno==ERANGE)std::cout<<"\nstrtod() erreur";
    
  std::cout <<"\n"  "long double = "<< std::defaultfloat << l <<'\t'<< std::hexfloat << l
            <<"\n"  "double      = "<< std::defaultfloat << d <<'\t'<< std::hexfloat << d
            <<"\n"  "float       = "<< std::defaultfloat << f <<'\t'<< std::hexfloat << f
            <<'\n';
}
```

Nous pouvons regretter qu’il faille utiliser des fonctions `strtof()` issues du C, qui imposent de verifier si `errno == ERANGE`. En théorie, `std::hexfloat` devrait fonctionner pour l’entrée (`istream`). Mais dans la pratique `std::hexfloat` semble ne fonctionner que pour la sortie (`ostream`). L’exemple suivant ne fonctionne toujours pas avec GCC-6.2, Clang-3.9 et MSVC++15 :

```cpp
double d;
std::istringstream iss("0xA.Bp-1");
iss >> std::hexfloat >> d;
std::cout << d;
``` 


Notons que c’est l’extraction qui ne s’effectue pas correctement. Le `std::istringstream` reste quand à lui dans un état correct, ainsi les erreurs sont vérifiables.

```cpp
std::cout
  << std::boolalpha
  << iss.fail() << '\n' // false
  << iss.bad()  << '\n' // false
  << iss.eof()  << '\n' // false
  << iss.str()  << '\n';// "0xA.Bp-1"
```

Réutilisation
=============


Le texte de cette dépêche est protégé par ~~le [droit d’auteur](https://fr.wikipedia.org/wiki/Droit_d%27auteur#Droit_d.E2.80.99auteur_traditionnel_vs._licences_de_libre_diﬀusion)~~ la [gauche d’auteur](https://fr.wikipedia.org/wiki/Gauche_d'auteur) et réutilisable sous licence [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr). Les images utilisées sont aussi sous licence libre (cliquer sur l’image pour plus de détails).


Donc n’hésitez pas à réutiliser ce contenu libre pour créer, par exemple, des supports de formation, des présentations _(Meetups)_, des publications sur d’autres blogs, des articles pour des magazines, et aussi un article C++17 sur Wikipédia dès que [Wikipédia passera de la licence CC-BY-SA-3.0 à la CC-BY-SA-4.0](https://meta.wikimedia.org/wiki/Terms_of_use/Creative_Commons_4.0) (le contenu de cette dépêche utilise la version la CC-BY-SA-4.0).



Les auteurs
===========


Par respect de la licence, merci de [créditer](https://fr.wiktionary.org/wiki/cr%C3%A9diter#Verbe) les auteurs :


* Les principaux auteurs sont [Adrien Jeser](https://linuxfr.org/users/jeser) et [Oliver H](https://linuxfr.org/users/oliver_h) ;
* Les nombreux autres contributeurs ayant contribué sur l’ancêtre de cette dépêche ou sur le [dépôt Git](https://github.com/cpp-frug/materials) sont [eggman](https://linuxfr.org/users/eggman), [Yves Bourguignon](https://linuxfr.org/users/biomin), [Storm](https://linuxfr.org/users/storm--2), [gorbal](https://linuxfr.org/users/gorbal), [palm123](https://linuxfr.org/users/palm123), [khivapia](https://linuxfr.org/users/khivapia), [BAud](https://linuxfr.org/users/baud), [Segfault](https://linuxfr.org/users/elly), [Benoît Sibaud](https://linuxfr.org/users/oumph), [Lucas](https://linuxfr.org/users/george), [cracky](https://linuxfr.org/users/cracky), [Martin Peres](https://linuxfr.org/users/mupuf), [RyDroid](https://linuxfr.org/users/rydroid), [olibre](https://github.com/olibre) et [Guss](https://github.com/GuillaumeDua).



Continuer à améliorer ce document
=================================


Malgré tout le soin apporté, il reste certainement des oublis, des ambiguïtés, des fôtes… Bien que cette dépêche restera figée sur le site *LinuxFr.org*, il est possible de continuer à l’enrichir sur le [dépôt Git](https://github.com/cpp-frug/materials/blob/gh-pages/news/README.md) du [**Groupe des Utilisateurs C++ Francophone**](http://linuxfr.org/news/douzieme-rencontre-parisienne-c-mercredi-27-avril-2016#historique-des-rencontres-c-francophones) (C++FRUG). C’est donc sur ce dépôt que se trouve les versions les plus à jour. &emsp; **(ღ˘⌣˘ღ)**

Alors que cet article restera figé sur le site *LinuxFr.org*, il continuera d’évoluer sur le dépôt Git. Merci de nous aider [à maintenir ce document à jour](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016-12-06_cpp17-exprime-la-virgule-flottante-en-hexadecimal.md) avec vos questions/suggestions/corrections. L’idée est de partager ce contenu libre et de créer/enrichir des articles Wikipédia quand la licence [sera CC BY-SA 4.0](https://meta.wikimedia.org/wiki/Terms_of_use/Creative_Commons_4.0/fr). &emsp; **٩(•‿•)۶**

Appel à contribution
====================


Nous nous efforçons de vous fournir une dépêche de qualité chaque jour ouvré. Et en plus, avec une illustration sympathique. Mais cela demande beaucoup de travail, et tenir les délais n’est pas toujours simple.


Merci de nous donner un coup de main, que ce soit sur la correction orthographique, le dessin, la lecture des spécifications techniques, la rédaction d’une nouvelle dépêche à intégrer au calendrier de l’Avent du C++. Tu peux aussi apporter ta contribution à la dépêche [*« Faut-il continuer à apprendre le C++ ? »*](https://linuxfr.org/news/faut-il-continuer-a-apprendre-le-c).


Rejoins-nous sur la [page du groupe de travail C++](https://linuxfr.org/redaction/news/groupe-de-travail-depeches-c-17) sur _LinuxFr.org_ (un [compte](https://linuxfr.org/compte/inscription) est nécessaire pour y accéder).


À suivre…
