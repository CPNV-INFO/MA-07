# Arborescence

## cd (change directory)

**cd** (abréviation de l'anglais change directory), est une commande informatique disponible dans les interfaces en ligne de commande pour changer de répertoire courant.

**cd** est un appel système qui modifie l'attribut **current working directory** du processus qui l'invoque, cette fonction n'est pas un programme à part, et elle est intégrée à l'interpréteur de commandes.

On spécifie comme premier paramètre le répertoire où l'on désire aller :

        $ cd <répertoire>

Lorsque le répertoire n'est pas spécifié, le répertoire personnel de l'utilisateur qui a lancé la commande est choisi.

En pratique, en utilisant **-** (moins) comme répertoire, cela a pour effet d'aller dans le répertoire où l'on se trouvait avant (un peu comme le bouton précédent d'un gestionnaire de fichiers). Le shell utilise en fait de façon transparente les variables d'environnement **PWD** (contenant le répertoire courant) et **OLDPWD** (contenant le répertoire précédent). Ainsi, lorsque l'on fait un **cd -**, le contenu de ces deux variables est échangé.

Lorsque l'on désire aller dans le répertoire parent, on spécifie le répertoire fictif .. (deux points).

        $ cd ..

## mkdir (make directory)

**mkdir** est une commande Unix permettant de créer des répertoires. **mkdir** est l'abréviation de *make directory* (termes anglais signifiant « créer répertoire »).

Voici par exemple comment créer le dossier "Linux" à l'emplacement courant:

        $ mkdir Linux

Une option particulièrement utile de **mkdir** est *-p* (parent). Cette option permet de créer un ensemble de dossier plutôt qu'un dossier seul.

Par exemple, si on veut créer la hiérarchie de dossier "dir1/dir2/dir3", il faut normalement utiliser mkdir trois fois:

        $ mkdir dir1
        $ mkdir dir1/dir2
        $ mkdir dir1/dir2/dir3

L'option -p permet de créer les dossiers intermédiaires:

        $ mkdir -p dir1/dir2/dir3

## ls (list)

**ls** est une commande *POSIX* (abréviation de list en anglais), qui permet d'afficher le contenu d'un répertoire.

Il est possible d'indiquer des arguments permettant d'obtenir plus ou moins d'informations. Par exemple l'argument *-a* permet d'afficher les fichiers dont le nom commence par "." (fichiers « cachés »).

Ces arguments peuvent varier d'une implémentation à l'autre, aussi il convient de vérifier la liste de ceux qui sont acceptés sur un système en regardant la page de manuel associée.

        $ man ls

