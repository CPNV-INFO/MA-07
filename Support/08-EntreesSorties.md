# Les entrées/sorties des processus

Chaque processus possède 3 flux standards qu'il utilise pour communiquer en général avec l'utilisateur :

- l'**entrée standard** nommée **stdin** (*identifiant 0*) : il s'agit par défaut du clavier 
- la **sortie standard** nommée **stdout** (*identifiant 1*) : il s'agit par défaut de l'écran 
- la **sortie d'erreur** standard nommée **stderr** (*identifiant 2*) : il s'agit par défaut de l'écran 

Ces flux peuvent être redirigés afin que le processus interagisse avec un autre au lieu d'interagir avec l'utilisateur.

## Rediriger la sortie standard

Quand on exécute une commande, le shell affiche le résultat sur la console de sortie (l'écran par défaut). On peut rediriger cette sortie vers un fichier en utilisant le signe **>**.

Exemple :

        $ ls > resultat
        --> Si le fichier existe déjà, il est écrasé.

## Concaténation

Au lieu de créer un fichier, il est possible d'ajouter les sorties d'un processus à un fichier existant en utilisant le double signe **>>**.

Exemple :
    
        $ ls >> resultat
        --> Si le fichier résultat existe déjà, les affichages sont concaténés.

## Syntaxe complète

En fait, les signes **>** peuvent être précédés de l'identifiant du flux à rediriger. Pour la sortie standard, on peut donc utiliser les syntaxes suivantes :

        $ ls 1> resultat
        $ ls 1>> resultat
        --> Ce qui revient au même que les deux premiers exemples ci-dessus

## Rediriger la sortie d'erreur standard

La redirection du flux de sortie d'erreur standard utilise les même signes, mais précédés de l'identifiant du flux : *2*.

Exemples :

        $ ls 2> erreurs
        $ ls 2>> erreurs

## Rediriger l'entrée standard

Rediriger l'entrée standard permet d'entrer des données provenant d'un fichier au lieu du clavier.

Exemple :

        $ cat < mon_fichier.txt

## /dev/null

*/dev/null* est un fichier spécial des systèmes d'exploitation Unix.

Ce pseudo-périphérique (device, en anglais) sert à rediriger un contenu dont on n'a pas besoin, et qui ne doit pas être sauvegardé ni affiché à l'écran. Toute information envoyée vers ce « périphérique » est automatiquement détruite.

Ce périphérique est appelé null et il est situé dans le répertoire */dev* où sont répertoriés les périphériques. On envoie donc ce qu'on ne veut pas garder vers ce */dev/null*.

Exemple :

Voici un exemple qu'un utilisateur de système basé sur Unix peut utiliser. Cette ligne de commande affiche tous les dossiers et fichiers du système mais va générer des erreurs sur les dossiers ou fichiers sur lesquels il n'aura pas les droits d'accès. Ce script va alors rediriger *stderr (2)* vers le pseudo périphérique */dev/null* inhibant ainsi l'affichage de celles-ci.

        $ find / 2> /dev/null

## Le pipe (un tube)

Redirige la sortie d'une commande vers l'entrée d'une autre commande. Il s'agit donc d'une chaîne de redirection entre deux processus qui ne passe pas par un fichier, mais par une zone mémoire du système.

Exemples :

        $ du | sort -rn 
        --> Afficher la taille des fichiers et répertoires
            et les trier du plus grand au plus petit :

        $ du | sort -rn | more
        --> Même résultat, mais affiché page par page
 
        $ ls -1 /usr/bin | wc -l
        --> Connaître le nombre de fichiers du répertoire /usr/bin
            L'option -1 de la commande ls affiche un fichier 
            ou répertoire par ligne. La commande wc (word count)
            avec l'option -l (line) compte le nombre de lignes.

