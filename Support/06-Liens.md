# Les liens

Les **liens** sont des fichiers spéciaux permettant d'associer plusieurs noms (liens) à un seul et même fichier. Ce dispositif permet d'avoir plusieurs instances d'un même fichier en plusieurs endroits de l'arborescence sans nécessiter de copie, ce qui permet notamment d'assurer un maximum de cohérence et d'économiser de l'espace disque. 

## Les liens symboliques

Les **liens symboliques** représentant des pointeurs virtuels (raccourcis) vers des fichiers réels. En cas de suppression du lien symbolique, le fichier pointé n'est pas supprimé. Les liens symboliques sont créés à l'aide de la commande **ln -s** selon la syntaxe suivante :

        $ ln -s nom-du-fichier-reel nom-du-lien-symbolique

Le principe du **lien symbolique** est que l'on crée un lien vers un autre nom de fichier. On pointe vers le nom de fichier et non vers l'inode directement.

        Fichier2 --> Fichier1 --> Inode

l'avantage des **liens symboliques** est qu'ils fonctionnent aussi sur des répertoires, contrairement aux **liens physiques**.

## Les liens physiques

Les **liens physiques** (aussi appelées liens durs ou en anglais hardlinks) représentent un nom alternatif pour un fichier. Ainsi, lorsqu'un fichier possède deux liens physiques, la suppression de l'un ou l'autre de ces liens n'entraine pas la suppression du fichier. Plus exactement, tant qu'il subsiste au minimum un lien physique, le fichier n'est pas effacé. En contrepartie lorsque l'ensemble des liens physiques d'un même fichier est supprimé le fichier l'est aussi. Il faut noter toutefois qu'il n'est possible de créer des liens physiques qu'au sein d'un seul et même système de fichiers. Les liens physiques sont créés à l'aide de la commande **ln** (sans l'option -s) selon la syntaxe suivante :

        $ ln nom-du-fichier-reel nom-du-lien-physique

Un **lien physique** permet d'avoir deux noms de fichiers qui partagent exactement le même contenu, c'est-à-dire le même **inode**

        Fichier1 --> Inode <-- Fichier2

## Exemple de liens

        $ ln -s fichier3.txt fichier
        $ ln fichier3.txt fichier2
        $ ls -i
        
    1610496 lrwxrwxrwx  1 user user    14 fév 28 14:52 fichier -> fichier3.txt 
    1606777 -rw-r--r--  2 user user  3407 fév 27 12:57 fichier2 
    1606777 -rw-r--r--  2 user user  3407 fév 27 12:57 fichier3.txt
	
- Le lien en dur possède le même numéro d'inode que le fichier original (no d'identification du fichier)
- Le tiret en tête des permissions pour le lien en dur, un «l» pour le lien symbolique
- Le même volume (3407) pour le lien en dur, 14 pour le lien symbolique
- Le même horodatage (date de création du fichier) pour le lien en dur
- Le lien symbolique montre, à la fin de la ligne, où celui-ci pointe
- Le numéro 2 (avant user indique le nombre de noms que le fichier possède)
	
Si on: 
			
- Supprime le fichier original (charlotte3.txt): 
    - le lien symbolique tombe dans le vide (inutilisable)
    - le lien en dur est toujours fonctionnel	
- Déplace l'original: 
	- le lien symbolique tombe dans le vide (inutilisable)
	- le lien en dur fonctionne toujours		
- Met l'original dans un dossier avec des droits interdits: 
	- le lien symbolique ne pourra pas rediriger vers l'original
	- le lien en dur sera accessible

