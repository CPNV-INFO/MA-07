# Présentation de GNU/Linux

## Qu'est-ce que le mouvement GNU ?

En 1984, **Richard Matthew Stallman**, chercheur en informatique du MIT[^MIT] quitte son poste et se consacre à l'écriture d'un système d'exploitation Libre du nom de **GNU**[^GNU].

Il annonce l'année suivante la création de la **FSF**[^FSF] afin de supporter ce projet. C'est durant ces années qu'il écrit ce qui deviendra les préceptes du Logiciel Libre. 

La concrétisation en est la publication en 1989 de la première version de la **licence GPL**[^GPL] qui sera alors le fondement éthique, juridique et politique du mouvement du Libre.

[^MIT]: Le Massachusetts Institute of Technology ou MIT, en français Institut de technologie du Massachusetts, est une institution de recherche et une université américaine, spécialisée dans les domaines de la science et de la technologie.

[^GNU]: Son nom est un acronyme récursif qui signifie en anglais « GNU's Not UNIX » (littéralement, « GNU n'est pas UNIX »).

[^FSF]: Free Software Foundation

[^GPL]: La licence publique générale GNU

# Qu'est-ce qu'un logiciel libre ?

L'expression **Logiciel Libre** fait référence à la liberté pour les utilisateurs d'exécuter, de copier, de distribuer, d'étudier, de modifier et d'améliorer le logiciel. Plus précisément, elle fait référence à quatre types de liberté pour l'utilisateur du logiciel

- **Liberté 0** : La liberté d'exécuter le programme, pour tous les usages.
- **Liberté 1** : La liberté d'étudier le fonctionnement du programme, et de l'adapter à vos besoins.
- **Liberté 2** : La liberté de redistribuer des copies, donc d'aider votre voisin.
- **Liberté 3** : La liberté d'améliorer le programme et de publier vos améliorations, pour en faire profiter toute la communauté. 

>Pour répondre aux libertés 1 et 3, l'accès au code source est une condition requise. 

Un programme est un Logiciel Libre si les utilisateurs ont **toutes** ces libertés.

## Linux

Linux est le nom couramment donné à tout **système d'exploitation libre** fonctionnant avec le noyau Linux. C'est une implémentation libre du système **UNIX**[^UNIX] respectant les spécifications POSIX[^POSIX]. Ce système est né de la rencontre entre le mouvement du logiciel libre et le modèle de développement collaboratif et décentralisé via Internet. Son nom vient du créateur du noyau Linux, **Linus Torvalds**.

[^UNIX]: Unix est un système d'exploitation multitâche et multi-utilisateur créé en 1969. Il est fondé sur une approche par laquelle il offre de nombreux petits outils, chacun doté d'une mission spécifique.

[^POSIX]: POSIX est une famille de standards techniques définie depuis 1988 par l'Institute of Electrical and Electronics Engineers (IEEE), et formellement désignée par IEEE 1003. Ces standards ont émergé d'un projet de standardisation des interfaces de programmation des logiciels destinés à fonctionner sur les variantes du système d'exploitation UNIX.

Le système avec toutes ses applications est distribué sous la forme de distributions Linux comme *Ubuntu*, *Debian* ou *CentOS*.

## Philosophie d'Unix

Douglas McIlroy, l'inventeur des tuyaux Unix (Unix pipes en anglais) et l'un des fondateurs de la tradition d'Unix, résume la philosophie comme suit :

Voici la philosophie d'Unix :

