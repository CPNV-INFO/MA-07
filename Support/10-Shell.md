# Le Shell

## history

La commande **history** est une commande *POSIX* (commune à toutes les distributions type Unix) qui permet de remonter dans les commandes que nous avons passées.

Il vous arrive probablement souvent de remonter vos commandes pour les réexecuter avec le **UP** (flèche du haut) de votre clavier, vous faites ainsi défiler l'ensemble des commande que vous avez exécutées. Cela est possible grâce à *history*. En effet, quand vous passez une commande, celle-ci est stockée dans un fichier du nom de *.historyb* du répertoire *home/$User*. Si l'utilisateur *cpnv* tape les commandes *ls* et *cd /*, celles-ci seront stockées dans le fichier */home/cpnv/.history* et quand *cpnv* voudra remonter dans ses commandes, c'est le processus et le fichier *.history* qui l'aideront.

Tapez la commande suivante pour voir vos dernières commandes passées:

        $ history

Les commandes que vous verrez seront alors uniquement celles de l'utilisateur avec lequel vous êtes connecté. Pour voir les commandes d'un autre utilisateur, il faut aller ouvrir le fichier *.history* de son répertoire, dans une architecture de droit normale, vous n'y serez bien sur pas autorisé (mis à part si vous êtes root).

## Le nombre d'entrées

Il faut savoir qu'*history* garde les *1000 commandes* (change selon les version et les distributions) les plus récentes et commence à effacer les plus anciennes une fois que le nombres maximum est dépassé.

Il est possible d'agrandir le nombre de commande stocké mais cela risque de ralentir votre shell.

Pour voir le nombre de commande qu'history peut stocker, entrez la commande:

        $ echo $HISTSIZE

Pour changer ce nombre à 300 (par exemple):

        $ export HISTSIZE=300

## Effacer ses traces

Pour vider votre fichier *.history* afin que root ou un utilisateur avec certains privilèges ne puisse plus voir les commandes que vous avez entrées, utilisez la commande:

        $ history -c

Un autre moyen est de supprimer le fichier *.history* dans votre répertoire */home/user*. Il faut savoir que sous Linux, quand vous mettez un *.* devant un fichier, cela le rend invisible. Cela explique pourquoi un simple *ls* n'affiche pas ce fichier, il faut utiliser *ls -a*.

## Utilisations supplémentaires

*history* permet comme je vous l'ai dit de remonter dans les commandes que vous avez entrées. Quelques raccourcis sont disponibles en plus du simple **UP** ou **DOWN** pour naviguer dans ses précédentes commandes. Cette commande permet de remonter dans ses commandes de manière plus rapide:

        $ !n -3

Par exemple avec *-3* pour retrouver l'avant avant avant dernière commande tapée. Il est ainsi possible de remonter jusqu'à $HISTSIZE commande:

        $ !n 3

A l'inverse, sans le *-*, on retrouve la troisième commande tapée. Cela perd de son intérêt quand nous avons tapé beaucoup de commandes car elles s'effacent une fois que l'HISTSIZE est dépassée.

La commande suivante permet de trouver les commandes contenant un mot précis, par exemple pour retrouver les commandes qui contiennent le mot “doc” nous entrerons:

        $ !?doc?

## alias

Certaines commandes récurrentes sous Linux peuvent être longues et préter à des erreurs de saisie. Pour cela il existe la possibilité de créer des *alias de commandes* qui sont des raccourcis vers des commandes plus complexes et/ou plus grande.

## Utilisation

Il est par exemple possible de remplacer la commande suivante :

        # /etc/init.d/networking restart

par

        # rn

Pour Restart Network par exemple, le nom de la commande alias est totalement libre. Il doit bien sur être plus cours ou plus explicite que la commande auquel il se substitue.

## Création

La création d'un *alias* est assez simple. Il faut utiliser la commande *alias* comme suivant :

        # alias rn='/etc/init.d/networking restart'

Il faut savoir qu'un alias s'efface lors du redémarrage. Pour parer à ce problème et faire en sorte que l'alias existe toujours après un redémarrage, il faut mettre la commande précédente dans le fichier *.bashrc* de votre utilisateur. Par exemple pour root :

        # nano /root/.bashrc

Il faut ensuite recharger notre shell :

        # source ~/.bashrc

Il est également possible de voir tous les alias créés avec la commande alias :

        # alias

## Supprimer un alias

Pour supprimer un *alias*, utilisez la commande *unalias* suivi de l'alias que vous désirez supprimer.

        # unalias rn

## PATH

*PATH* est une variable d'environnement. Pour afficher le contenu d'une variable d'environnement, on utilise la commande *echo* :

        $ echo $PATH

La variable *PATH* contient la liste de tous les répertoires dans lesquels le système va chercher les exécutables des commandes que vous tapez au prompt, séparés par des *:* . Par exemple, le répertoire */bin/* contient les commandes Unix de base, et vous pouvez vérifier qu'il est bien dans le *PATH*.

La commande *printenv* affichent les noms et les valeurs de toutes les variables d'environnement définies.

Pour modifier le *PATH*, éditez le fichier de configuration *~/.profile* et ajoutez à la fin du fichier

        PATH="rep_chemin:$PATH"
        --> Remplacer rep_chemin par le nom de répertoire à rajouter

