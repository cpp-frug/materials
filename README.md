Partage de contenus C++ francophones
------------------------------------

Ce dépôt Git permet de partager tout type d'information concernant le C++ et la galaxie qui tourne autour.

* [Images et dessins](images/README.md) ;
* [Les dépêches C++](news/README.md) ;
* Merci de proposer d'autres types de contenus...


Comment contribuer ?
--------------------

1. Cloner ce dépôt et pousser vos contributions *(pull request)* ;
2. Devenir membre de ce dépôt Git (demander les droits en écriture via la page des [*"issues"*](https://github.com/cpp-frug/materials/issues) en expliquant ses motivations) ;
3. Utiliser les outils de GitHub pour annoter des fichiers, des commits ou en utilisant la fonctionnalité des [*"issues"*](https://github.com/cpp-frug/materials/issues).


Quel types de contenu ?
-----------------------

- Permettre la réutilisation (utiliser une licence libre, CC-BY-SA, copyleft...) ;
- Les documents textes de préférence au format Markdown (les fichier `.tex .rst .ascidoc .pdf ...` sont acceptés, mais il est également possible de les convertir en Markdown avec `pandoc` par exemple et de fornir un CSS si besoin) ;
- En langue française de préférence (les autres langues ne sont pas interdites, mais C++FRUG essaye de promouvoir la communauté C++ francophone) ;
- Les images sont les bienvenus, de préférence au format SVG si c'est du dessin (clipart), sinon au format JPEG (et WebP) ;
- Les `git clone` n'appréciant pas les fichier trop volumineux, merci de ne pas ajouter une vidéo de 2Go par exemple (à moins que cela ne pose pas de problème technique et donc merci d'expliquer comment gérer les fichiers volumineux avec GitHub...).


Les fichiers SVG
----------------

Les logiciels d'édition d'image SVG (e.g. inkscape) produisent des fichiers SVG verbeux dont de nombreuses balises et attrubuts ne sont pas nécessaires à l'affichage. Le script `scour` permet de nettoyer et réduire les fichiers SVG (https://github.com/scour-project/scour).

### Installation

    sudo apt install python-pip
    sudo pip install scour

### Utilisation

    scour gros.svg resultat.svg --create-groups --enable-viewboxing --strip-xml-space --enable-id-stripping --shorten-ids --protect-ids-noninkscape --error-on-flowtext 

Le détail des options est disponible avec `scour --help`.

### Pas de SVG compressé

La compression `gzip` d'un fichier SVG peut se faire de deux façons : (1) entre le serveur web et le navigateur ; (2) directement dans le dépôt Git (avec par exemple la commande `gzip --keep --no-name --best image.svg ; mv image.svg.gz image.svgz`). Nous déconseillons cette seconde façon pour plusieurs raisons :

1. Les navigateurs Firefox et Chrome/Chromium ne supportent pas le format SVGZ ;
2. Git compresse déjà très bien les fichiers textes (contrairement aux fichiers binaires) - SVG étant un fichier texte XML ;
3. Le format texte permet d'avantage de possibilités (édition des fichiers via l'interface web, diff de deux versions...) ;
4. Les fichiers SVG contiennent des `<metadata>` pouvant contenir les information de droit d'auteur et licence d'utilisation et sont plus faciles à lire en mode non compressé.

### Copyright et licence

Utiliser la balise `<metadata>` pour indiquer le copyright et la licence :

```xml
 <title>Bjarne Stroustrup s'impatiente pour l'intégration des Concepts au standard C++</title>
 <metadata  xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
  <rdf:RDF  xmlns:cc="http://creativecommons.org/ns#">
   <cc:Work xmlns:dc="http://purl.org/dc/elements/1.1/"
    rdf:about="https://github.com/cpp-frug/materials/blob/gh-pages/images/cpp-concepts-bjarne-original.svg">
    <dc:format>image/svg+xml</dc:format>
    <dc:type rdf:resource="http://purl.org/dc/dcmitype/StillImage"/>
    <dc:creator>
     <cc:Agent>
      <dc:title>Oliver H</dc:title>
     </cc:Agent>
    </dc:creator>
    <dc:language>fr</dc:language>
    <dc:date>2016</dc:date>
    <cc:license  rdf:resource="http://creativecommons.org/licenses/by/3.0/"/>
   </cc:Work>
   <cc:License   rdf:about="http://creativecommons.org/licenses/by/3.0/">
    <cc:permits  rdf:resource="http://creativecommons.org/ns#Reproduction"/>
    <cc:permits  rdf:resource="http://creativecommons.org/ns#Distribution"/>
    <cc:requires rdf:resource="http://creativecommons.org/ns#Notice"/>
    <cc:requires rdf:resource="http://creativecommons.org/ns#Attribution"/>
    <cc:permits  rdf:resource="http://creativecommons.org/ns#DerivativeWorks"/>
   </cc:License>
  </rdf:RDF>
 </metadata>
```

Licence
-------

Ce présent fichier Markdown est sous licence [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/deed.fr). Voir la liste des contributeur sur l'[historique](https://github.com/cpp-frug/materials/commits/gh-pages/README.md).

Les différents documents présents dans ce dépôt Git sont également sous licence libre.  
Se référer au document en question pour connaître la licence précise (souvent CC-BY-SA).

Quelques idées de réutilisations du contenu de ce dépôt Git :

* des présentation (Meetup) ;
* des dépêches ;
* de la formation ;
* des articles Wikipédia ;
* des articles sur son blog...
 
 
Liste des tâches
----------------

* Les différentes tâches sont gérées sur la page [Issues](https://github.com/cpp-frug/materials/issues).
