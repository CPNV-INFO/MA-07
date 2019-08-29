# Les permissions

Les **permissions UNIX** constituent un système simple de définition des droits d'accès aux ressources, représentées par des fichiers disponibles sur un système informatique.

## Notion d'utilisateur (user)

Toute entité (personne physique ou programme particulier) devant interagir avec un système UNIX est authentifiée sur cet ordinateur par un utilisateur ou **user**. Ceci permet d'identifier un acteur sur un système UNIX. Un utilisateur est reconnu par un nom unique et un numéro unique (la correspondance nom/numéro est stockée dans le fichier **/etc/passwd**).

Tous les utilisateurs UNIX n'ont pas les mêmes droits d'accès à l'ordinateur (ils ne peuvent pas tous faire la même chose), et ceci simplement pour des raisons de sécurité et d'administration. 

Sur tout système UNIX, il y a un **super-utilisateur**, généralement appelé **root**, qui a tous les pouvoirs. Il peut accéder librement à toutes les ressources de l'ordinateur, y compris à la place d'un autre utilisateur, c'est-à-dire sous son identité. En général, du moins sur les systèmes de production, seul l'administrateur système possède le mot de passe root. L'utilisateur root porte le numéro 0.

## Groupe

Un utilisateur UNIX appartient à un ou plusieurs **groupes**. Les groupes servent à rassembler des utilisateurs afin de leur attribuer des droits communs.

## Propriété

Tout fichier UNIX possède un **propriétaire**. Au départ, c'est l'utilisateur qui a créé le fichier mais "root" peut le donner à un autre utilisateur. Seul le propriétaire du fichier et le super utilisateur (root) peuvent changer les droits.

Un fichier UNIX appartient aussi à un groupe.

## Droits d'accès à un fichier

À chaque fichier est associée une **liste de permissions** (ACL), qui déterminent ce que chaque utilisateur et groupe a le droit de faire du fichier.

Sous UNIX **les répertoires sont aussi des fichiers**. Les droits sur les répertoires (mais aussi les périphériques, etc.) fonctionnent exactement de la même façon que sur des fichiers ordinaires.

## Permissions du système de fichiers

Les permissions du système de fichiers d'un système basé sur UNIX sont définies pour trois catégories d'utilisateurs :

- **U** l'utilisateur qui possède le fichier 
- **G** les autres utilisateurs du groupe à qui appartient le fichier 
- **O** tous les autres utilisateurs dont on parle aussi en tant que « monde entier » ou « tout le monde »

Pour les fichiers, chaque permission correspondante permet les actions suivantes :

- **r** la permission en lecture permet à son propriétaire de voir le contenu du fichier 
- **w** la permission en écriture permet à son propriétaire de modifier le fichier
- **x** la permission d'exécution permet à son propriétaire de lancer le fichier comme une commande

Pour les répertoires, chaque permission correspondante permet les actions suivantes :

- **r** la permission en lecture permet à son propriétaire d'afficher le contenu du répertoire 
- **w** la permission en écriture permet à son propriétaire d'ajouter ou supprimer des fichiers de ce répertoire
- **x** la permission d'exécution permet à son propriétaire d'accéder aux fichiers du répertoire

*La permission en exécution sur un répertoire ne signifie pas uniquement l'autorisation de lire des fichiers dans ce répertoire mais aussi l'autorisation de voir leurs attributs, tels que leur taille et l'heure de modification.*

*ls* est utilisé pour afficher les informations de permissions (et davantage) des fichiers et répertoires. Lorsque cette commande est passée avec l'option *-l*, elle affiche les informations suivantes dans l'ordre donné :

- Type de fichier (premier caractère) 
- Autorisation d'accès au fichier (neuf caractères, constitués de trois caractères pour l'utilisateur, le groupe et « les autres », dans cet ordre) 
- Nombre de liens physiques vers le fichier 
- Nom de l'utilisateur propriétaire du fichier 
- Nom du groupe à qui appartient le fichier 
- Taille du fichier en caractères (octets) 
- Date et heure du fichier (mtime)
- Nom du fichier

## Représentation des droits

Cet ensemble de 3 droits sur 3 entités se représente généralement de la façon suivante : on écrit côte à côte les droits r, w puis x respectivement pour le propriétaire (U), le groupe (G) et les autres utilisateurs (O). 

