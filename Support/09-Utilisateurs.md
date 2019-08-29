# Les utilisateurs

Chaque utilisateur du système dispose de droits différents sur les processus et sur les fichiers. Il existe des utilisateurs humains qui ont un compte sur la machine, et des utilisateurs systèmes qui sont en général des utilisateurs utilisés par certains programmes spécifiques.

## Connaitre la liste des utilisateurs du système

Il y a deux types d'utilisateurs, ceux que l'on appellera *réels* et ceux considérés comme *systèmes*.

## Les utilisateurs systèmes

Les *utilisateurs systèmes* sont ceux employés par des tâches spécifiques (exécution de logiciels ou commandes) régulières qui souvent portent le même nom que l'utilisateur.

## Les utilisateurs réels

Les *utilisateurs réel*s, quant à eux sont associés à des personnes qui se connectent sur la machine soit via une interface graphique ou un accès en ligne de commande (shell) particulier.

## Ajout d'un utilisateur

Cette opération se fait via la commande *adduser*. 

Pour ajouter "toto" on lance donc la commande suivante :

        $ adduser toto
        --> Après plusieurs questions facultatives et la demande 
            d'un mot de passe, l'utilisateur "toto" est créé sur le système.

Par défaut son répertoire utilisateur sera */home/toto* 
Les options par défaut affiliées à un utilisateur lors de sa création sont définies dans le fichier de configuration */etc/adduser.conf* qui est éditable en tant que super-utilisateur.

## Changer d'utilisateur

Losque l'on est connecté à la machine et que l'on souhaite changer d'utilisateur, il suffit de lancer la commande :

        $ su autre_utilisateur
        --> autre_utilisateur est le nom d'un utilisateur existant
            sur le système. Son mot de passe sera alors demandé.

Pour revenir à l'utilisateur précédent il suffira ensuite de lancer la commande :

        $ exit

Pour devenir super-utilisateur, la commande *su* seule suffit.

## Changer le mot de passe d'un utilisateur

Pour modifier le mot de passe d'un utilisateur, on utilise la commande *passwd*.

Après le lancement, le système demandera alors le nouveau mot de passe choisi et sa confirmation. Cette commande lancée seule changera le mot de passe sur compte avec lequel vous êtes connecté.

Pour changer le mot de passe d'un autre utilisateur, exécutez cette commande connecté en *root*

        # passwd toto

## Suppression d'un utilisateur du système

Dans cet exemple, nous allons supprimer le compte *toto* précédemment créé du système.

Avant de supprimer l'utilisateur, il est important de bloquer son compte. On utilise la commande suivante pour ce faire :

        # passwd -l toto

L'utilisateur ne devrait plus pouvoir se connecter (vous pouvez à ce moment sauvegarder sainement le contenu du répertoire /home/toto/ par exemple). On ne peut supprimer un compte de quelqu'un logué sur la machine. On va donc fermer l'ensemble des programmes lancés par cet utilisateur ainsi que sa connexion.

La commande suivante liste les pid de ces programmes :

        # pgrep -u toto

Si elle ne renvoie aucun nombre, cela veut dire que l'utilisateur n'est pas logué sur la machine et qu'il n'a lancé aucun programme.

Si vous souhaitez voir les programmes lancés par l'utilisateur, lancez cette commande :
 
        # ps -fp $(pgrep -u toto)

Si la commande a retourné quelque chose, utilisez les commandes suivantes pour fermer les programmes :

        # killall -KILL -u toto

Sous Debian, la commande *killall* se trouve dans le paquet *psmisc*.

On peut ensuite supprimer l'utilisateur *toto* et son répertoire *home* ainsi que sa boîte email (avec l'option -r) avec la commande userdel :

        # userdel -r toto

Si l'utilisateur a des tâches *CRON* dans son fichier crontab, supprimez-les avec la commande :

        # crontab -r -u toto

## sudo

L'arrivée d'*Ubuntu* a contribué à l'utilisation régulière de la commande **sudo** installée par défaut sur cette distribution. Elle permet de gérer simplement la délégation de droits normalement associés au super-utilisateur (root) du système à d'autres utilisateurs d'une manière simple.

### Installation de sudo

*sudo* n'est pas installé par défaut sur Debian (contrairement à Ubuntu), il est donc nécessaire de l'installer :

        $ su
        # apt-get install sudo

## Configuration minimale de sudo

Pour éditer les autorisations de *sudo*, tout se passe dans le fichier */etc/sudoers*.

On ouvre donc ce fichier afin de l'éditer :

        # visudo

On souhaite qu'un utilisateur dont l'identifiant est *cpnv* puisse avoir accès à l'ensemble des droits root sur le serveur, on ajoute donc la ligne suivante en fin de fichier :

        cpnv      ALL=(ALL:ALL) ALL

Il en sera de même pour chaque utilisateur système auquel on souhaite autoriser ces fonctions. 
Si vous souhaitez affiner les droits d'utilisateurs, vous pouvez vous référer à cette adresse [http://guide.andesi.org/html/ksudo.html](http://guide.andesi.org/html/ksudo.html).

