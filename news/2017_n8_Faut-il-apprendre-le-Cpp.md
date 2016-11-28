Faut-il continuer à apprendre le C++
====================================

Origine de cette dépêche
------------------------

La dépêche [*C++17, Genèse d'une version mineure*](https://linuxfr.org/news/c-17-genese-d-une-version-mineure) a reçu [227 commentaires](https://linuxfr.org/news/c-17-genese-d-une-version-mineure#droit-dauteur-licences-remerciements) représentant un volume dix fois supérieur à la dépêche elle-même. Et ces commentaires, très souvent bien écris, nourissent des [trolls](https://fr.wikipedia.org/wiki/Troll_%28Internet%29) bien velus !

L'idée de créer cette dépêche vient de deux constats :
    
1. L'énergie dépensée et les nombreuses heures consacrées à rédiger ces 227 commentaires est phénoménale ;
2. Par contre, la lecture de tous ces commentaires est laborieuse.

Avec le recul, nous aurions pu concentrer tout cet investissement dans une dépêche collaborative du style *« Aujourd'hui, est-il pertinent de choisir le C++ pour une nouvelle application ? »* afin de structurer et consolider tous les arguments dispersés au fil des commentaires.

Objectif de cette dépêche
-------------------------

Cette dépêche propose un sujet bien plus large *« Faut-il continuer à apprendre le C++ ? »*. Et nous avons besoin des nombreux commentaires de qualité de la dépêche [*C++17, Genèse d'une version mineure*](https://linuxfr.org/news/c-17-genese-d-une-version-mineure) méritent d'y être copiés/améliorés/fusionnées. Malheureusement, ceux-ci sont rarement sous licence compatible CC-BY-SA-4.0.

L'objectif de cette dépêche est donc un appel à tous leurs auteurs de ces commentaires afin de copier les commentaires ici. Ainsi, nous pourrons les structurer/consolider/capitaliser et proposer des points de vue concis, clairs et utils à tous.


Le C++ en bref
--------------

Le C++ est un vieux langage (bientôt 40 ans) hérité du langage C avec lequel il entretient une compatibilité. 
De tout ce long historique, le C++ a évolué du mieux possible entre paradigmes de programmation et nouveaux besoins.
Au final, sa syntaxe évolue lentement, est complexe, bourrée de subtilités et lente à compiler.

Mais c'est aussi un langage permettant des optimisations de folie *(costless abstraction)*.
Le C++ est utilisé au quotidien, ne serait-ce que la plupart des environnements graphiques et des navigateurs web (pour flaner sur *LinuxFr.org*). Et le C++ continuera pour encore de nombreuses années à être utilisé en production, notamment pour les applications critiques. 

Le C++ n'est pas mourrant. Au contraire, le C++ connait un vif intérêt depuis C++11.
De plus en plus de personnes s'investissent à améliorer davantage ce langage, comme sur la vitesse de compilation qui devrait être grandement améliorée pour C++20.

Alors, faut-il tout effacer et recommencer un nouveau langage qui par *design* prend en compte les contraintes de concurrence (multi-core, NUMA) et de monté en charge *(scalability)* ? Des langages de programmation tentent d'obtenir des performances similaires avec une syntaxe expressive et concise.

La puissance du C++
-------------------

Les points positifs qui démarquent le C++ sont sa programmation générique et sa méta-programmation qui permettent d'avoir des abstractions sans pénalités de performance. Si on ne profite pas de ces fonctionnalités, vaut mieux utiliser un autre langage.



Les alternatives
----------------

* Rust
* Go
* Dart
* Elixir
* Phoenix
* Pony
* D
* ...

Critères pour adopter un nouveau langage
----------------------------------------


Mais pour qu'un langage soit adopter plusieurs ingrédients sont nécessaires :

* Un gage de pérennité ;
* Facile à débogage (déverminage) ;
* Une communauté, des meetups, des entreprises ;
* Une galaxie de sites webs, d'outils diverses, des bibliothèques, des tutoriels...

Sur ce terrain, le C++ est bien doté avec de très nombreux outils, bibliothèques et communautés.


Popularité du C++ 
-----------------

Et toi, chère lectrice, cher lecteur, penses-tu que les nouvelles fonctionnalités du C++ ne font que compliquer inutilement le langage le plus complexe que l'humanité ait inventé ?
Ou au contraire, es-tu persuadé.e que grâce à ces évolutions, le C++ va progresser dans le classement du _TIOBE Index_ et garder loin derrière des prétendants comme ~~[D](https://fr.wikipedia.org/wiki/D_(langage)),~~ [Dart](https://fr.wikipedia.org/wiki/Dart_(langage_informatique)), [Nim](https://fr.wikipedia.org/wiki/Nim_(langage)), [Rust](https://fr.wikipedia.org/wiki/Rust_(langage)) ou [Pony](http://www.ponylang.org/) ?

![Indice TIOBE de popularité des langages de programmation, la courbe en vert clair représente l'inexorable descente du C++ qui reste quand même en troisième place derrière Java et C, mais devant Python et C#](http://cdn.edureka.co/blog/wp-content/uploads/2016/06/TIOBE-index-2016.png)

    TODO mettre à jour le graphique


à intégrer :
* http://langpop.corger.nl/
* http://pypl.github.io/PYPL.html
* https://github.com/showcases/programming-languages
* http://www.informit.com/articles/article.aspx?p=2472981
* http://redmonk.com/sogrady/2016/07/20/language-rankings-6-16/




Questions
---------

* Faut-il débuter un logiciel prévu en C++ ?
* Est-il pertinent d'apprendre le C++ aujourd'hui ?