- Écrivez des programmes qui effectuent une seule chose et qui le font bien.
- Écrivez des programmes qui collaborent.
- Écrivez des programmes pour gérer des flux de texte [en pratique des flux d'octets], car c'est une interface universelle.

>Ce qui est souvent résumé par : **Ne faire qu'une seule chose, et la faire bien.**

## Historique et genèse de Linux

**Linus B.Torvalds** est à l'origine de ce système d'exploitation entièrement libre. Au début des années 90, il voulait mettre au point son propre système d'exploitation pour son projet de fin d'études. Linus Torvalds avait pour intention de développer une version d'UNIX pouvant être utilisé sur une architecture de type 80386.

Le premier clone d'UNIX fonctionnant sur PC a été *Minix*, écrit par Andrew Tanenbaum, un système d'exploitation minimal pouvant être utilisé sur PC. 

Linus Torvalds décida donc d'étendre les possibilités de Minix, en créant ce qui allait devenir Linux. Amusées par cette initiative, de nombreuses personnes ont contribué à aider Linus Torvalds à réaliser ce système, si bien qu'**en 1991 une première version du système a vu le jour**. C'est en mars 1992 qu'a été diffusée la première version ne comportant quasiment aucun bug. 

## Noyau Linux

Le noyau Linux est un noyau de système d'exploitation de type UNIX. Le noyau Linux est un logiciel libre développé essentiellement en langage C par des centaines de bénévoles et salariés communiquant par Internet.

Ses caractéristiques principales sont d'être **multitâche et multi-utilisateur**. Il respecte les normes *POSIX* ce qui en fait un digne héritier des systèmes *UNIX*.

Si au début de son histoire le développement du noyau Linux était assuré par des développeurs bénévoles, les principaux contributeurs sont aujourd'hui un ensemble d'entreprises, souvent concurrentes, comme RedHat, Novell, IBM ou Intel.

La licence du noyau Linux est la licence publique générale GNU dans sa version 2.

## Définition

**GNU/Linux** est un système d'exploitation complètement Libre et performant. Il est hautement configurable. Il ne dépend pas d'une multinationale. Il est supporté par une grande communauté d'utilisateurs souvent prêts à vous aider. 

Quelque soit votre domaine de compétence, vous pouvez participer à l'amélioration de *GNU/Linux* pour que ce dernier évolue dans votre intérêt.

**Ce n'est pas un simple logiciel gratuit, mais un Logiciel Libre**. Ce qui garantit qu'il restera accessible et gratuit pour tous, sans discrimination.

## Qu'est-ce qu'une distribution ?

En réalité, si on vous livrait le noyau Linux seul, accompagné des outils GNU de base, vous seriez bien avancé : pas d'interface graphique, juste quelques commandes, bref, votre système d'exploitation serait inexploitable.

C'est pour cela qu'existe des distributions Linux qui contiennent le noyau Linux, les outils GNU, plus un ensemble de logiciels qu'elles ont choisi de supporter. Ceux-ci sont testés et compilés pour vous. La plupart d'entre elles contiennent un système d'installation de logiciel simplifié qui leur est propre.

Il existe de nombreuses distributions, chacune ayant ses particularités. Certaines sont dédiées à un usage spécifique (pare-feu, routeur, grappe de calcul, édition multimédia…), d'autres à un matériel spécifique.

Les distributions généralistes destinées au grand public pour un usage en poste de travail (bureautique) sont les plus connues (Debian, Gentoo, Mageia, Red Hat/Fedora, Slackware, SUSE Linux Enterprise/openSUSE, Ubuntu). Le mainteneur de la distribution peut être une entreprise (comme dans le cas de Fedora, RedHat et Ubuntu, Canonical) ou une communauté (comme Debian, Gentoo ou Slackware).

## Les caractéristiques du système
 
Linux est un système d'exploitation proche des systèmes UNIX pouvant être exécuté sur différentes plates-formes matérielles : x86 (c'est-à-dire des plates-formes à base de processeurs Intel, AMD, etc.), Sparc, PowerPC, Alpha, ARM, etc. Ainsi le système Linux peut fonctionner aussi bien sur des ordinateurs personnels que des consoles de jeu ou des assistants personnels ! 

Linux est ainsi un système **multi plate-forme**. Il est également **multi-utilisateurs** (plusieurs personnes peuvent en même temps travailler sur le même ordinateur), mais aussi **multi-tâches** (plusieurs applications peuvent être lancées en même temps sans qu'aucune n'affecte les autres) et **multi-processeurs**. 

>Linux est considéré comme un système fiable, robuste et puissant. Il est d'ailleurs capable de fonctionner avec très peu de ressources sur des ordinateurs bas de gamme très peu puissants.