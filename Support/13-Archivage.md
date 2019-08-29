# Archivage

**tar** (*tape archiver*) est un outil très puissant pour la manipulation d'archives sous les systèmes Unix et les dérivés dont Linux. Il ne compresse pas les fichiers, mais les concatène au sein d'une seule et même archive. La majorité des programmes Linux utilisent ce système d'archivage.

## Installation

Le programme *tar* est disponible par défaut sous Debian. Il fait partie de l'installation minimale.

Pour tous les formats à base de *tar*, vous verrez que les options de tar sont les mêmes :

- c : créer l'archive  
- x : extraire l'archive  
- f : utiliser le fichier donné en paramètre  
- v : activer le mode « verbeux » (bavard, afficher ce qu'il fait).  

Puis selon la compression souhaitée :

- z : ajouter la compression Gzip  
- j : ajouter la compression Bzip2  
- J : ajoute la compression Lzma  

## Utilisation en archivage simple

Utilisation tar seul : concaténation de fichiers

Création d'une archive, archivage de plusieurs fichiers :

        tar -cvf archive.tar fichierarchive1 fichierarchive2...

De même pour un dossier :

        tar -cvf archivedossier.tar dossier/

Pour l'extraction :

        tar -xvf archive.tar -C dossier

on remarque ici l'utilisation de trois options :

*v* pour un affichage des actions, mode verbeux  
*f* pour indiquer que l'on va utiliser un fichier ( on précise son nom ici : archivedossier.tar )  
*C* pour indiquer le dossier de destination de l'extraction  

## Utilisation avec compression

Il est possible d'utiliser tar pour l'archivage et la compression de fichiers. Dans ce cas, il fait appel à d'autres utilitaires comme *Bzip2*, *Gzip*, *Gunzip*. L'archivage se fait alors en deux temps, d'abord la concaténation des fichiers en un seul puis la compression du tout.


## Compression avec gzip (.tar.gz)

Création

        tar -zcvf votre_archive.tar.gz votre_dossier/

Extraction

        tar -zxvf votre_archive.tar.gz

## Compression avec Bzip2 (.tar.bz2)

Remarques : Bzip2 crée des fichiers beaucoup plus petits que Gzip, mais utilise plus de ressources processeur surtout pour compresser.

Création

        tar -jcvf votre_archive.tar.bz2 votre_dossier/

Extraction

        tar -jxvf votre_archive.tar.bz2

## Compression avec Lzma (.tar.xz)

Ces archives sont des archives Tar compressées avec Lzma, un utilitaire de compression libre parmi les plus puissants: c'est la même méthode de compression que celle utilisée par 7zip.

Pour utiliser le format « .xz », installez le paquet xz-utils.

Création

        tar -Jcvf votre_archive.tar.xz votre_dossier/

Extraction

        tar -Jxvf votre_archive.tar.xz

## Archivage incrémentiel

La taille des archives et leur stockage peuvent très vite poser problème. Voici un cas d'utilisation illustrant l'utilité de cet archivage. Vous désirez sauvegarder le /home (données des utilisateurs) toutes les semaines sur un second disque dur, tout en gardant les données antérieures. Vous avez en tout 50 Go de données et le second disque dur fait 500Go. 10% de ces données changent toutes les semaines (5Go). Dans le cas d'une sauvegarde complète, chaque archive fait 50Go, votre disque serait rempli en deux mois.

Nous remarquons que si 10% de ces données changent toutes les semaines, 90% sont identiques et ne nécessitent pas d'être sauvegardées à chaque fois. Il nous faut donc sauvegarder uniquement les nouvelles données en utilisant la sauvegarde incrémentielle. La première sauvegarde est complète, la suivante copie uniquement les nouveaux fichiers et ainsi de suite. Vous gardez ainsi chaque sauvegarde dans l'état à différentes dates.

## Utilisation de l'archivage incrémentiel

Créer la première sauvegarde (sauvegarde complète) :

        tar --create --file=archive.1.tar  
        --listed-incremental=/save/save.list /home

Seconde sauvegarde (incrémentée avec uniquement les fichiers ayant changé) :

        tar --create --file=archive.2.tar  
        --listed-incremental=/save/save.list /home

Restauration :

        tar --extract --listed-incremental=/dev/null  
        --file archive.1.tar
        tar --extract --listed-incremental=/dev/null 
        --file archive.2.tar 

Utiliser la date pour incrémenter le numéro :

        tar --create --file=/save/archive.`date --rfc-3339=date`.tar 
        --listed-incremental=/save/archive.list /home

