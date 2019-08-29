# Installation

## Debian ? Qu'est-ce que c'est ?

**Debian** est une des plus anciennes distributions de Linux et fut créé en **1993**. Elle utilise Linux en tant que noyau de manière similaire aux autres distributions.

**Debian est aujourd'hui la seule distribution majeure non commerciale**.

Debian est une organisation à but non lucratif constituée d'un millier de développeurs bénévoles répartis sur toute la planète. Elle est dirigée par un projet leader élu par les développeurs. Les décisions se prennent au consensus ou par vote.

Les autres distributions GNU/Linux majeures sont des sociétés commerciales, ce qui ne les empêche pas de produire des logiciels libres !

Debian se distingue aussi par son attachement très fort à la philosophie du logiciel libre.

## La stabilité

Debian GNU/Linux est réputé pour être un système d'exploitation très stable. Avant chaque nouvelle version, le système est longuement testé et il ne sort qu'une fois que tous les bogues connus ont été corrigés. Debian s'est doté d'un **Bug Tracking System (BTS)** très performant et très pratique qui permet aux développeurs d'avoir un retour d'expérience instructif des utilisateurs, ce qui les aide à corriger les bogues rapidement.

## Les architectures

Debian GNU/Linux est disponible sous 12 architectures, dont Intel 32 et 64 bits, PowerPC (les anciens Macintosh) et Sparc (les stations Sun).

## Les différentes versions de Debian

La première version de Debian, la 0.01 est sortie en 1993. Puis les versions s'enchaînent, avec des noms inspirés du film Toy Story.

Debian est toujours disponible en trois versions (trois branches) qui sont :

1. **stable** : version figée où les seules mises à jour sont des correctifs de sécurité.
2. **testing** : future version stable où seuls les paquets suffisamment matures peuvent rentrer.
3. **unstable** : il s'agit d'une version en constante évolution, alimentée sans fin par de nouveaux paquets ou de mises à jour de paquets déjà existants (on parle de rolling release).

## Installation de Debian

Je vous propose de commencer par installer une version stable. Il faut savoir que vous pouvez passer facilement d'une version donnée à une version supérieure, mais l'inverse est plus difficile. Donc si vous installez une stable, vous pourrez passer facilement en testing ou en Sid (unstable) ; mais vous ne pourrez que difficilement revenir en stable ensuite.

>**Remarque :** Veuillez remplacer la variable entre crochet par le contenu idoine. (ex. *[Module]*-debian )

## Préparation de Vmware

1. Téléchargez sur votre disque dur l'image du CD d'installation stable de DEBIAN [^stable]