Les codes U, G et O (U comme user, G comme group et O comme others) sont utilisés par les commandes UNIX qui permettent d'attribuer les droits et l'appartenance des fichiers. Lorsqu'un flag est attribué à une entité, on écrit ce flag (r, w ou x), et lorsqu'il n'est pas attribué, on écrit un '-'. 

    rwx r-x r--
    \ / \ / \ /
     v   v   v
     |   |   droits des autres utilisateurs (o)   
     |   droits des utilisateurs appartenant au groupe (g)
     droits du propriétaire (u)
 
signifie que le propriétaire peut lire, écrire et exécuter le fichier, mais que les utilisateurs du groupe attribué au fichier ne peuvent que le lire et l'exécuter, et enfin que les autres utilisateurs ne peuvent que lire le fichier.

Une autre manière de représenter ces droits est sous forme binaire grâce à une clef numérique fondée sur la correspondance entre un nombre décimal et son expression binaire :

    0 = 000
    1 = 001
    2 = 010
    3 = 011
    4 = 100
    5 = 101
    6 = 110
    7 = 111

À l'expression binaire en trois caractères sont associés les 3 types de droits (r w x) ; il suffit donc de déclarer pour chacune des catégories d'utilisateur (user, group, others) un chiffre entre 0 et 7 auquel correspond une séquence de droits d'accès. Par exemple :

    777 donne 111 111 111 soit rwx rwx  rwx
    605 donne 110 000 101 soit rw- ---  r-x
    644 donne 110 100 100 soit rw- r--  r--
    666 donne 110 110 110 soit rw- rw-  rw-

Une astuce permet d'associer rapidement une valeur décimale à la séquence de droits souhaitée. Il suffit d'attribuer les valeurs suivantes pour chaque type de droit :

    lecture   (r) correspond à 4
    écriture  (w) correspond à 2
    exécution (x) correspond à 1
    
Puis on additionne ces valeurs selon qu'on veuille ou non attribuer le droit en correspondant.

Ainsi, rwx « vaut » 7 (4+2+1), r-x « vaut » 5 (4+1) et r-- « vaut » 4. Les droits complets (rwxr-xr--) sont donc équivalent à 754. Une manière directe d'attribuer les droits est de les écrire sous cette forme et d'utiliser le code à 3 chiffres résultant avec chmod (voir ci-après).

## chown (change owner)

La commande **chown** (*change owner*, changer le propriétaire) permet de changer le propriétaire du fichier. Seuls le super-utilisateur ou le propriétaire actuel d'un fichier peut utiliser chown. La commande s'utilise de la façon suivante :

    $ chown toto mon_fichier

Le fichier *mon_fichier* appartient maintenant à l'utilisateur *toto*.

chown permet aussi de changer en une seule commande le propriétaire et le groupe du fichier :

    $ chown toto:lesPotes mon_fichier

Le fichier *mon_fichier1* appartient alors à l'utilisateur *toto* et au groupe *lesPotes*.

## chgrp (change group)

La commande **chgrp** (pour *change group*) permet de changer le groupe auquel appartient le fichier. Tous les membres de ce groupe seront concernés par les permissions du groupe de la 2ème série de rwx. Encore une fois, seuls le super-utilisateur ou le propriétaire actuel d'un fichier peut utiliser chgrp (un membre du groupe ne peut pas changer le groupe propriétaire). La commande s'utilise de la façon suivante :

    $ chgrp mesPotes mon_fichier

Le fichier *mon_fichier* appartient maintenant au groupe *mesPotes*. Tous les membres du groupe *mesPotes* auront accès à ce fichier selon les permissions du groupe.

## chmod (change mode)

L'outil **chmod** (*change mode*, changer les permissions) permet de modifier les permissions sur un fichier.

Il peut s'employer de deux façons :

- soit en ajoutant ou en retirant des permissions à une ou plusieurs catégories d'utilisateurs à l'aide des symboles *r w et x* de manière "relative" 
- soit en précisant les permissions de manière octale

    Les deux méthodes sont équivalentes, elles affectent toutes deux les permissions de la même manière.

### La manière "symbolique"

