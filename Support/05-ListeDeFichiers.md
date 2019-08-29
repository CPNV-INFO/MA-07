# Liste de fichiers

## touch

En fait, il n'existe aucune commande spécialement faite pour créer un fichier vide sous Linux (ce n'est pas très utile). En général, on se contente d'ouvrir un éditeur de texte et d'enregistrer, ce qui provoque la création d'un fichier.

La commande **touch** est à la base faite pour modifier la date de dernière modification d'un fichier. D'où son nom : on « touche » le fichier pour faire croire à l'ordinateur qu'on vient de le modifier alors que l'on n'a rien changé. Ça peut se révéler utile dans certains cas précis qu'on ne verra pas ici.

L'intérêt de touch pour nous, c'est que si le fichier n'existe pas, il sera créé ! On peut donc aussi utiliser touch pour créer des fichiers, même s'il n'a pas vraiment été fait pour ça à la base.

Pour créer un fichier vide, il vous suffit de taper la commande suivantes'il n'existe pas déjà. Dans le cas contraire, elle modifiera la date d'accès du fichier. : 

        $ touch fichier

Vous pouvez également utiliser la commande : 

        $ > fichier

## cp (copy)

La commande **cp** sert à copier des  fichiers (et eventuellement des répertoires). On peut aussi bien copier un fichier donné vers une destination précise que copier un ensemble de fichiers dans un répertoire.

Si le dernier argument correspond à un nom de répertoire, **cp** copie dans ce répertoire chaque fichier indiqué en conservant le même nom.

Sinon, s'il n'y a que deux fichiers indiqués, il copie le premier sur le second.

## mv (move)

La commande **mv** est un raccourci pour "move" (déplacer). Elle est utilisée pour déplacer/renommer un fichier d'un répertoire à un autre. La commande **mv** est différente de la commande **cp** puisqu'elle retire le fichier entièrement de la source et le déplace au répertoire spécifique, tandis que la commande **cp** copie simplement le contenu d'un fichier à un autre.

- Pour renommer/déplacer un fichier

        $ mv file1.txt file2.txt 
        
- Pour déplacer un répertoire

        $ mv dir tmp

- Pour déplacer de multiples fichiers/Plus de fichiers dans un autre répertoire 

        $ mv file1.txt tmp/file2.txt newdir

## more

La commande **more** permet d'afficher le contenu d'un fichier texte page par page dans la console.