[^stable]: [https://www.debian.org/releases/stable/](https://www.debian.org/releases/stable/)


2. Utilisez VMware pour créer une nouvelle machine virtuelle

  - File → New → Virtual Machine
  - Virtual Machine Configuration → Custom (advanced)
  - Hardware compatibility → Workstation *[dernière version]*
  - Install operating system from → I will install the operating system later
  - Guest Operating System → 2. Linux → Debian *[dernière version]* 64-bit
  - Name → *[Module]*-Debian
  - Number of processors → 1
  - Memory → 512 MB
  - Network Connection → Use network address translation (NAT)
  - I/O Controller Types → LSI Logic (Recommended)
  - Virtual Disk Type → SCSI (Recommended)
  - Disk → Create a new virtual disk
  - Disk Size → Maximum disk size (in GB) → 20.0
  - Disk File → *[Module]*-Debian.vmdk
  - Customize Hardware
    - Enlever → USB Controller
    - Enlever → Sound Card
    - Enlever → Printer
    - New CD/DVD (IDE) → Use ISO image → *[image ISO d'installation de DEBIAN]*

## Boot sur le support

Configurez votre ordinateur pour qu'il démarre sur le support d'installation. Au moment du boot, vous avez accès à une ligne de commande permettant de lancer l'installation en sélectionnant **Install** et en appuyant sur **Entrée**.

## Choix des langues et pays

Trois écrans vous permettent de choisir :

- La langue utilisée par le processus d'installation. Naviguez avec les flèches, sélectionnez **Français** et appuyez sur **Entrée** pour continuer. Dans la suite, c'est le français qui sera utilisé.
- Selon la langue initiale choisie, Debian vous demande ensuite dans quel pays vous vous situez. C'est utile, car c'est ainsi que sont positionnées les variables locales : format de date, d'heure, encodage des caractères, formats numériques et monétaires, etc. Sélectionnez **Suisse** et appuyez sur **Entrée** pour continuer.
- Enfin, choisissez votre type de clavier. Pour la Suisse, c'est **Suisse romand**

## Paramètres du réseau

Les trois étapes suivantes concernent les informations réseaux de base. Si l'installateur n'a pas réussi à configurer la carte réseau par DHCP, il vous demandera de saisir les informations de base :

- Adresse IP
- Masque de sous réseau
- Passerelle par défaut
- DNS

Puis vous devez saisir un nom d'hôte (le nom de la machine sur le réseau) et le nom du domaine.

- Saisissez le nom d'hôte **[Module]-debian** et appuyez sur **Entrée** pour continuer.
- Comme votre machine n'appartient à auccn domaine, laissez le champ **Domaine** vide et appuyez sur **Entrée** pour continuer.

## Comptes root et utilisateurs

Vous devez maintenant saisir le mot de passe de l'administrateur root de la machine. Celui-ci vous sera demandé deux fois pour confirmation. Ne le perdez pas ! Il n'y a aucun moyen de retrouver le mot de passe d'origine. Debian vous prévient et peut même refuser un mot de passe s'il est trop simple.

Vous devez ensuite créer au moins un utilisateur simple. Vous devrez saisir le nom complet de la personne et Debian vous propose un login. Saisissez ensuite les mots de passe associés. Vous pouvez créer plusieurs utilisateurs, mais rien ne vous empêche de faire ceci après l'installation.

- Créez l'utilisateur **cpnv** avec comme mot de passe **cpnv**

## Partitionner les disques

De manière simpliste, vous avez le choix entre trois principales méthodes pour partitionner vos disques

- Une méthode manuelle
- Une méthode assistée (voire automatique) en utilisant le partitionnement classique
- Une méthode assistée proposant le LVM[^LVM]

[^LVM]: LVM (Logical Volume Manager, ou gestionnaire de volumes logiques en français)

La méthode assistée classique dans le cas d'une nouvelle installation donne des bons résultats. Si vous réinstallez une machine, ou que vous installez Debian sur une machine disposant déjà de partitions contenant les dossiers personnels par exemple, passez par un partitionnement personnalisé.

Le LVM consiste à regrouper des disques physiques ou partitions (appelés volumes physiques) en un seul grand espace (appelé groupe de volumes) dans lequel vous pouvez découper des espaces logiques à volonté (appelés volumes logiques), les agrandir, les réduire, etc.

>*Cependant vous devriez envisager la solution LVM dans le cadre d'un serveur d'entreprise ou si vous pensez rajouter à terme des disques dans votre machine pour rajouter de l'espace de stockage. Le LVM apporte une très grande souplesse.*

- Sélectionnez **Manuel** et appuyez sur **Entrée** pour continuer.
- Sélectionnez le disque **(sda)** et appuyez sur **Entrée** pour continuer.
- Fait-il créer une nouvelle table des partitions sur ce disque ? Sélectionnez **OUI** et appuyez sur **Entrée** pour continuer.

Linux utilise deux types de systèmes de fichiers :

- **Swap** qui sert de mémoire virtuelle, qui est utilisée quand la mémoire vive est pleine
- **Ext4** qui sert à stocker les fichiers et les répertoires (il existe de nombreuses alternatives à Ext4 : Ext3, Ext2, ReiserFS, xfs, jfs…).

## Explication de l'arborescence des fichiers

Voici pour information quelques explications sur les différents dossiers
indispensables dans / :

- **/bin** : Contient les programmes systèmes importants
- **/boot** : Les fichiers utiles au démarrage du système
- **/dev** : Contient des fichiers factices permettant de communiquer avec vos périphériques
- **/etc** : Ici se trouve la plupart des fichiers de configuration du système
- **/home** : Contient les dossiers personnels des utilisateurs. Chacun y possède un dossier à son nom avec ses fichiers personnels
- **/lib** : Contient les librairies –bibliothèques – utiles au système
- **/media** : Les dossiers contenus correspondent aux accès de montage des périphériques de stockage
- **/opt** : A un peu la même fonction que /usr, sauf que certains l'utilisent pour les programmes qu'ils compilent eux-même et qui ne sont logiquement pas aussi intégrés qu'un logiciel disponible dans les sources de mises à jour
- **/proc** : Ce dossier contient des fichiers et dossiers virtuels qui correspondent à l'état du système en temps réel : programmes ( processus ) lancés, occupation mémoire, RAM disponible, etc..
- **/root** : C'est le /home de l'administrateur ! Ce dernier est séparé pour des questions de sécurité.
- **/sbin** : A un peu la même fonction que /bin, sauf que tous les programmes issus ne sont accessibles qu'à l'administrateur.
- **/tmp** : Comme son nom l'indique, ici sont stockés les fichiers temporaires utiles aux programmes en cours d'exécution. Ce dossier est vidé à chaque redémarrage.
- **/usr** : Dossier important, contenant tous les programmes et les bibliothèques installés.
- **/var** : Dossier contenant tout ce qui est variable au système. Par exemple, les fameux fichiers « log » enregistrant ce qui se passe sur votre système, utiles quand quelque chose ne fonctionne plus par exemple – contenus dans /var/log/ .

## Création de la partition SWAP

Traditionnellement, on crée une partition avec un système de fichiers de type Swap de taille double ou triple de la taille de la mémoire vive quand celle-ci est inférieure à 256 Mo ou égale à la taille de la mémoire vive quand celle-ci est supérieure ou égale à 256 Mo.

Cette partition est appelée partition de swap ou d'échange.

- Sélectionnez **Espace libre** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Créer une nouvelle partition** et appuyez sur **Entrée** pour continuer.
- Entrez la valeur **512M** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Primaire** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Début** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Utiliser comme** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **espace d'échange (swap)** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Fin du paramétrage de cette partition** et appuyez sur **Entrée** pour continuer.

## Création de la partition / (racine)

La partition racine / est la partition qui contiendra le système et tous ses composants (programmes, paramètres systèmes, etc.)

- Sélectionnez **Espace libre** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Créer une nouvelle partition** et appuyez sur **Entrée** pour continuer.
- Entrez la valeur **10 GB** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Primaire** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Début** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Utiliser comme** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **système de fichiers journalisés ext4** et appuyez sur **Entrée** pour continuer.
- Contrôlez la valeur **Point de montage** soit égale à **/**
- Sélectionnez **Indicateur d'amorçage** et appuyez sur **Entrée**. La valeur va passer à présent.
- Sélectionnez **Fin du paramétrage de cette partition** et appuyez sur **Entrée** pour continuer.

## Création de la partition /home

La partition /home est la partition qui va contenir les données des utilisateurs.

Créer une partition pour le répertoire des utilisateurs est la méthode la plus pertinente pour un poste de travail. Elle permet de réinstaller facilement un autre système (mise à jour ou réinstallation complète) sans casser les données personnelles. La nouvelle distribution ainsi installée pourra réutiliser la partition montée sur /home et ainsi récupérer les données.

- Sélectionnez **Espace libre** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Créer une nouvelle partition** et appuyez sur **Entrée** pour continuer.
- Laissez la valeur proposée et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Primaire** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **Utiliser comme** et appuyez sur **Entrée** pour continuer.
- Sélectionnez **système de fichiers journalisés ext4** et appuyez sur **Entrée** pour continuer.
- Contrôlez la valeur **Point de montage** soit égale à **/home**
- Sélectionnez **Fin du paramétrage de cette partition** et appuyez sur **Entrée** pour continuer.

Ne soyez pas surpris par les numéros de partitions. Très souvent la seule partition primaire est la racine / tandis que toutes les autres sont des partitions logiques au sein d'une partition étendue, et Linux numérote les primaires de 1 à 4 (une partition étendue est une partition primaire) tandis que la numérotation des partitions logiques débute à 5.

Si ce schéma de partitionnement vous convient, validez. L'écran suivant vous donne un récapitulatif que vous devez de nouveau valider.

*Attention ! Le partitionnement est suivi de l'écriture des systèmes de fichiers sur les partitions concernées. Cette opération est est destructive.*

- Sélectionnez **Terminer le partitionnement et appliquer les changements** et appuyez sur **Entrée** pour continuer.
- Faut-il appliquer les changements sur les disques ? Sélectionnez **Oui** et appuyez sur **Entrée** pour continuer.

Une fois les changements validés, une barre de progression vous informe de l'état du partitionnement et de l'écriture des nouveaux systèmes de fichiers. Debian va ensuite monter ces systèmes pour l'installation.

## Installation
L'installation se déroule en plusieurs étapes

Debian procède tout d'abord à l'installation du système de base : c'est l'ensemble des logiciels communs à toute installation de Debian tels que la bibliothèque standard, les utilitaires GNU et les outils Debian indispensables. Cette étape ne nécessite aucune intervention de votre part et prend quelques minutes.

Installation des éléments de base. Soit téléchargés ou contenus sur le support d'installation, les éléments de base sont recopiés sur votre disque. Ils se composent des packages essentiels.

Vous choisissez ensuite un miroir : c'est le lieu (sur Internet) où sont présents les dépôts de logiciels Debian. Si vous n'utilisez pas de dépôts, Debian se base uniquement sur le contenu du support d'installation. S'il s'agit d'un DVD il n'y a pas de problèmes, mais si vous utilisez comme ici un CD d'installation réseau, seule la base est présente et rien d'autre.

- Faut-il analyser un autre CD ou DVD? Sélectionnez **Non** et appuyez sur **Entrée** pour continuer.
- Faut-il continuer sans miroir sur le réseau ? Sélectionnez **Oui** et appuyez sur **Entrée** pour continuer. Nous le configurons plus tard.

L'installateur charge les listes de paquets, puis vous demande si vous souhaitez participer aux statistiques d'utilisation des paquets.

>Souhaitez-vous participer à l'étude statistique ? Sélectionnez **Non** et appuyez sur **Entrée** pour continuer. Nous le configurons plus tard.

Sélection des logiciels :
À l'aide de la **barre d'espace** désélectionnez. Appuyez sur **Entrée** pour continuer

Ensuite, il procède à l'installation de nombreux paquets de base. Vous n'avez rien à faire pendant le déroulement de cette étape, qui prend quelques bonnes minutes.

## Fin d'installation et redémarrage

Pour préparer le premier démarrage sous Linux, il faut rendre votre nouveau système d'exploitation démarrable directement depuis le disque dur. Pour cela, le programme GRUB va être installé dans le MBR (master boot record) de votre disque dur. C'est ce programe qui va vous proposer de choisir un des multiples systèmes d'exploitation installés sur votre ordinateur (et par la suite il vous permettra aussi de choisir la version du noyau Linux avec laquelle vous allez démarrer votre système Debian).

C'est très simple ici, car c'est le seul système installé. Sachez que le chargeur de démarrage écrase celui précédemment installé, mais que vous pouvez parfaitement utiliser grub pour démarrer n'importe quel système y compris Windows.

>Installer le programme de démarrage GRUB ? Sélectionnez **Oui** et sélectionnez **/dev/sda**

Il n'y a plus qu'à rebooter. 

Voici ce que les ingénieurs en électronique appellent le test de la fumée : démarrer un système pour la première fois.

Après une installation standard, le premier écran que vous verrez au démarrage du système est le menu du programme d'amorçage GRUB .

Le premier choix est votre nouveau système Debian.

## Site miroir de Debian

Les différents paquets proposés à l'installation sont placés sur des serveurs appelés les **dépôts**, et c'est en définissant à quels dépôts votre système aura accès que vous délimiterez la diversité et les versions des programmes disponibles à l'installation sur votre Debian.

Cette liste de dépôts auquel votre système a accès est contenue dans un fichier essentiel à toute Debian : le fichier sources.list (/etc/apt/sources.list), ou dans le dossier /etc/apt/sources.list.d/ sous forme de plusieurs fichiers.

Debian est distribuée (copiée) sur des centaines de serveurs sur la Toile. L'utilisation d'un serveur proche devrait augmenter la vitesse de téléchargement et également réduire la charge de nos serveurs centraux et de la Toile tout entière.

        # nano /etc/apt/sources.list

Commentez toutes les lignes du fichier en rajoutant le caractère **#** au début de la ligne et rajouter la ligne suivant à la fin du fichier.

        deb http://debian.ethz.ch/debian stable main contrib non-free

Exécutez la commande suivante afin de mettre à jour votre nouveau dépôt ainsi que votre distribution.

        # apt-get update && apt-get upgrade

## Gestion des paquets

Un paquet est un logiciel ou une partie d'un logiciel, qui a été préparé dans un format spécial, afin de faciliter sa recherche, la consultation d'informations à son sujet, ainsi que son installation et sa désinstallation.

Ce paquet prend la forme d'un fichier avec un nom particulier : nom-du-logiciel_numéro-de-version_nom-de-l'architecture.deb (par exemple le fichier apache_1.3.24_i386.deb contient la version 1.3.24 du programme Apache pour processeurs Intel). Ce fichier contient les binaires du programme ainsi qu'un certain nombre d'en-têtes.

Le système de gestion des paquets de Debian est très performant et très facile à utiliser. Grâce à lui, les logiciels s'installent, se retirent et peuvent être mis à jour très facilement.

**APT** est le *Advanced Package Tool* et fournit le programmme **apt-get**. Apt-get fournit un moyen simple pour installer des paquets depuis la ligne de commande. Apt-get travaille avec le nom du paquet et peut seulement installer les archives .deb depuis une source indiqué dans */etc/apt/sources.list*.

Les options les plus courantes de apt-get :

- Pour mettre à jour la liste des paquets connus par votre système

        # apt-get update

- Pour mettre à jour tous les paquets de votre système, sans installer de paquets supplémentaires ou en supprimer :

        # apt-get upgrade

- Pour installer le paquet lynx et toutes ses dépendances

        # apt-get install lynx

- Pour supprimer le paquet lynx de votre système

        # apt-get remove lynx

- Pour supprimer le paquet lynx et ses fichiers de configuration de votre système

        # apt-get --purge remove lynx

- Pour mettre à jour votre système entier, en permettant si nécessaire l'installation de paquets supplémentaires ou la suppression de paquets

        # apt-get dist-upgrade

*Notez que vous devez être authentifié en tant que root pour exécuter toutes commandes qui modifient le système de paquets.*

Notez que **apt-get** installe par défaut les paquets recommandés et constitue le programme de référence pour la gestion des paquets en console, leur installation mais aussi la mise à jour du système.

La suite d'outils **apt** inclut aussi le programme **apt-cache** pour questionner les listes de paquet.

## Installation du SSH

**SSH** signifie **Secure SHell**. C'est un protocole qui permet de faire des connexions sécurisées (i.e. chiffrées) entre un serveur et un client SSH.

Installer un serveur SSH permet aux utilisateurs d'accéder au système à distance, en rentrant leur login et leur mot de passe (ou avec un mécanisme de clefs). Cela signifie aussi qu'un pirate peut essayer d'avoir un compte sur le système (pour accéder à des fichiers sur le système ou pour utiliser le système comme une passerelle pour attaquer d'autres systèmes) en essayant plein de mots de passes différents pour un même login (il peut le faire de manière automatique en s'aidant d'un dictionnaire électronique). On appelle ça une attaque en force brute.

Il y a donc trois contraintes majeures pour garder un système sécurisé après avoir installé un serveur SSH :

- avoir un serveur SSH à jour au niveau de la sécurité, ce qui doit être le cas si vous faites consciencieusement les mises à jour de sécurité en suivant la procédure Debian

- que les mots de passes de TOUS les utilisateurs soient suffisamment complexes pour résister à une attaque en force brute

- surveiller les connexions en lisant régulièrement le fichier de log */var/log/auth.log*

Pour pouvoir vous connecter à distance, vous pouvez maintenant installer le serveur SSH :

        # apt-get install openssh-server

L'installation comporte une étape de génération des clefs de chiffrement. Finalement, le serveur SSH se lance.

Notez l'adresse IP de votre serveur à l'aide de la commande

       # ip addr

Vous pouvez à présent utiliser un client SSH depuis votre poste de travail (Ex. PuTTY[^PuTTY], Cygwin[^Cygwin]) pour accéder à votre serveur et ouvrir une session à distance.

[^PuTTY]: [http://www.putty.org/](http://www.putty.org/)
[^Cygwin]: [https://cygwin.com/](https://cygwin.com/)


