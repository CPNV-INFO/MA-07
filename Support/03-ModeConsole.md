# Mode console

## Notions de base

Une fois que la procédure d'installation est terminée, vous arrivez à l'invite de connexion :

        Debian GNU/Linux
        Debian tty1
        debian login :

Pour vous connecter, vous avez le choix entre :

**a. Vous connecter en tant que root**

Tapez **root**, appuyez sur **Entrée**, ensuite tapez le mot de passe root que vous avez défini pendant la procédure d'installation et appuyez sur **Entrée**. Quand vous êtes ainsi connecté en tant que root, vous avez *tous les droits sur le système*

        debian:~#

**b. Vous connecter en tant que simple utilisateur**

Tapez le **nom d'utilisateur** que vous avez défini pendant la procédure d'installation, appuyez sur **Entrée**, ensuite tapez le mot de passe associé à cet utilisateur et appuyez sur **Entrée**. Quand vous êtes ainsi connecté en tant que simple utilisateur, vous n'avez que des droits limités sur le système.

        cpnv@debian:~$

>**Attention** L'utilisation du compte root est réservée à la modification de la configuration du système, à l'installation de paquets et aux rares tâches qui nécessitent les droits de root. Pour toutes les autres tâches, il faut utiliser un compte utilisateur. En effet, l'utilisation du compte root est dangereuse : une fausse manipulation peut détruire le système, ce qui est impossible en tant que simple utilisateur !

## Convention

Dans toute la suite de cette formation, nous adopterons la convention suivante

les commandes qui devront être exécutées en tant que root auront un prompt **#**

        # commande_à_exécuter

les commandes qui devront être exécutées en tant que simple utilisateur auront un prompt **$**

        $ commande_à_exécuter

## Se déconnecter

Pour vous déconnecter, et retourner à l'invite de connexion, vous pouvez saisir la commande **logout** puis valider avec **Entrée**, ou bien utiliser la combinaison de touches **Ctrl+d**.

## su

Cette commande sert à changer d'utilisateur, après avoir rentré le bon mot de passe, bien sûr !

- **su** permet de devenir root.

- **su cpnv** permet de devenir l'utilisateur *cpnv*.

**Note** Le passage de root à un simple utilisateur par la commande **su cpnv** se fait sans rentrer le mot de passe de l'utilisateur *cpnv*.

##  man

Depuis la version 9 "Strech" de Debian, nous devons installer le "man" avec la commande suivante :

        # apt-get install man

man est une commande disponible sur les systèmes d'exploitation de type Unix. Elle permet de visionner le manuel d'une commande.

## Utilisation

Elle doit être utilisée sous la forme suivante :

        man [-s<section>] <nom_de_commande>

Par exemple, pour voir le manuel de la commande *ls*, il faut taper

        $ man ls

Pour naviguer dans une page, il faut généralement utiliser les flèches vers le haut et vers le bas ou les touches page down et page up, ou encore la touche d'espacement, selon le pager utilisé. On sort généralement d'une page avec la touche Q, mais, avec certaines versions, il faut appuyer sur la touche d'espacement jusqu'à ce qu'on arrive à la fin de la page de manuel.

## Sections

Les pages du manuel Unix sont divisées en plusieurs sections. Par exemple, sous Linux, on retrouve les sections suivantes :

- Commandes utilisateur (Section 1)
- Appels système (Section 2)
- Fonctions de bibliothèque (Section 3)
- Fichiers spéciaux (Section 4)
- Formats de fichier (Section 5)
- Jeux (Section 6)
- Divers (Section 7)
- Administration système (Section 8)
- Interface du noyau Linux (Section 9)

Chaque section possède une page d'introduction qui présente la section, disponible en tapant

        $ man <section> intro

Pour plus d'information sur man, il est possible de regarder la page man de man, avec la commande

        $ man man
