| Pour contribuer à ce document, merci de lire le [`README.md`](README.md)
|-------------------------------------------------------------------------

Les nouveautés au cœur du C++17
===============================

L'ajout des fonctionnalités au **C++17** a été clôturé au premier semestre 2016. Depuis, nous nous efforçons à vous fournir des dépêches de qualité sur le sujet. Après deux dépêches de mise-en-bouche, cette troisième dépêche entre enfin dans le vif du sujet en décortiquant les changements au niveau du langage C++. Quelques anecdotes parsèment cet article, des suggestions comme le **C++ without class** en echo au **C with classes**, ou quelques illustrations inédites comme celle du *"Compilé c'est testé, linké c'est livré"*. Alors faisons donc le tour des nouveautés :-)
    
![C++17 à l'école primaire](https://cpp-frug.github.io/materials/images/cpp-ecole-primaire_copyright-Ziyue-OliverH-2016_CC-BY-SA-3.jpg)

----

* [La précédente dépêche "C++17, Genèse d'une version mineure"](https://linuxfr.org/news/c-17-genese-d-une-version-mineure)
* [Contenu markdown de cette dépêche sur le dépôt C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md)
* [Journal "C++17 est sur les rails" par rewind a propos de la réunion du comité en mars 2016](https://linuxfr.org/users/rewind/journaux/c-17-est-sur-les-rails)
* [Réunion du comité en mars 2016 racontée par Herb Sutter](https://isocpp.org/blog/2016/03/trip-report-jax-sutter)
* [Réunion du comité en juin 2016 racontée par Herb Sutter](https://herbsutter.com/2016/06/30/trip-report-summer-iso-c-standards-meeting-oulu/)
* [Réunion du comité en mars 2016 détaillée par botondballo](https://botondballo.wordpress.com/2016/03/21/trip-report-c-standards-meeting-in-jacksonville-february-2016/)
* [Liste très complète des nouveautés C++17 sur StackOverflow.com](http://stackoverflow.com/a/38060437/938111)
* [Liste des nouveautés C++17 sur Meeting C++](https://meetingcpp.com/index.php/br/items/final-features)
* [Dépôts Git du comité de standardisation ISO C++](https://github.com/cplusplus))
* [Article Wikipédia C++17](https://en.wikipedia.org/wiki/C%2B%2B17)

----

![Illustration C++ de Dominic Alves sous license CC-BY-SA 2.0](https://c2.staticflickr.com/2/1116/785982209_b0da7b4380_o.jpg)


TODO
====
    
Reste à faire avant publication :
    
Qui ?     | Quoi ?                                        
----------|-----------------------------------------------
Oliver    | ~~Vérifier les TS qui manquent~~
Oliver    | ~~Réordonner les TS de cette dépêche~~
Oliver    | ~~Appliquer le nouveau sommaire~~
Oliver    | ~~Expliquer les nouveaux TS qui manquaient~~
???       | Ajouter des images (humoristiques) pour illustrer les sous-sections
**Oliver**| Préparer la dépêche suivante <br> **[Changements au niveau de la bibliothèque standard](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n4_Cpp17_Nouveautes-de-la-bibliotheque.md)** <br> Avec une liste exhaustive des TS et des `TODO`
Oliver    | Créer la dépêche suivante dans l'espace de rédaction *LinuxFr.org* <br> Ajouter les liens entre cette dépêche et la suivante <br> Proposer d'aider à la rédaction de la dépêche suivante
???       | Déplacer dans la dépêche suivante le TS Alias de iostream
Oliver    | Créer la dépêche **Bilan C++17** dans l'espace de rédaction *LinuxFr.org*
Oliver    | Créer la dépêche **Faut-il continuer à apprendre le C++ ?** dans l'espace de rédaction *LinuxFr.org* <br> Dans la section Troll, inviter à participer à cette dépêche <br> Prendre en compte les changements de eggman
Oliver    | Relire la sous-section *"Évaluation stricte des expressions"* <br> Proposer des ajouts/améliorations
Oliver    | Mettre à jour le chapitre **Concours** : Présenter les deux concours (héxadécimaux et code C++17 qui ne ressemble plus à C++98) + S'organiser pour les récompense
???       | Ajouter la section finale **Remerciments** pour remercier Adrien. Rappeler la licences et les auteurs. Des statistiques: la dépêche la plus longue de *LinuxFr.org* ...
???       | Passer un coup de Grammalect sur tout les paragraphes <br> pour insérer les espaces insécables (et autres formatages de texte)

Série de dépêches C++
=====================
    
Cette dépêche *LinuxFr.org* fait partie d'un série de dépêches disponibles également sur [le dépôt Git C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md).
    
Résumé de chacune des dépêches :

1. Les coulisses
----------------
    
La première dépêche, [*Les coulisses du standard C++*](https://linuxfr.org/news/les-coulisses-du-standard-cpp) est très longue mais passionnante. Elle présente la naissance du langage, le comité de normalisation, les brouillons du standard, la procédure de normalisation, le spécifications technique (*TS*), les correctifs (*DR*) publiés en parallèle... bref, des aspects souvent méconnus des développeurs C++.

2. Genèse du C++17
------------------
    
La seconde dépêche, [*C++17, Genèse d’une version mineure*](https://linuxfr.org/news/c-17-genese-d-une-version-mineure) dresse le périmètre fonctionnel du prochain C++ en rappelant les deux [réunions du comité de standardisation C++](http://www.open-std.org/jtc1/sc22/wg21/docs/meetings) de 2016 et la longue évolution de ce langage de programmation. 

3. Changements C++17 au niveau du langage
-----------------------------------------
    
Cette troisième dépêche [décrypte](https://fr.wiktionary.org/wiki/d%C3%A9crypter#figur.C3.A9) les spécifications techniques (*TS*) du cœur du C++17 : Déduction des arguments `template` du constructeur `std::array a{1,2,3}` ; Décomposition du retour de fonction `auto [x,y]=fonction()` ; `template<auto>` pour éviter la redondance dans `MaClasse<decltype(variable),variable>` ; `namespace` imbriqué `namespace aaa::bbb { ... }` ; `if constexpr` pour sélectionner du code à la compilation (peut remplacer `#if` dans certains cas) ; Lambda `constexpr` ; Lambda pouvant capturer `*this` ; `if(init;condition)` et `switch(init;condition)` comme pour `for(init;cond;inc)` ; Variables `inline`...

Par contre, des fonctionnalités majeures qui étaient très attendues sont toujours en cours d'élaboration ne sont pas encore suffisamment matures pour être publiées avec C++17 : [Concepts](http://fr.cppreference.com/w/cpp/concept) ; [Modules](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0142r0.pdf) qui propose des `import std.string;` en alternative des `#include <string>` ; [Syntaxe d'appel uniforme *(Uniform call syntax)*](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax#C.2B.2B_proposal) ; [Coroutines](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0057r4.pdf) ; [Mémoire Transactionnelle _(Transactional Memory)_](http://en.cppreference.com/w/cpp/language/transactional_memory) ; [Réflexion _(Static Reflection)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0194r1.html).

4. Changements C++17 au niveau de la bibliothèque standard
----------------------------------------------------------
    
Cette quatrième dépêche traitera encore de nombreux *TS* dont les [algorithmes parallélisés](http://en.cppreference.com/w/cpp/experimental/parallelism#Parallelized_versions_of_existing_algorithms), le [`std::string_view`](http://en.cppreference.com/w/cpp/string/basic_string_view) (pour utiliser les méthodes de std::string sur des const char* sans faire de ré-allocation inutile) et les transfuges de chez [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) comme [`std::filesystem`](http://en.cppreference.com/w/cpp/filesystem), [`std::variant`](http://en.cppreference.com/w/cpp/utility/variant), [`std::any`](http://en.cppreference.com/w/cpp/utility/any), [`std::optional`](http://en.cppreference.com/w/cpp/utility/optional) et [`boost::math`](http://www.boost.org/libs/math) (les [fonctions spéciales mathématiques](http://en.cppreference.com/w/cpp/numeric/special_math)).
    
Tout comme la dépêche précédente, les fonctionnalités majeures très attendues, comme les [intervalles *(Ranges)*](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf) ou le [réseau _(Networking)_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4588.pdf) seront publiées pour une autre version du C++...

5. Bilan C++17 et attentes pour C++20
-------------------------------------
    
Alors, version mineure ou majeure ? Les améliorations sont appréciables, mais aucune fonctionnalité majeure au niveau du langage. Et côté bibliothèque standard, la plupart des fonctionnalités majeures sont déjà disponibles dans [Boost](https://fr.wikipedia.org/wiki/Boost_(biblioth%C3%A8ques)) et supportent donc aussi d'anciennes versions des compilateurs (ce qui n'est pas le cas de C++17). Et C++20 ?


6. Faut-il apprendre le C++ ?
-----------------------------
    
Cette [sixième dépêche](https://github.com/cpp-frug/materials/blob/gh-pages/news/2017_n1_Faut-il-continuer-d-apprendre-le-Cpp.md) compare le C++ aux alternatives et permet de mieux situer l'intérêt du C++ dans le monde sans cesse mouvant de l'informatique.

Partager
========
    
Chère lectrice, cher lecteur _LinuxFr.org_. Tu souhaites donner un coup de main pour les dépêches suivantes ? Rejoins‐nous dans l’[espace de rédaction collaborative sur _LinuxFr.org_](https://linuxfr.org/redaction) (un [compte](https://linuxfr.org/compte/inscription) est nécessaire pour y accéder).
    
Quelques lecteurs *LinuxFr.org* ont beaucoup contribué à cette dépêche pour détailler au mieux les nouvelles fonctionnalités. Malgré les manques, ambiguïtés et fôtes, cette dépêche restera figée sur le site *LinuxFr.org*.
    
Par contre, tu peux continuer à enrichir ce contenu sur [le dépôt Git C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news). C’est donc sur ce dépôt [Git C++FRUG](https://github.com/cpp-frug/materials/blob/gh-pages/news) que tu trouveras les versions les plus à jour :
    
1. [Les coulisses du standard C++](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n1_Coulisses-du-standard.md) ;
2. [Genèse d’une version mineure](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n2_Cpp17_Genese-d-une-version-mineure.md) ;
3. [Nouveautés au cœur du langage](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n3_Cpp17_Nouveautes-du-langage.md) ;
4. [Nouveautés de la bibliothèque standard](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n4_Cpp17_Nouveautes-de-la-bibliotheque.md) ;
5. [Bilan et attentes pour C++20](https://github.com/cpp-frug/materials/blob/gh-pages/news/2016_n5_Bilan-Cpp17-et-attentes-Cpp20.md) ;
6. [Faut-il apprendre le C++ ?](https://github.com/cpp-frug/materials/blob/gh-pages/news/2017_n1_Faut-il-continuer-d-apprendre-le-Cpp.md)
    
Avec toutes nos contributions réunies, nous proﬁterons davantage de nos découvertes individuelles et nous offrirons un contenu CC BY-SA de qualité pour créer, par exemple, des supports de formation _(Meetups)_, des publications sur d’autres blogs, des articles Wikipédia dès que [Wikipédia passera de la licence CC-BY-SA-3.0 à la CC-BY-SA-4.0](https://meta.wikimedia.org/wiki/Terms_of_use/Creative_Commons_4.0) (le contenu de cette dépêche utilise la version la CC-BY-SA-4.0).

Améliorations notables
======================


[[P0061]](https://wg21.link/p0061) `__has_include`
--------------------------------------------------
    
La macro [**`__has_include(<filesystem>)`**](http://en.cppreference.com/w/cpp/preprocessor/include) vérifie si l'en-tête `<filesystem>` est disponible pour inclusion ;
    
```cpp
#if    __has_include(<filesystem>)
#  include           <filesystem>
#elif  __has_include(<experimental/filesystem>)
#  include           <experimental/filesystem>
#elif __has_include(<boost/filesystem.hpp>)
#  include          <boost/filesystem.hpp>
#else
#  error Ne trouve aucune en-tête filesystem
#endif
``` 
    
Allons plus loin avec un autre exemple :
     
```cpp
#if __has_include(<windows.h>)
#  include <windows.h>
   LONGLONG ticks1nano = []() {
     LARGE_INTEGER freq;
     QueryPerformanceFrequency(&freq);
     return freq.QuadPart / 1000'000;
   }();
   LONGLONG nanosecondes() {
     LARGE_INTEGER time;
     QueryPerformanceCounter(&time);
     return time.QuadPart/ticks1nano;
   }
#elif __has_include(<time.h>)
#  include <time.h>
   auto nanosecondes() {
      struct timespec ts;
      clock_gettime(CLOCK_MONOTONIC,&ts);
      return 1000'000'000 * ts.tv_sec + ts.tv_nsec;
   }
#else
#  error Ne trouve ni <windows.h> ni <time.h>
#endif
```



[[P0135]](http://wg21.link/p0135) Court-circuitage du constructeur par copie *(Guaranteed copy elision)*
------------------------------------------------------
    
C++17 garantit le [court-circuitage du constructeur par copie](https://en.wikipedia.org/wiki/Copy_elision). Mais pas dans tous les cas : ce *TS* distingue le cas général *"elision"* du cas spécifique *"genuine elision"*.
    
```cpp
int n = 0; // compte le nombre d'appel au constructeur par copie

struct A
{
  explicit A(int) {}
  A(const A&) { ++n; }
};

int main()
{
  A a = A( A( A( A(42) ) ) );
  return n; // toujours 0 avec C++17
}           // pas de garantie avant C++17
```

[[P0145]](https://wg21.link/p0145) Fixer l'ordre d'évaluation des expressions
-----------------------------------------------------------------------------
    
Héritées du C, les expressions sont indéfiniment séquencées. Le choix de l'ordre d'évalution est délégué au compilateur, qui peut optimiser le code. Par contre, cette liberté amène à des comportements incertains, notamment lorsqu’on utilise le même objet. Cette absence de spécification est dommageable avec les pratiques courantes, comme le chainage (`std::future<T>`, `std::io_base`, …).
    
```cpp
    
std::map<int, int> m;
m[0] = m.size();
int i = 0;
    
// Doit afficher 0 ou 1 ?
// Avec Clang : 0
// Avec G++ : 1
std::cout << m[0] << std::endl; 
    
// Avec Clang : 00
// Avec G++ : 10
std::cout << i << i++; 
    
``` 
    
### Exemple commenté
    
Ce problème n'est pas juste l'apanage des experts. C'est un piège qui concerne aussi les débutants. Un exemple commenté permettra à tous de mieux comprendre.
    
```cpp
    
    std::string s = "but I have heard it works even if you don't believe in it";
    s.replace(0, 4, "")
//  ^ ^       ^  ^  ^
//  A B       |  |  |
//            1  2  3
    
        .replace(s.find("even"), 4, "only")
//       ^       ^               ^  ^
//       C       |               |  |
//               4               5  6
//              
        .replace(s.find(" don't"), 6, "");
//      ^        ^                 ^  ^
//      D        |                 |  |
//               7                 8  9
     assert(s == "I have heard it works only if you believe in it");
    
    
``` 
    
Ce code provient du brouillon. Il remplace plusieurs caractères d'un objet std::string. Pourtant ce programme semble légitime, mais produira un résultat non désiré, selon le compilateur.
    
La première ligne est en somme tout classique. Un objet std::string est déclaré et initialisé. 
L'instruction suivante utilise le chainage. [`replace`](http://en.cppreference.com/w/cpp/string/basic_string/replace) est une fonction membre de l'objet `s`. Chaque appel et leurs arguments sont souvent perçu comme un groupe d'expression (par exemple : `replace(0, 4, "")`). Dans l'exemple, ils sont annotés alphabétiquement. À première vue, chacun est dépendant du précédant. Donc leurs évaluations devraient être séquencés de la gauche vers la droite. En réalité avant cette norme, toutes les expressions sont indéfiniment séquencées.
    
### Les nouvelles règles
    
**L'ordre d'évaluation est :**
    
- De la gauche vers la droite pour les expressions suffixés. Ceci inclue les appelles de fonction et la section des membres.
- L'assignement de la droite vers la gauche.
- Les opérateurs de décalage (_shift operators_) de la gauche vers la droite.
    
Par contre, lorsque une surcharge d'opérateur est invoquée, la priorité arithmétique est utilisée.

[[P0400]](https://wg21.link/p0400) Corrige la précédente TS P0145
-----------------------------------------------------------------
    
Une toute petite reformulation d'une phrase de la *TS* concernant l'ordre d'évaluation des arguments de fonction.



[[P0245]](http://wg21.link/p0245) Littéral pour exprimer la virgule flottante en hexadécimal
--------------------------------------------------------------------------------------------
    
La réunion de Jacksonville en février 2016 a amendé ce *TS* qui permet d'exprimer les [virgule flottante (IEEE 754)](https://fr.wikipedia.org/wiki/Virgule_flottante#Norme_IEEE_754) en hexadécimal. Enfin, le C++ permet d'avoir une représentation exacte des [virgules flottantes](http://en.cppreference.com/w/cpp/language/floating_literal). Cette fonctionnalité était déjà présente depuis longtemps dans d'autres langages : C99, Java 5 (2004)...
    
La représentation hexadécimale a l'avantage d'être celle du registre (mémoire binaire). Attention à la notation décimale des virgules flottantes. Par exemple, `0.1f` ne vaut pas exactement `0.1` mais `0.10000000149...`. Un [exemple](http://coliru.stacked-crooked.com/a/7b70c88142f28581) :
    
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
    
Les hexadécimaux permettent d'écrire la représentation exacte des virgules flottantes en s'affranchissant de ces erreurs d'arrondis.
Passons à la pratique :
    
```cpp
// Fraction hexadécimale
float  v = 0xa.bp3f;
assert(v == 85.5f);
// 0xA.B = 0xA*16^0 + 0xB*16^-1
// 0xA   = 10
// 0x.B  = 11/16 = 0,6875
// 0xA.B = 10,6875
// p3 = 2^3 = 8
// v = 10,6875*8 = 85,5
// 'f' final = type 'float'
    
double w = 0xC0DE2017.1CAFEp-1;
assert(w == 1617891339.55602931976318359375);
// 0xC0DE2017 = 3235782679
// 0x1CAFE    = 117502
// 0xFFFFF    = 1048576
// p-1        = 2^-1 = 1/2
// w = (3235782679 + 117502/1048576) / 2
```



### Concours
    
Chère lectrice, cher lecteur *LinuxFr.org*, as-tu d'autres idées de jeux de mots avec cette notation hexadécimale ? Alors défoule toi dans les commentaires ;-) Les plus beaux jeux de mots seront récompensés par des petits cadeaux *(goodies)* sur le stand *LinuxFr.org* au salon [Paris Open Source Summit](https://linuxfr.org/sections/paris-open-source-summit) les 16 et 17 novembre 2016. Possibilité de les envoyer par courrier ~~électronique~~ postal ;-)
    
Remarquons le `p` à la fin. Celui-ci représente l'exposant binaire et il est suivi par un entier décimal (et non pas hexadécimal). Cet exposant binaire est obligatoire pour plusieurs raisons :
    
- Évite l'ambiguïté du `f` final dans `0xA.Bf` (`float` ou le chiffre `F` hexadécimal ?) ;
- Évite l'ambiguïté du `E` dans `0xa.bE-12` (exposant `-12` ou `0xA.BE - 12` ?) ;
- Correspond à la norme [IEEE 754](https://fr.wikipedia.org/wiki/IEEE_754) (puissance de deux) ;
- 100% compatible avec la notation C99 (et celle d'autres langages).
    
Tentons de représenter cette notation hexadécimale en [regex](https://fr.wikipedia.org/wiki/Expression_rationnelle) :
    
* `0[xX][0-9a-fA-F]+[.]?[pP][+-]?[0-9]+[fFlL]?`
* `0[xX][0-9a-fA-F]*[.][0-9a-fA-F]+[pP][+-]?[0-9]+[fFlL]?`



### Termes du standard
    
Allez, soyons curieux, regardons comment le standard C++ spécifie cette notation avec un extrait du chapitre **§ 2.13.4 Floating literals** du [brouillon C++17](https://github.com/cplusplus/draft/raw/master/papers/n4604.pdf) :
    
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
    
Et l'équivalent chez [cppreference.com](http://en.cppreference.com/w/cpp/language/floating_literal) :
    
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
    
En attendant C++17, il est possible d'utiliser [`strtof()`](http://en.cppreference.com/w/cpp/string/byte/strtof) et [`std::hexfloat`](http://en.cppreference.com/w/cpp/io/manip/fixed) pour jouer avec les virgules flottantes hexadécimales. Un exemple :
    
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
    
Nous pouvons regretter qu'il faille utiliser des fonctions `strtof()` issues du C. En théorie, `std::hexfloat` devrait fonctionner pour l'entrée (`istream`). Mais dans la pratique `std::hexfloat` semble ne fonctionner que pour la sortie (`ostream`). L'exemple suivant ne fonctionne toujours pas avec GCC-6.2 et Clang-3.9 :
    
```cpp
double d;
std::istringstream("0xA.Bp-1") >> std::hexfloat >> d;
std::cout << d;
```


[[P0292]](https://wg21.link/p0292) `if constexpr`
------------------------------------------------
    
À [l'origine (fin 2011)](https://wg21.link/n3322), c'était `static_if`. Puis renommé en [`constexpr_if`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0128r0.html). Et détaché en deux mots `constexpr if`. Finalement, les deux mots sont inversés pour donner `if constexpr`. Cette fonctionnalité va simplifier beaucoup de code générique :
    
```cpp
// Trois définitions nécessaires avant C++17
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
    
// Une seule définition grâce à C++17
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

[[P0386]](http://wg21.link/p0386) Variable `inline`
---------------------------------------------------
    
Les variables `inline` — comme les fonctions `inline` — peuvent être définies dans plusieurs unités de traduction (_translation units_). Son utilisation suggère au compilateur de substituer l'appel à la variable par son contenu. Elles sont adéquates pour remplacer les macros non-triviales. Plus subtil, on peut contourner la règle de la définition unique (_One Definition Rule_).
    
```cpp
struct A
{
  // Déclaration de la variable inline
  static int v;
};
    
// Définition de la variable inline
inline int A::v = 0;
    
// Ou plus simplement
struct B
{
  static inline int v = 0; 
};
    
// Les variables constexpr sont implicitement inline
constexpr const int celerite_lumiere = 299'792'458;
``` 
    
Par curiosité, [générons le code assembleur](https://framagit.org/Cpp17/variable_inline) x86_64 de l'exemple ci-dessus [avec](https://framagit.org/Cpp17/variable_inline/blob/master/avec_inline.cc) et [sans variable `inline`](https://framagit.org/Cpp17/variable_inline/blob/master/sans_inline.cc). Le compilateur `clang++ -S --std=c++1z -O0` optimise davantage le code avec variable `inline` en supprimant les lignes suivantes :
    
```nasm
.type	_ZN1A27variable_inline_sans_inlineE,@object
.section	.rodata,"a",@progbits
.globl	_ZN1A27variable_inline_sans_inlineE
.p2align	2
_ZN1A27variable_inline_sans_inlineE:
.long	42
.size	_ZN1A27variable_inline_sans_inlineE, 4
```

Améliorations concernant les attributs
======================================
    
Trois nouveaux [attributs standards](http://en.cppreference.com/w/cpp/language/attributes#Standard_attributes) : `[[fallthrough]]`, `[[nodiscard]]` et `[[maybe_unused]]`. Initialement, ces trois nouveaux attributs étaient portés par un seul *TS*, le [P0068](https://wg21.link/p0068). Ces attributs complètent les `[[noreturn]]`, `[[carries_dependency]]` et `[[deprecated]]` introduits par C++11 et C++14.

[[P0188]](https://wg21.link/p0188) `[[fallthrough]]`
---------------------------------------------------
    
Le terme anglais *fall through* désigne le fait de *passer à travers* (*entre les mailles du filet*, *tomber à l'eau*...). Cette expression était déjà utilisée comme convention pour signifier l'[intention de continuer avec le prochain `case` dans un `switch`](https://github.com/search?l=C&q=fall+through&type=Code) (c'est à dire de ne pas terminer le `case` avec un `break`).
    
```cpp
switch (valeur)
{
case 1:
  std::cout <<" valeur 1";
  break;
    
case 2:  // fall through
case 3:
  std::cout <<" valeur 2 ou 3";
  break;
    
default:
  std::cout <<" valeur différente"
              " de 1, 2, 3, 4";
}
``` 
    
Donc, comme son nom l'indique, l'attribut **`[[fallthrough]]`** indique au compilateur (ou à l'outil d'analyse statique de code) que c'est normal qu'il n'y ait pas de `break;` à la fin d'un `case`, on continue bien avec le `case` suivant. Cela évite des avertissements _(warnings)_ inutiles.
      
```cpp
switch (valeur)
{
case 1:
  std::cout <<" valeur 1";
  break;
    
case 2:            // Pas de break
  [[fallthrough]]; // => Continue avec
                   // le case suivant
case 3:
  std::cout <<" valeur 2 ou 3";
  break;
    
case 4:
  std::cout <<" valeur 4";
  // Ici pas de break ni de [[fallthrough]]
  // Un oubli du développeur ?
  // => Le compilateur avertit
    
default:
  std::cout <<" valeur différente"
              " de 1, 2, 3 et 4";
}
```


[[P0189]](https://wg21.link/p0189) `[[nodiscard]]`
-------------------------------------------------
    
L'attribut **`[[nodiscard]]`** indique que la valeur de retour d'une fonction ne doit pas être ignorée. Ce fonctionnent était déjà implémenté par l'extension GNU `__attribute__((warn_unused_result))`.
    
```cpp
// Ancienne version de affiche_division()
// avec une faille : la division par zéro 
//void affiche_division (int a)
//{ std::cout << (42/a); }
    
// Nouvelle version
// Le code de retour doit être
// pris en compte par l'appelant
[[nodiscard]]
bool affiche_division (int a)
{
  if (a == 0)
    return false; // échec
    
  std::cout << (42/a);
  return true;    // succès
}
      
// Mais main() n'a pas été mise à jour !
int main (int argc, char *argv[])
{
  affiche_division(argc-1);
  // Le compilateur avertit que
} // le code de retour est ignorée
```

[[P0212]](https://wg21.link/p0212) `[[maybe_unused]]`
----------------------------------------------------
    
L'attribut **`[[maybe_unused]]`** [(qui devait s'appeler `[[unused]]`)](https://wg21.link/p0068) permet de supprimer des avertissements _(warning)_ quand une variable, une fonction ou un paramètre de fonction n'est pas utilisé. Notons que la spécification C++ traite de plus en plus des avertissements _(warning)_, auparavant seules les erreurs des compilateurs était traitées.
    
```cpp
[[maybe_unused]]
void affiche_division(int a)
{ std::cout << (42/a); }
    
int main (int argc, [[maybe_unused]] char *argv[])
{
  [[maybe_unused]]
  bool test = argc % 2;
  assert(test); // assert() désactivé en
}               // mode Release (-DNDEBUG)
    
// Avant C++17, pour éviter les warnings :
#ifdef DOXYGEN_PARSING
#  define DOC_ONLY(x) x
#else
#  define DOC_ONLY(x)
#endif
    
#ifdef NDEBUG
#  define DEBUG_ONLY(x)    // Release
#else
#  define DEBUG_ONLY(x) x  // Debug
#endif
    
int main (int argc, char** DOC_ONLY(argv))
{
  DEBUG_ONLY(bool impaire = argc % 2);
  assert(impaire);
}
``` 
    
[Mozilla propose aussi `DebugOnly<T>`](https://developer.mozilla.org/docs/Mozilla/Debugging/DebugOnly%3CT%3E) (plus élégant qu'une macro).

[[N4266]](https://wg21.link/n4266) Appliquer les `[[attributs]]` aux `namespace` et `enum`
-----------------------------------------------------------------------------------------
    
Ce *TS* corrige un oubli du C++14 et permet d'appliquer des `[[attributs]]` aux `namespace` et `enum`.
    
```cpp
[[maybe_unused]]
namespace debug
{
enum Couleur {
  Rouge,
  Vert,
  Web [[deprecated("Ce n'est pas une couleur")]],
  Bleu
};
}
```

[[P0028]](https://wg21.link/p0028) `using` évite la répétition des namespace d'`[[attribut]]`
--------------------------------------------------------------------------------------------
    
```cpp 
// Avant ce TS, on était obligé de répéter le namespace "rpr"
void f() {
  [[ rpr :: kernel, rpr :: target(cpu,gpu)]]
  do_task();
}
``` 
    
```cpp
// Ce TS permet d'éviter de répéter "rpr"
void f() {
  [[ using rpr:  kernel, target(cpu,gpu)]]
  do_task();
}
```


[[P0283]](https://wg21.link/p0283) Ignorer les `[[attributs]]` non reconnus
---------------------------------------------------------------------------
    
Avec C++17, les compilateurs doivent désormais ignorer les attributs qu'ils ne connaissent pas. Avant, les compilateurs pouvaient rejeter les attributs ne faisant pas partie du standard.


Améliorations concernant les lambdas
====================================
    
Les [lambdas](http://en.cppreference.com/w/cpp/language/lambda) ont été introduites avec C++11. C++14 a améliorer leur utilisation, notamment en permettant les variadiques lambdas. Et C++17 apporte deux autres améliorations.

[[N4487]](https://wg21.link/n4487) Lambda `constexpr`
----------------------------------------------------
    
Les lambda sont automatiquement `constexpr` si répond aux critères `constexpr`.

[[P0018]](https://wg21.link/p0018) Capture de `*this`
----------------------------------------------------
    
Dans une lambda, accéder aux membres de `this` se faisait toujours via le pointeur, comme `this->membre`. C++17 permet une capture d'une copie de `*this` avec la syntaxe `[=,copie=*this]`. Tout le contenu de l'objet `*this` est copié (capturé) au lieu de seulement du pointeur `this`. C'est très avantageux pour les petits objets. La copie d'un objet plus volumineux permet aussi d'éviter de mettre en place des verrous entre fils d'éxécution [*(value semantics)*](https://en.wikipedia.org/wiki/Value_semantics).


Sucre syntaxique
================

[[N3928]](https://wg21.link/n3928) `static_assert(expr)` avec un seul paramètre (sans le second paramètre "message")
-----------------------------------------------------------------
    
C++17 permet d'écrire `static_assert(condition)` avec un seul paramètre. Avant, seule la fonction [`static_assert(condition, message)`](http://fr.cppreference.com/w/cpp/language/static_assert) était disponible avec le second paramètre `message` obligatoire.
    
```cpp
// avant C++17 il était courant de fournir un message vide
static_assert(sizeof(int) == 4, "");
    
// avec C++17
static_assert(sizeof(int) == 4);
``` 
    
Pour l’anecdote, cette fonctionnalité aurait bien pu s'appeler `constexpr_assert()` car `constexpr` exprime que c'est évalué lors de la compilation, ce qui est plus précis que `static` pour `constexpr_assert()`. La fonctionnalité `static_if` s'est bien fait renommée `constexpr_if` (voir plus bas dans la dépêche).
    
Soulignons que les [mots clés](http://en.cppreference.com/w/cpp/keyword) `constexpr` et `static_assert()` permettent au C++ de réaliser l'adage *"Compilé c'est testé, linké c'est livré"* comme illustré par le [comic strip](https://fr.wikipedia.org/wiki/Comic_strip) ci-dessous.
    
[![Un développeur annonce à son responsable "Compilé c'est Testé, Linké c'est Livré" puis explique que le code C++ est constexpr et les tests sont static_assert()](https://cpp-frug.github.io/materials/images/compiler-c-est-tester_copyright-OliverH-2016_CC-BY-SA-3.0.svg)](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#compil%C3%A9-cest-test%C3%A9)

[[N4230]](https://wg21.link/n4230) `namespace aa::bb` imbriqué
--------------------------------------------------------------
    
En C++17, écrire **[`namespace`](http://en.cppreference.com/w/cpp/language/namespace) `aa::bb { }`** correspond à **`namespace aa { namespace bb { } }`**.
    
```cpp
// Avant C++17
namespace aa {
namespace bb { 
}
}

// Avec C++17
namespace aa::bb {
}
```

[[N4295]](https://wg21.link/n4295) Expression dépliable
-------------------------------------------------------
    
Les fonctions et classes variadiques peuvent réaliser des expressions dépliables, [exemple](http://gcc.godbolt.org/#g:!((g:!((g:!((h:codeEditor,i:(j:1,options:(colouriseAsm:'0',compileOnChange:'0'),source:'template%3Ctypename+...Types%3E%0Aauto+somme+(Types...+valeurs)%0A%7B+return+(valeurs+%2B+...)%3B+%7D%0A%0Atemplate%3Cbool+...Valeurs%3E%0Aauto+un_seul()%0A%7B+return+(...+%7C%7C+Valeurs)%3B+%7D%0A%0Aint+main()%0A%7B%0A++if+(un_seul%3Cfalse,true,false%3E())%0A++++return+somme(1,2,3,4)%3B%0A%7D%0A'),l:'5',n:'1',o:'C%2B%2B+source+%231',t:'0')),k:49.99999999999999,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:compiler,i:(compiler:clang390,filters:(b:'0',commentOnly:'0',directives:'0',intel:'0'),options:'-std%3Dc%2B%2B1z+-Weverything+-Wno-c%2B%2B98-compat+-Os'),l:'5',n:'0',o:'%231+with+x86-64+clang+3.9.0',t:'0')),k:49.99999999999999,l:'4',n:'0',o:'',s:0,t:'0')),l:'2',n:'0',o:'',t:'0')),version:4) :
    
```cpp
template<typename ...Types>
auto somme (Types... valeurs)
{ return (valeurs + ...); }

template<bool ...Valeurs>
auto un_seul()
{ return (... || Valeurs); }

int main()
{
  if (un_seul<false,true,false>())
    return somme(1,2,3,4);
}
```



[[P0036]](https://wg21.link/p0036) Révision de la TS précédente **N4295**
-------------------------------------------------------------------------
    
Cette *TS* limite les ambitions de la *TS* sur les expressions dépliables.
    
```cpp
std::vector v1 {1, 2, 3};
std::vector v2 {2, 2, 2};
    
// La fonction mixe
// mélange les vecteurs
// et retourne un vecteur
auto v3 = mixe(v1, v2);
    
template<typename ...Types>
auto fait_un_truc_magique (Types... x)
{ return mixe(x + ...); }
    
// Oups la fonction a été appelée sans paramètres
auto vec = fait_un_truc_magique();
    
// D'après N4295, la ligne ci-dessus revient à faire
auto vec = mixe(0);
``` 
    
D'après la *TS* **N4295**, le compilateur aurait du interpréter l'absence de paramètre dans `mixe(x + ...)` comme `mixe(0)`. Cette *TS* interdit l'absence de paramètre pour les expressions dépliables utilisant `+ * & |`. Attention, cette *TS* n'a pas été suffisamment vérifiée...

[[P0017]](http://wg21.link/p0017) Héritage des agrégats d'initialisation
------------------------------------------------
    
L'*agrégat d'initialisation* c'est le nom barbare d'une technique bien connue des développeurs C et C++ :
    
```cpp
struct Personne
{
    std::string nom;
    int         age;
};
    
// Initialisation avec un agrégat
Personne a{"Alice", 42};
``` 
    
Ce *TS* permet d'utiliser également les *agrégat d'initialisation* avec l'héritage :
    
```cpp
struct Poste
{
    std::string metier;
    int         anciente;
    
    Poste() { metier = "non spécifié"; }
};
    
struct Collegue : Personne, Poste
{
    bool teletravail = false;
};
    
Collegue b{ {"Bob", 30}, {"Développeur", 10}, true };
Collegue c{ {"Cloé", 40}, {"Manager", 15} };
Collegue d{ {"Didier", 50}, {} }; // metier = "non spécifié", anciennete = 0
Collegue e{ {"Élodie"}, {"Big Boss"}, false };
``` 
    
Attention, ces exemples ci-dessus n'ont pas pu être vérifiés faute d'implémentation de cette fonctionnalité dans Clang-3.9 et GCC-7.

[[P0091]](https://wg21.link/p0091) Déduction des arguments `template` du constructeur
-------------------------------------------------------------------------------------
    
Le compilateur peut [déduire les arguments `template` des fonctions](http://en.cppreference.com/w/cpp/language/template_argument_deduction). [Exemple](http://gcc.godbolt.org/#g:!((g:!((g:!((h:codeEditor,i:(j:1,options:(colouriseAsm:'0',compileOnChange:'0'),source:'template+%3Cclass+T%3E%0AT+foo(T+v)+%7B+return+v%2B%2B%3B+%7D%0A++++%0Aint+main()%0A%7B%0A++auto+v+%3D+foo(0)%3B%0A++return+v%3B%0A%7D%0A'),l:'5',n:'1',o:'C%2B%2B+source+%231',t:'0')),k:50,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:compiler,i:(compiler:clang390,filters:(b:'0',commentOnly:'0',directives:'0',intel:'0'),options:'-std%3Dc%2B%2B1z+-Weverything+-Wno-c%2B%2B98-compat+-Os'),l:'5',n:'0',o:'%231+with+x86-64+clang+3.9.0',t:'0')),k:50,l:'4',n:'0',o:'',s:0,t:'0')),l:'2',n:'0',o:'',t:'0')),version:4):
    
```cpp
template <class T>
T foo(T v) { return v++; }
    
// Déduit que le type T est int
auto v = foo(0);
``` 
L'idée est d'étendre cette déduction aux classes, via les arguments des constructeurs. Attention, les compilateurs [GCC-7 et Clang-3.9 ne compilent pas (encore?) le code source ci-dessous](http://gcc.godbolt.org/#g:!((g:!((g:!((h:codeEditor,i:(j:1,options:(colouriseAsm:'0',compileOnChange:'0'),source:'%23include+%3Carray%3E%0A%23include+%3Ctuple%3E%0A%23include+%3Cexperimental/array%3E%0A%0Adecltype(auto)+a+%3D+std::experimental::make_array(1,2,3)%3B%0A++++%0Astd::array%3Cint,3%3E+avant%7B1,2,3%7D%3B+//+Avant+C%2B%2B17%0Astd::array++++++++avec+%7B1,2,3%7D%3B+//+Avec++C%2B%2B17%0A++++%0Astd::pair%3Cint,char%3E+p_avant(4,!'L!')%3B%0Astd::pair+++++++++++p_avec+(4,!'L!')%3B%0A++++%0Aauto+++++++t_avant+%3D+std::make_tuple(%22voiture%22,4,!'L!')%3B%0Astd::tuple+t_avec(%22voiture%22,4,!'L!')%3B'),l:'5',n:'1',o:'C%2B%2B+source+%231',t:'0')),k:50,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:compiler,i:(compiler:g7snapshot,filters:(b:'0',commentOnly:'0',directives:'0',intel:'0'),options:'-std%3Dc%2B%2B1z'),l:'5',n:'0',o:'%231+with+x86-64+gcc+7+(snapshot)',t:'0')),k:50,l:'4',n:'0',o:'',s:0,t:'0')),l:'2',n:'0',o:'',t:'0')),version:4). Ce code est peut-être erroné...
    
```cpp
// Avec les fonctions d'aide
auto a = std::make_array(1,2,3);
    
// Avant C++17 et Avec C++17
std::array<int,3> avant{1,2,3};
std::array avec{1,2,3};
    
std::pair<int,char> p_avant(4,'L');
std::pair p_avec(4,'L');
    
auto t_avant = std::make_tuple("voiture",4,'L');
std::tuple t_avec("voiture",4,'L');
``` 
    
Pas mal de fonctions d'aide `make_***()` risquent de devenir inutiles...

[[P0127]](https://wg21.link/p0127) Déclaration des paramètres `template<auto>`
-----------------------------------------------------------------------------
    
Le `template<auto>` permet de remplacer `MaClasse<int,42>` par un élégant `MaClasse<42>`. Apparemment, ce n'est [pas encore supporté](http://gcc.godbolt.org/#g:!((g:!((g:!((h:codeEditor,i:(j:1,options:(colouriseAsm:'0',compileOnChange:'0'),source:'template+%3Ctypename+Type,+Type+Constante%3E%0Astruct+Cpp14%0A%7B%0A++auto+foo()+const+%7B%0A++++auto+x+%3D+Constante%3B%0A++++return+%2B%2Bx%3B%0A++%7D%0A%7D%3B%0A++++%0Atemplate+%3Cauto+Constante%3E%0Astruct+Cpp17%0A%7B%0A++auto+foo()+const+%7B%0A++++auto+x+%3D+Constante%3B%0A++++return+%2B%2Bx%3B%0A++%7D%0A%7D%3B%0A++++%0Aint+main()%0A%7B%0A++const+auto+x+%3D+42%3B%0A++Cpp14%3Cdecltype(x),+x%3E+cpp14%3B%0A++Cpp17%3Cx%3E+cpp17%3B%0A++return+cpp14.foo()+%2B+cpp17.foo()%3B%0A%7D%0A'),l:'5',n:'1',o:'C%2B%2B+source+%231',t:'0')),k:33.333333333333336,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:compiler,i:(compiler:clang390,filters:(b:'0',commentOnly:'0',directives:'0',intel:'0'),options:'-Os+-std%3Dc%2B%2B1z+-Weverything+-Wno-c%2B%2B98-compat'),l:'5',n:'0',o:'%231+with+x86-64+clang+3.9.0',t:'0')),k:29.11051212938005,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:output,i:(compiler:1,editor:1),l:'5',n:'0',o:'%231+with+x86-64+clang+3.9.0',t:'0')),k:37.5561545372866,l:'4',n:'0',o:'',s:0,t:'0')),l:'2',n:'0',o:'',t:'0')),version:4) par Clang-3.9 et GCC-7.0.
    
```cpp
template <typename Type, Type Constante>
struct Cpp14
{
  auto foo() const {
    auto x = Constante;
    return ++x;
  }
};
    
template <auto Constante>
struct Cpp17
{
  auto foo() const {
    auto x = Constante;
    return ++x;
  }
};
    
int main()
{
  const auto x = 42;
  Cpp14<decltype(x), x> cpp14;
  Cpp17<x> cpp17;
  return cpp14.foo() + cpp17.foo();
}
```

[[P0217]](https://wg21.link/p0217) Attaches structurées *(Structured bindings)*
------------------------------------------------------------------------------
    
La **décomposition du retour de fonction** est limitée aux `std::tuple`, aux tableaux (comme `std::array`) et aux structures plates (comme `std::pair`).
    
```cpp
struct A
{
  int  a;
  bool b;
  char c;
};

A foo() {
  return A{42, true, 'c'};
}

auto [ x, y ] = foo();
// Attention, non testé...

assert(x == 42);
assert(y == true);
static_assert(std::is_same_v<decltype(x),decltype(A::a)>);
static_assert(std::is_same_v<decltype(y),decltype(A::b)>);
``` 
    
Quand la fonction retourne un `std::tuple` (comme le `std::pair`) il était déjà possible d'utiliser `std::tie`. Mais la décomposition est plus commode (sauf pour le `std::ignore`).
    
```cpp
#include <set>
#include <tuple>

int main()
{
  std::set<int> entiers;
 
  // Avant C++17
  std::set<int>::iterator iter;
  bool inserted; 
  std::tie(iter, inserted) = entiers.insert(42);
  
  // Avec C++17
  auto [ it, is_inserted ] = entiers.insert(42);
}
```

[P0305] `if(init;condition)` et `switch(init;condition){}`
---------------------------------------------------------
    
Ce *TS* introduit les *instruction de sélection avec initialiseur*.
En concret, c'est l'ajout du terme **`initialisation;`** dans les instructions :
    
* `if( initialisation; condition )` et
* `switch( initialisation; condition )`
    
Notons que cela ressemble à `for( initialisation; condition; incrémentation )`.
    
L'expression **`if(MonType v = truc())`** peut donc être remplacée par **`if(MonType v = truc(); v)`**.
    
```cpp
// Version verbeuse
{
  auto paire = map.insert({k,v});
  auto it       = paire.first;
  bool inserted = paire.second;
  if (inserted)
  {
    foo(it);
    return iterateur;
  }
}   // <- bloc pour limiter la portée des variables

// Version C++17
if (auto [it, inserted] = map.insert({k,v}); inserted)
{
  foo(it);
  return iterateur;
}
```


Corrections
===========


[[N3922]](https://wg21.link/n3922) Déduction `auto x{42};` comme `int x{42};`
----------------------------------------------------------------------------
    
Ce *TS* comble un trou sur les règles de déduction pour `auto` à partir des {listes d'initialisation}.
    
```cpp
auto a   {1};     //ok => int a{1};
auto b = {1};     //ok => std::initializer_list<int> b = {1};
    
auto c   {1, 2};  //KO car plus d'un élément
auto d = {1, 2};  //ok => std::initializer_list<int> d = {1, 2};
    
auto e   {1, 2.0}; //KO car plus d'un élément
auto f = {1, 2.0}; //KO car pas le même type (int et double)
``` 
    
**Exercice :** Chercher la différence entre l'image ci-dessous et celle au tout début de la dépêche.
    
[![Une écolière écrit une boucle for en C++17 pour régler sa punition d'écrire 100 fois "Je ne dois pas envoyer d'avion en papier"](http://cpp-frug.github.io/materials/images/cpp-ecole-primaire_copyright-Ziyue-OliverH-2016_CC-BY-SA-3_auto.jpg)](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#c17-sauve-une-%C3%A9coli%C3%A8re)

[[N4051]](https://wg21.link/n4051) Autoriser `typename` pour les paramètres `template template`
-----------------------------------------------------------------------------------------------
    
Avant C++17, seule la classe `Cpp98` était conforme au standard :
    
```cpp
template<template<typename> class    T> class Cpp98;
template<template<typename> typename T> class Cpp17;
``` 
    
Mais à quoi cela sert les paramètres `template template` ?
Cela sert, par [exemple](http://gcc.godbolt.org/#g:!((g:!((g:!((h:codeEditor,i:(j:1,options:(colouriseAsm:'0',compileOnChange:'0'),source:'%23include+%3Cvector%3E%0A%23include+%3Clist%3E%0A%0Atemplate%3C+template+%3Ctypename,+typename%3E+typename+Container%0A++++++++,+typename+T%0A++++++++,+typename+Allocator+%3E%0Aauto+convert_to_vector(const+Container%3CT,+Allocator%3E%26+container)%0A%7B%0A+++std::vector%3CT,+Allocator%3E+v%3B%0A+++v.reserve(container.size())%3B%0A+++for+(const+auto%26+e+:+container)++v.push_back(e)%3B%0A+++return+v%3B%0A%7D%0A%0Aint+main()%0A%7B%0A++std::list%3Cint%3E+s%7B3,1,7,4%7D%3B%0A++auto+v+%3D+convert_to_vector(s)%3B%0A%7D'),l:'5',n:'1',o:'C%2B%2B+source+%231',t:'0')),k:49.99999999999999,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:compiler,i:(compiler:clang390,filters:(b:'0',commentOnly:'0',directives:'0',intel:'0'),options:'-std%3Dc%2B%2B1z+-Wall+-Wextra+-pedantic'),l:'5',n:'0',o:'%231+with+x86-64+clang+3.9.0',t:'0')),k:49.99999999999999,l:'4',n:'0',o:'',s:0,t:'0')),l:'2',n:'0',o:'',t:'0')),version:4), à obtenir les paramètres `template` d'un conteneur :
    
```cpp
template< template <typename, typename> typename Container
        , typename T
        , typename Allocator >
auto convert_to_vector (const Container<T, Allocator>& container)
{
   std::vector<T, Allocator> v;
   v.reserve(container.size());
   for (const auto& e : container)  v.push_back(e);
   return v;
}
``` 
    
C'est juste un exemple, la [version suivante](http://gcc.godbolt.org/#g:!((g:!((g:!((h:codeEditor,i:(j:1,options:(colouriseAsm:'0',compileOnChange:'0'),source:'%23include+%3Cvector%3E%0A%23include+%3Clist%3E%0A%0Atemplate%3Ctypename+Container%3E%0Aauto+convert_to_vector+(const+Container%26+container)%0A%7B%0A+++std::vector%3Ctypename+Container::value_type,+typename+Container::allocator_type%3E+v%3B%0A+++v.reserve(container.size())%3B%0A+++for+(const+auto%26+e+:+container)++v.push_back(e)%3B%0A+++return+v%3B%0A%7D%0A%0Aint+main()%0A%7B%0A++std::list%3Cint%3E+s%7B3,1,7,4%7D%3B%0A++auto+v+%3D+convert_to_vector(s)%3B%0A%7D'),l:'5',n:'1',o:'C%2B%2B+source+%231',t:'0')),k:49.99999999999999,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:compiler,i:(compiler:clang390,filters:(b:'0',commentOnly:'0',directives:'0',intel:'0'),options:'-std%3Dc%2B%2B1z+-Wall+-Wextra+-pedantic'),l:'5',n:'0',o:'%231+with+x86-64+clang+3.9.0',t:'0')),k:49.99999999999999,l:'4',n:'0',o:'',s:0,t:'0')),l:'2',n:'0',o:'',t:'0')),version:4) est plus pertinente :
    
```cpp
template<typename Container>
auto convert_to_vector (const Container& container)
{
   std::vector<typename Container::value_type, typename Container::allocator_type> v;
   v.reserve(container.size());
   for (const auto& e : container)  v.push_back(e);
   return v;
}
``` 
    
Chère lectrice, cher lecteur *LinuxFr.org*,
Tu as peut-être déjà utilisé les paramètres `template template` ?
Ou tu as peut-être de meilleurs idées sur l'utilité d'une telle fonctionnalité ?
Alors partage dans les commentaires tes exemples ;-)
Et le top du top serait un exemple de paramètres `template template` variadiques !
Un truc du genre :
    
```cpp
template< template<typename,typename,typename...> typename Truc
        , typename    Premier >
        , typename    Deuxieme >
        , typename... Reste >
auto machin( const Truc<Premier, Deuxieme, Reste...>& t1
           , const Truc<Deuxieme, Premier, Reste...>& t2)
{
    Truc<Reste...> t3 (t1, t2);
    return t1 + t2 - t3;
}
``` 
    
**Anecdote :** À l'époque lointaine où les `template` avaient été introduites au C++, seul le mot-clé `class` permettait d'indiquer que le paramètre `template` est un type (le mot-clé `typename` n'existait pas encore). Donc, pour un paramètre `template`, le mot-clé `class` désigne tout les types, dont `struct`, `int`... (pas seulement les types `class`). Dans l'exemple ci-dessous, `class T` signifie que `T` est un type, n'importe lequel :
    
```cpp
template <class T>
T foo(T);
    
int v = foo(42);
``` 
    
Mais les compilateurs C++ avaient du mal a déduire la nature des certaines instructions :
    
```cpp
template <class T>
void foo()
{
  T::fonction();    // Est-ce objet de type T::fonction ?
  T::type();        // Est-ce un appel de fonction ?
  T::type     *  v; // Est-ce une multiplication ?
  T::constante** v; // Est-ce une déclaration ?
}
``` 
    
Alors le mot-clef `typename` a été ajouté, [exemple](http://gcc.godbolt.org/#g:!((g:!((g:!((h:codeEditor,i:(j:1,options:(colouriseAsm:'0',compileOnChange:'0'),source:'template%3Ctypename+...Types%3E%0Aauto+somme+(Types...+valeurs)%0A%7B+return+(valeurs+%2B+...)%3B+%7D%0A%0Atemplate%3Cbool+...Valeurs%3E%0Aauto+un_seul()%0A%7B+return+(...+%7C%7C+Valeurs)%3B+%7D%0A%0Aint+main()%0A%7B%0A++if+(un_seul%3Cfalse,true,false%3E())%0A++++return+somme(1,2,3,4)%3B%0A%7D%0A'),l:'5',n:'1',o:'C%2B%2B+source+%231',t:'0')),k:49.99999999999999,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:compiler,i:(compiler:clang390,filters:(b:'0',commentOnly:'0',directives:'0',intel:'0'),options:'-std%3Dc%2B%2B1z+-Weverything+-Wno-c%2B%2B98-compat+-Os'),l:'5',n:'0',o:'%231+with+x86-64+clang+3.9.0',t:'0')),k:49.99999999999999,l:'4',n:'0',o:'',s:0,t:'0')),l:'2',n:'0',o:'',t:'0')),version:4) :
    
```cpp
template <class T>
void foo()
{
  T::fonction();       // Appel de fonction
  typename T::type();  // Objet temporaire
  typename T::type* v; // Déclaration d'une variable
  T::constante * *v;   // Multiplication
}
``` 
    
Puis, le mot-clef `typename` a aussi remplacé `class` pour le paramètre `template`. Et c'est plus logique car ce n'est pas restreint aux seuls types déclarés avec le mot-clé `class`. La rétrocompatibilité ayant été conservée, les mots-clés `typename` et `class` sont interchangeables pour les paramètres `template`.
    
```cpp
template <class T> // ou <typename T>
void foo() { }
    
template <typename T> // ou <class T>
void bar() { foo<T>(); }
``` 
    
Et avec C++17, le cas du paramètre `template template` peut enfin utiliser `typename`.
    
**Conséquence :** Alors que le nom originel du C++ était ***C with `class`***, nous pourrions dire que le C++17 est le ***C++ without `class`***, c'est à dire, sans avoir besoin du mot-clé `class`. En effet, `class` est maintenant remplaçable partout soit par `typename`, soit par `struct` moyennant quelques changements :
    
```cpp
template <class T, template<class> C>
class AvecClass : C<T>
{
    int v;
};
    
template <typename T, template<typename> C>
struct SansClass : private C<T>
{
private:
    int v;
};
``` 
    
Alors, qu'en penses-tu ?
***C++ without `class`*** c'est plus² la classe ?

[[N4261]](https://wg21.link/n4261) Conversion des tableaux de pointeurs
----------------------------------------------------------------------- 
    
Ce *TS* complète la section 4.4 (conversion de qualification) sur la conversion d’un tableau de pointeurs constants/volatiles vers un autre type similaire.
    
```cpp
double      *       tableau_2d[2][3];
double      *       (*a)[3] = tableau_2d;
double      * const (*b)[3] = a;
double const* const (*c)[3] = b; // OK C++17
```


[[N4267]](https://wg21.link/n4267) Littéral de caractère UTF-8 `u8`
------------------------------------------------------------------
    
En programmation, un [littéral](https://fr.wiktionary.org/wiki/litt%C3%A9ral#Nom_commun) est un préfixe ou un suffixe qui indique le **type** d'une constante (i.e. d'une valeur codée en dur). Ce *TS* corrige l'absence du littéral `u8` pour les [caractères](http://en.cppreference.com/w/cpp/language/character_literal) déjà disponible pour les [chaînes de caractères](http://en.cppreference.com/w/cpp/language/string_literal). Nous avons maintenant [quatre littéraux de caractères](https://godbolt.org/g/60AKT3) :
    
```cpp
#include <type_traits> // std::is_same_v (pas encore dispo pour Clang-3.9)
    
// Pas de littéral
const auto narrow = 'a'; // char
static_assert(std::is_same_v<decltype(narrow), const char>);
    
// Nouveau littéral pour C++17
const auto utf8 = u8'e'; // char
static_assert(std::is_same_v<decltype(utf8), const char>);
    
// Littéraux déjà disponibles en C++ et C
const auto ucs2 = u'î'; // char16_t
const auto ucs4 = U'ö'; // char32_t
const auto wide = L'ù'; // wchar_t
    
static_assert(std::is_same_v<decltype(ucs2), const char16_t>);
static_assert(std::is_same_v<decltype(ucs4), const char32_t>);
static_assert(std::is_same_v<decltype(wide), const wchar_t>);
``` 
    
Notons que ce littéral `u8` est (pour le moment?) absent des [caractères en C](http://en.cppreference.com/w/c/language/character_constant) comme le montre ce tableau récapitulatif :
    
Nom   |Préfixe| Type     |Chaîne de caractères| Caractère
------|-------|----------|--------------------|-----------------
Wide  | `L`   |`wchar_t` | C++98 et C89/C90   | C++98 et C89/C90
UTF-8 | `u8`  |`char`    | C++11 et C11       | **C++17 seulement**
UTF-16| `u`   |`char16_t`| C++11 et C11       | C++11 et C11
UTF-32| `U`   |`char32_t`| C++11 et C11       | C++11 et C11
    
Ce littéral n'avait pas été introduit auparavant car il peut induire en erreur. En effet, un caractère `u8` ne peut contenir tous les codes UTF-8, seulement ceux qui peuvent être contenus dans un `char` (sauf du `char` représenté en 32 bits). En fait, le littéral `u8` sert à représenter n'importe quel `char` (dans le sens octet) d'une chaîne de caractère `u8` qu'il soit un code UTF-8 valide ou pas.
    
```cpp
const char* s = u8"aéîöù";           // Correct en C++11 et C11
const char  c = u8'a';               // Correct en C++17
const char t[] = {u8'a',u8'e',u8'i'};// Correct en C++17
const char ko = u8'é';               // 'é' dépasse la capacité de stockage du char (1 octet)
const auto Ko = u8'é';               // Exactement le même problème, auto ne change rien
const char ok = u8'\xFF';            // Correct en C++17 (ce n'est pas un code UTF-8 valide)
const char a[] = u8"\xFF";           // Correct en C++11 et C11 (code UTF-8 invalide)
const char b[] = {u8'\xFF',u8'\x04'};// Correct en C++17 (deux octets pour un code UTF-8 valide)
``` 
    
L'[exemple ci-dessus](https://godbolt.org/g/RMJfWb) est intéressant car GCC-6 et GCC-7 affichent des avertissements (`warning`) pour les variables `[kK]o` alors que Clang-3.6 à Clang-3.9 produisent des erreurs : GCC considère que ce code est conforme au standard C++17 (car pas d'erreur) alors que Clang non.

[[N4268]](https://wg21.link/n4268) Autoriser l'évaluation constante pour les arguments `template`
---------------------------------------------------------------------------
    
Cette *TS* harmonise les évaluations constantes pour les arguments `template` n'étant pas un type. Les arguments de type **pointeur**, **référence** et **pointeur-vers-membre** acceptent d'avantage d'expressions constantes. C'est un oubli de C++11 qui avait pourtant étendu la notion d'expression constante. La [table suivante](http://open-std.org/JTC1/SC22/WG21/docs/papers/2014/n4198.html) résume les changements.
    
Type     | C++14  | C++17
---------|--------|-------
Pointeur|`&variable`, tableau, fonction référant un objet statique ou `nullptr` | évaluation d'une adresse constante d'un objet complet statique ou d'une fonction, ou `nullptr`
Référence|objet ou fonction référant un objet statique| évaluation d'un *glvalue* constant référant un objet complet statique ou d'une fonction
Pointeur-vers-membre|`&S::statique` ou `nullptr`|toutes expressions constantes
Intégral `bool char int` ...|toutes expressions constantes|pareil
`enum`|toutes expressions constantes|pareil
`nullptr_t`|toutes expressions constantes|pareil
    
Le code source suivant permet de vérifier que cette fonctionnalité est déjà [prise en compte par GCC-6 et Clang-3.6](http://gcc.godbolt.org/#g:!((g:!((g:!((h:codeEditor,i:(j:1,options:(colouriseAsm:'0',compileOnChange:'0'),source:'//+Cette+classe+permet+de+tester%0A//+les+expressions+constantes%0Atemplate%3Cint*+ExpressionConstante%3E%0Aclass+Test%0A%7B+%7D%3B%0A++++%0A//+La+fonction+constexpr+getPtr()+retourne%0A//+un+pointeur+vers+un+objet+statique%0A//+(static+storage+duration+object)%0Aint+entier+%3D+42%3B%0Aconstexpr+int*+getPtr()+++++%7Breturn+%26entier%3B%7D%0Aconstexpr+int*+getNullptr()+%7Breturn+nullptr%3B%7D%0ATest%3C%26entier%3E++++++++ok_entier%3B%0ATest%3CgetPtr()%3E+++++++ok_Cxx17%3B+//KO+C%2B%2B14%0ATest%3CgetNullptr()%3E+++ok_nullptr%3B%0A++++%0A//+L!'expression+%26obj.statique+est+un%0A//+pointeur-vers-membre+d!'un+objet+statique%0Astruct+Str%0A%7B+int+membre%3B+static+int+statique%3B+%7D%3B%0AStr+obj%3B%0A//Test%3C%26Str::membre%3E+++ko_ptr_non_statique%3B%0ATest%3C%26Str::statique%3E+ok_ptr_statique%3B%0ATest%3C%26obj.statique%3E++ok_cxx17%3B+//KO+C%2B%2B14%0A++++%0A//+Le+pointeur+vers+un+%C3%A9l%C3%A9ment+de+tableau%0A//+statique+ne+semblent+pas+%C3%AAtre+support%C3%A9s%0Aint+++tableau%5B5%5D%3B%0A//Test%3C%26tableau%5B2%5D%3E++++ko_adresse_element%3B%0A'),l:'5',n:'1',o:'C%2B%2B+source+%231',t:'0')),k:20.007346465412752,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:compiler,i:(compiler:g6,filters:(b:'0',commentOnly:'0',directives:'0',intel:'0'),options:'-std%3Dc%2B%2B1z+-Wall+-Wextra+-pedantic'),l:'5',n:'0',o:'%231+with+x86-64+gcc+6.1',t:'0')),k:24.382417314114804,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:output,i:(compiler:1,editor:1),l:'5',n:'0',o:'%231+with+x86-64+gcc+6.1',t:'0')),k:30.610236220472437,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:output,i:(compiler:1,editor:1),l:'5',n:'0',o:'%231+with+x86-64+gcc+6.1',t:'0')),k:25,l:'4',n:'0',o:'',s:0,t:'0')),l:'2',n:'0',o:'',t:'0')),version:4) :
    
```cpp
// Cette classe permet de tester
// les expressions constantes
template<int* ExpressionConstante>
class Test
{ };
    
// La fonction constexpr getPtr() retourne
// un pointeur vers un objet statique
// (static storage duration object)
int entier = 42;
constexpr int* getPtr()     {return &entier;}
constexpr int* getNullptr() {return nullptr;}
Test<&entier>        ok_entier;
Test<getPtr()>       ok_Cxx17; //KO C++14
Test<getNullptr()>   ok_nullptr;
    
// L'expression &obj.statique est un
// pointeur-vers-membre d'un objet statique
struct Str
{ int membre; static int statique; };
Str obj;
Test<&Str::membre>   ko_ptr_non_statique;
Test<&Str::statique> ok_ptr_statique;
Test<&obj.statique>  ok_cxx17; //KO C++14
    
// Le pointeur vers un élément de tableau
// statique ne semblent pas être supportés
int   tableau[5];
Test<&tableau[2]>    ko_adresse_element;
```


[[N4285]](https://wg21.link/n4285) Réécriture de paragraphes concernant les exceptions
--------------------------------------------------------------------------------------
    
Ce *TS* a le mérite d'identifier des paragraphes qui ne sont pas clairs et de proposer une reformulation.
    
Profitons de ce *TS* pour faire l'analogie entre le standard C++ et la loi en France. Pour savoir comment la loi s'applique, il faut d'abord comprendre les textes votés par les députés, puis prendre en compte les [amendements](https://fr.wikipedia.org/wiki/Amendement_(loi)) et enfin vérifier la [jurisprudence](https://fr.wikipedia.org/wiki/Jurisprudence) sur le terrain. Et bien nous avons une ressemblance avec le standard C++ : la [norme ISO/IEC](https://linuxfr.org/news/les-coulisses-du-standard-cpp#les-versions-c) correspond à la loi (la théorie), les [*Defect Reports*](https://linuxfr.org/news/les-coulisses-du-standard-cpp#defect-report-dr) (rapports d’anomalie) et l'implémentation des compilateurs est la jurisprudence.

[[P0012]](https://wg21.link/p0012) `noexcept` devient un type système
---------------------------------------------------------------------
    
Ce *TS* intégre les spécifications d'exception dans le type système, c'est à dire que `noexcept` devient un [type système](http://en.cppreference.com/w/cpp/language/type) afin de pouvoir distinguer les types de [pointeur de fonction](http://en.cppreference.com/w/cpp/language/pointer#Pointers_to_functions) `noexcept` des autres.
    
Ainsi C++17 peut interdire la conversion de pointeurs de fonction `throw()` vers ceux de fonctions `noexcept`, mais l'inverse est toujours possible. Le code suivant est valide en **C++14**, mais ne compile plus avec **C++17** :
    
```cpp
void (*p)() throw(int);
void (**pp)() noexcept = &p; //Erreur C++17

struct S
{
  typedef void (*p)();
  operator p();
};
void (*q)() noexcept = S(); //Erreur C++17

template<class T>
void f(T*, T*) {}
void g1() noexcept {}
void g2()          {}
f(g1, g2);                 //Erreur C++17
```


[[P0035]](http://wg21.link/p0035) Allocation mémoire dynamique des données
--------------------------------------------------------------------------
    
C++11 a permis de préciser l’alignement mémoire d'une structure avec le mot clef `alignas`
    
```cpp
class alignas(16) maclasse {
	float f[4];
};
``` 
    
Mais rien n'avait été précisé dans le cas d'une allocation dynamique
    
```cpp
maclasse *p = new maclasse[5];
``` 
    
Dans ce cas l'alignement mémoire de la zone allouée restait au choix du compilateur.
    
Avec C++17 des surcharges des opérateurs `new` et `delete` permettent de préciser l'alignement. 
`new maclasse[5]` est convertis soit en :
    
*  `operator new[](sizeof(maclasse)*5+x)` 
*  `operator new[](sizeof(maclasse)*5+x, std::align_val_t(alignof(maclasse)))`  nouvelle surcharge)
    
Si `std::align_val_t(alignof(maclasse))` est supérieur à `__STDCPP_DEFAULT_NEW_ALIGNMENT__`, c'est la nouvelle surcharge de `new` qui sera utilisée.

[[P0136]](https://wg21.link/p0136) Héritage des constructeurs
-------------------------------------------------------------
    
Certaines règles d’héritage des constructeurs via `using` ont été modifiées dans un soucis de cohérence et de simplification. Concrètement, plusieurs cas d’héritages précédemment interdits sont maintenant autorisés.
    
Le [_Substitution Failure Is Not An Error (SFINAE)_](http://h-deb.clg.qc.ca/Sujets/Divers--cplusplus/SFINAE.html) sur les constructeurs hérités fonctionne de manière fiable :
    
```cpp
struct A {
  template<typename T> A(T, typename enable_if<sizeof(T) == 4, int>::type = 0);
};
struct B : A {
  using A::A; // déclare les constructeur suivants :
              //   #1: B(T)
              //   #2: B(T, typename enable_if<...>::type)
              // car maintenant A::A(T, typename enable_if<...>::type = 0)
              // est un constructeur visible depuis B
  B();
};
B b(123ull);  // Autorisé en C++17
``` 
    
Paramètres variables :
    
```cpp
struct A { A(const char *, ...); };
struct B : A { using A::A; };
    B b("%d %d", 1, 2); // Maintenant accepté dans toutes les implémentations
``` 
    
Les droits d’accès sont maintenant identiques à ceux de la classe de base :
    
```cpp
class A {
public:
 template<typename T> A(T, typename T::type);
 private:
  A(int);
  friend void f();
};
class B {
  typedef int type;
  friend class A;
};
struct C : A {
  using A::A;
};
void f() {
  A a1(B(), 0); // accepté (pas de changement)
  C c1(B(), 0); // précédemment refusé (le constructeur implicite de C ne pouvait pas accéder à B::type), maintenant accepté
    
  A a2(42); // accepté (pas de changement), f est un `friend`)
  C c2(42); // précédemment refusé,( (le constructeur implicite de C ne pouvait pas accéder au constructeur de A), maintenant accepté
}
C c3(123); // reste refusé, pas d'accès à A(int) 
``` 
En présence d’arguments par défaut, le masquage des constructeurs fonctionne maintenant de la même manière que pour les autres membres hérités via `using`.

```cpp
struct A {
  A(int a, int b = 0);
  void f(int a, int b = 0);
};
struct B : A {
  B(int a);      using A::A;
  void f(int a); using A::f;
};
struct C : A {
  C(int a, int b = 0);      using A::A;
  void f(int a, int b = 0); using A::f;
};

B b(0); // était accepté, maintenant ambigu.
b.f(0); // ambigu(pas de changement)

C c(0); // était ambigu, maintenant accepté
c.f(0); // accepté (pas de changements)
```

[[P0138]](https://wg21.link/p0138) Direct list-initialization of enums
----------------------------------------------------------------------
    
Voici comment [créer un type `byte`](https://godbolt.org/g/FI2Bj8) en C++98 :
    
```cpp
typedef unsigned char byte;
byte b1 = 42;  // OK C++98
byte b2(42);   // OK C++98
byte b3{42};   // OK C++11
``` 
    
Une autre possibilité mi-C++98, mi-C++11 :
    
```cpp
  struct byte { unsigned char v; };
//byte b1 = 42; // Erreur
//byte b2(42);  // Erreur
  byte b3{42};  // OK C++11
``` 
    
Avec les possibilités du C++11 :
    
```cpp
using byte = unsigned char;
byte b1 = 42;   // OK C++11
byte b2(42);    // OK C++11
byte b3{42};    // OK C++11
byte b4 = {42}; // OK C++11
``` 
    
Et grâce à ce *TS* intégré à C++17 :
    
```cpp
  enum byte : unsigned char { };
//byte b1 = 42;   // Erreur
//byte b2(42);    // Erreur
  byte b3{42};    // OK C++17
//byte b4 = {42}; // Erreur
``` 
    
[Voici](https://godbolt.org/g/5LPgHl) ce que tout ce *TS* autorise :
    
```cpp
enum E : int {};
E e {0};          // OK
E e = {0};        // Erreur
E e = E{0};       // OK
const E& e {0};   // OK
const E& e = {0}; // Erreur
E* p = new E{0};  // OK
    
void f(E) {}
f({0});              // Erreur
f(E{0});             // OK
E g() {return {0}; } // Erreur
    
struct A {
  E e{0};       // OK
  E e = {0};    // Erreur
  A() : e{0} {} // OK
};

struct B { E e; };
B b = { {42} };    // Erreur
B b = { E{42} };   // OK
```

[[P0184]](https://wg21.link/p0184) Généralisation des boucles pour gérer les *Intervalles (Ranges)*
-----------------------------------------------------
    
Cette petite *TS* permet aux boucles `for` *"each"* de gérer des conteneurs ayant des `begin()` et `end()` retournant des types différents mais comparables.
    
Cette correction est nécessaire à l'implémentation des [intervalles](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/n4569.pdf). Cela permet également de supporter d'avantage de [valeurs sentinelles](https://fr.wikipedia.org/wiki/Valeur_sentinelle).

[[P0296]](https://wg21.link/p0296) Forward progress guarantees (FPG) et [[P0299]](https://wg21.link/p0299) FPGs for parallel algorithms
---------------------
    
Ces deux *TS* concernent le verrouillage des fils d’exécution *(thread lock)* et des [situation de compétition](https://fr.wikipedia.org/wiki/Situation_de_comp%C3%A9tition) *(race condition)* afin de limiter les cas de [boucle infinie](https://fr.wikipedia.org/wiki/Boucle_infinie).

Compatibilité avec le langage **C**
===================================
    
[[P0063]](https://wg21.link/p0063) C++17 se réfère à C11 au lieu de C99
-----------------------------------------------------------------------
    
**C++17** est maintenant [basé sur **C11** au lieu de **C99**](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html) + **C Unicode TR**.
    
Ajout des en-têtes (_headers_) `<stdalign.h>` et `<uchar.h>`. On ignore les en-têtes **C11** `<stdatomic.h>`, `<threads.h>` et `<stdnoreturn.h>`. [Dépréciation](https://fr.wikipedia.org/wiki/D%C3%A9pr%C3%A9ciation_(informatique)) des en-têtes `<ccomplex>`, `<ctgmath>`, `<cstdalign>`, `<cstdbool>`, `<complex.h>`, `<stdalign.h>`, `<stdbool.h>` et `<tgmath.h>`.
    
Donc, **C++17** se base sur une partie du **C11**. Par exemple, la gestion du multitâche du **C** n'est pas prise en compte dans le standard (donc c'est optionnel). Pour la première fois, le **C++** n'est plus rétrocompatible —  du moins une partie — avec les en-têtes du **C** (le **C** était un sous-ensemble du **C++**).  
    
Finalement, peu de changements. Par exemple, la fonction [`aligned_alloc()`](http://en.cppreference.com/w/c/memory/aligned_alloc) avait déjà été intégrée avec **C++11**.
     
Suppression
===========

[[N4086]](https://wg21.link/n4086) Trigraphes
-------------------------------------------------------------
    
Il était une fois, un clavier qui ne permettait pas d'insérer tous les caractères nécessaires aux langages de programmation. Alors les [digraphes, puis les trigraphes](https://en.wikipedia.org/wiki/Digraphs_and_trigraphs) furent inventés afin de pallier cette limitation. C'était également le cas des premiers claviers français qui n'avaient pas tous les caractères des claviers des États-Unis, comme la [barre oblique inversée](https://fr.wikipedia.org/wiki/Barre_oblique_invers%C3%A9e) <kbd>\\</kbd> de ce [clavier AZERTY](http://thumbs4.picclick.com/d/w1600/pict/182215529855_/Apple-M4M0110F-clavier-keyboard-AZERTY-keypad-pav%C3%A9-numerique-M0120P.jpg).
    
[![Image du clavier de l'Apple II qui n'a pas de touche pour les accolades et crochets](https://upload.wikimedia.org/wikipedia/commons/thumb/2/21/Apple_II-IMG_7073.jpg/1024px-Apple_II-IMG_7073.jpg)](https://commons.wikimedia.org/wiki/File:Apple_II-IMG_7073.jpg)
    
```cpp
// Avec digraphes et trigraphes
??=include <iostream>
int main(int argc, char *argv<::>) ??< 
  const char hello_world ??(??) = "Hello world !??/0";
  std::cout << hello_world << std::endl;
??>
``` 
    
```cpp
// Sans digraphe/trigraphe
#include <iostream>
int main(int argc, char *argv[]) {
  const char hello_world[] = "Hello world !";
  std::cout << hello_world << std::endl;
}
``` 
    
Certaines entreprises maintiennent du très vieux code C/C++ contenant des [digraphes et trigraphes](https://en.wikipedia.org/wiki/Digraphs_and_trigraphs#Removal_of_trigraphs). Ces digraphes/trigraphes pourraient être remplacés par les caractères correspondants avec un script. Mais ces entreprises préfèrent les garder dans leur code source, maintenir cette complexité dans les compilateurs et entretenir la surprise quand les développeurs utilisent [certaines suites de caractères](http://stackoverflow.com/questions/9387166).
    
**Question piège :** Qu'affiche ce [code source](http://coliru.stacked-crooked.com/a/35548faf134a2c96) en C++98, C++14 et C++17 ?
    
```cpp
#include <iostream>
int main()
{
  std::cout // La question ?????/
  << "L'univers, la vie et le reste\n"
  << "Indiquer la date au format ??/??/??\n";
}
``` 
    
**Réponse**
    
* En C++98 et C++14, même comportement
    
        $ g++ -std=c++14 main.cpp && ./a.out
        Indiquer la date au format \??
    
* En C++17, l'affichage est très différent
    
        $ g++ -std=c++1z -w main.cpp && ./a.out
        L'univers, la vie et le reste
        Indiquer la date au format ??/??/??
    
**Anecdote :** Les trigraphes auraient pu devenir obsolètes dès C++11 (proposé en 2009). Mais, quelques membres du comité de normalisation du C++, dont IBM et Bloomberg, avaient réussi à ne pas les rendre obsolètes. Pour C++17, les membres ont finalement voté la suppression pure et simple sans étape intermédiaire. IBM a même tenté une dernière [tentative pour conserver les trigraphes](https://wg21.link/n4210) mais sans succès.
    
Cette suppression simplifie grandement les compilateurs car les passes des digraphes et trigraphes ne s'effectuent pas au même moment.
    
Alors que **tripgraphe** signifie comme son nom l'indique *trois caractères*, **digraphe** en C++ est un abus de langage car il intègre le digraphe `%:%:` composé de 4 caractères. Voici ce que dit le standard :
    
> The term “digraph” (token consisting of two characters) is not perfectly descriptive, since one of the alternative preprocessing-tokens is  and of course several primary tokens contain two characters. Nonetheless, those alternative tokens that aren’t lexical keywords are colloquially known as “digraphs”.
    
Dans un sens plus large le standard parle de *Alternative tokens* gérant de la même façon les digraphes et quelques autres mots-clés. Voici ce qui en reste pour C++17 :
    
Caractère primaire | Séquence alternative
-------------------|---------------------
`<%`               | `{`
`%>`               | `}`
`<:`               | `[`
`:>`               | `]`
`%:`               | `#`
`%:%:`             | `##`
`and`              | `&&`
`bitor`            | &#124;
`or`               | &#124;&#124;
`xor`              | `^`
`compl`            | `~`
`bitand`           | `&`
`and_eq`           | `&=`
`or_eq`            | &#124;=
`xor_eq`           | `^=`
`not`              | `!`
`not_eq`           | `!=`

[[P0001]](https://wg21.link/p0001) Mot-clé `register`
----------------------------------------------------------------------------
    
Historiquement, le mot-clé [`register`](http://en.cppreference.com/w/c/keyword/register) force l'utilisation d'un registre du processeur. Cela permettait de gagner en performance en indiquant au compilateur quelles variables à garder dans un registre (à l'époque les compilateurs n'étaient pas très futés).
    
```c
// ERREUR Interdit sur les variables globales
register int g = 0;
    
int main()
{
  register int r = 0; // OK
    
  // ERREUR Une variable register n'a pas d'adresse
  // Mais GCC et Clang le tolère.
  register int *pointeur = &r;
    
  register int tableau[1]; // Comportement indéfini
}
``` 
    
Le mot-clé `register` est déprécié depuis C++11. À l'époque, les contraintes de ce mot-clé (pas de pointeur...) ont été conservées pour la compatibilité avec le C, en particulier avec les arguments des fonctions. Pourtant, son usage n’est pas pertinent en C++ :  redondant avec d’autres fonctionnalités et ses restrictions ne peuvent être facilement transcrites en C++. Plutôt que d’essayer de résoudre les différences avec le C, le standard fait de `register` un mot-clé réservé non utilisé. Espérons qu'un usage futur lui soit trouvé...

[[P0002]](https://wg21.link/p0002) Incrémentation sur les booléens
-----------------------------------------------------------------------------
    
Dans les temps anciens, le type `bool` n’existait pas. Les entiers étaient utilisés pour cet usage avec `#define FALSE 0` et `#define TRUE !0` (souvent égal à `1`). C'est à dire **zéro pour faux** et **toutes les autres valeurs pour vrai**.
    
La création du type `bool` avec le C++ avait nécessité de garder une comptabilité avec le vieux code : l'incrémentation avait été autorisée mais pas la décrémentation.
    
```cpp
bool b = aimes_tu_cpp17();
--b; // Erreur depuis C++98
++b; // Erreur depuis C++17
```

Exemple final
=============


Donc en C++17 nous pourrons écrire :

```cpp
#include <array>

struct Truc
{
  bool  b = false;      
  float f = 0xA.Bp3f; // hexa
};

int main (int argc, 
    [[maybe_unused]] char* argv[])
{
  // Déduction array<int,4>
  std::array tableau {1,2,3,argc};
   
  // lambda constexpr
  auto f = [](){ return Truc(); };

  if constexpr (auto [x,y]=f(); x)
    return y + tableau[1] * argc;
  else
    return y - tableau[2] * argc;
}
```



Alors, chères lectrices et chers lecteurs de *LinuxFr.org* ?
Séduits ? Conquis ? Impatients de coder en C++17 ?
La tentation est grande d’épater ses collègues avec du code qu’ils ne comprennent plus… non ?


Concours
========
    
Proposer dans les commentaires un code source utilisant le maximum des nouveautés du C++17 et pouvant faire croire aux développeurs ne lisant pas *LinuxFr.org* que ce n'est pas du C++.
    
Les vainqueurs recevront des petits cadeaux (goodies, autocollant...) sur le stand *LinuxFr.org* du [Paris Open Source Summit](https://linuxfr.org/sections/paris-open-source-summit) les 16 et 17 novembre. Possibilité de les envoyer par courrier ~~électronique~~ postal ;-)

Appel à participation
======
    
La précédente dépêche a reçu [227 commentaires](https://linuxfr.org/news/c-17-genese-d-une-version-mineure#droit-dauteur-licences-remerciements), soit un volume dix fois supérieur à la dépêche elle-même. Tous ces commentaires cachent tout de même quelques joyeux [trolls](https://fr.wikipedia.org/wiki/Troll_%28Internet%29) velus !

Quand on pense à toute l'énergie dépensée et toutes les heures consacrées à rédiger ces 227 commentaires ! Avec le recul nous aurions pu concentré tout cet investissement dans une dépêche collaborative du style « *Aujourd'hui, est-il pertinent de choisir le C++ pour une nouvelle application ?* »

Mais il n'est jamais trop tard ! Aussi nous proposons-vous de rédiger la dépêche « *Faut-il continuer à apprendre le C++ ?* » Les nombreux commentaires de la dépêche précédente mériterai d'y être copiés. Malheureusement, ceux-ci sont rarement sous licence compatible CC-BY-SA-4.0. Ceci est donc un appel à tous leurs auteurs de les copier dans cette dépêche afin de la nourrir. Ainsi, nous pourrons les structurer et proposer des réponses concises, claires et utiles à tous.
    
Merci et à vos claviers ! ;-)

[![Panneau Troll barré](https://upload.wikimedia.org/wikipedia/commons/e/ea/DoNotFeedTroll.svg)](https://commons.wikimedia.org/wiki/File:DoNotFeedTroll.svg) | [![Panneau Please Do Not Feed the Trolls](https://upload.wikimedia.org/wikipedia/commons/1/19/Trolls.jpg)](https://commons.wikimedia.org/wiki/File:Trolls.jpg)
----|----

La suite
========
    
Nous venons de découvrir les nombreuses évolutions au niveau du langage, le cœur du C++. La dépêche suivante nous emmènera au niveau de la bibliothèque standard. À suivre...