De cette façon, on va choisir :

À qui s'applique le changement

- **u** (user, utilisateur) représente la catégorie "propriétaire" 
- **g** (group, groupe) représente la catégorie "groupe propriétaire" 
- **o** (others, autres) représente la catégorie "reste du monde" 
- **a** (all, tous) représente l'ensemble des trois catégories 

La modification que l'on veut faire

- \+ : ajouter 
- \- : supprimer 
- = : force la valeur 

Le droit que l'on veut modifier

- **r** : read --> lecture
- **w** : write --> écriture
- **x** : execute --> exécution

Exemple :

    $ chmod o-w mon_fichier
    --> Enlève le droit d'écriture pour les autres.

    $ chmod a+x mon_fichier
    --> Ajoute le droit d'exécution à tout le monde.

    $ chmod a=r mon_fichier
    --> Alloue pour tous le monde le droit en lecture seul.

On peut aussi combiner plusieurs actions en même temps :

    $ chmod u+rwx,g+rx-w,o+r-wx mon_fichier
    --> Ajoute la permission de lecture, d'écriture 
        et d'exécution sur le fichier pour le propriétaire
    --> Ajoute la permission de lecture et d'exécution au
        groupe propriétaire, on retire la permission d'écriture
    --> Ajoute la permission de lecture aux autres, on retire
        la permission d'écriture et d'exécution

### La manière "octale"

En octal, chaque « groupement » de droits (pour user, group et other) sera représenté par un chiffre et à chaque droit correspond une valeur :

    r = 2^2 --> 4
    w = 2^1 --> 2
    x = 2^0 --> 1
    - = 0

Par exemple

    Pour rwx, on aura : 4+2+1 --> 7
    Pour rw-, on aura : 4+2+0 --> 6
    Pour r--, on aura : 4+0+0 --> 4
    
Reprenons le répertoire *Documents*. Ses permissions sont :

    drwxr-x---
    rwx        r-x        ---
    7(4+2+1)   5(4+0+1)   0(0+0+0)
    En octal, on aura 750
  
Pour mettre ces permissions sur le répertoire on taperait donc la commande :

    $ chmod 750 Documents

### Remarques importantes

- Un programme ne peut être exécuté que si le fichier exécutable correspondant possède le droit d'exécution dans la catégorie à laquelle appartient l'utilisateur. 
- On ne peut accéder à un fichier que si les répertoires successifs constitutifs du chemin absolu de ce fichier possèdent le droit en exécution. 
- Pour pouvoir lister les fichiers d'un répertoire, ce dernier doit être accessible en lecture.
- Le droit en exécution n'a aucune incidence sur un fichier non exécutable. 
- Un script (c'est-à-dire un fichier texte contenant des commandes du Shell) doit avoir les droits en lecture et en exécution pour pouvoir être interprété et exécuté par le Shell.

## Masque de protection des fichiers (umask)

Le masque de protection de fichier permet de définir les droits par défaut de tout fichier créé.

Ce masque se comporte comme un filtre et utilise la notation numérique. On parle de filtre car il ne contient pas la série des 3 chiffres octaux correspondants aux droits à allouer aux fichiers, mais celle correspondant aux droits à ne pas allouer.

Le système Unix affecte à un fichier les droits globaux résultant de la soustraction des droits maxima *777* par le masque de protection.

Exemple : si le masque de protection vaut *037* alors *740 (=777-037)* seront les droits alloués à tout nouveau fichier.

La commande permettant de définir un nouveau masque de protection est umask.

    $ umask 037
   
Exemple de calcul

          777 = rwx rwx rwx = 111 111 111
        - 037 = --- -wx rwx = 000 011 111
        = 740 = rwx r-- --- = 111 100 000

D'après cet exemple, tout nouveau fichier aura les droits 740 (rwxr-----) car le masque de protection vaudra 037 (----wxrwx).

Pour connaître la valeur du masque de protection, tapez *umask* sans attribut.

>**Attention** : Lors de la création d'un fichier, même si le masque de protection spécifie le droit en exécution, ce dernier ne sera pas affecté au fichier nouvellement créé mais seulement à un répertoire. Donc, si vous créez un fichier exécutable ou un script il faudra lui rajouter manuellement le droit en exécution.

