# Les processus

## Gestionnaire de fenêtres

En système de fenêtrage un *gestionnaire de fenêtres* (« window manager » en anglais) est un logiciel chargé de l'affichage et du placement des fenêtres d'applications. Les plus connus sont ceux utilisé par le système de fenêtrage X (sur les systèmes Unix, Linux et BSD).

Le gestionnaire de fenêtres constitue l'intermédiaire entre le système de fenêtrage et l'environnement graphique.

Ici, on parle plus particulièrement des gestionnaires basés sur le système de fenêtrage X.

Étant lui-même un client sur serveur X, le gestionnaire de fenêtres offre des moyens pour déplacer, redimensionner et icônifier les fenêtres affichées par les autres clients. De plus, il ajoute une décoration aux fenêtres qui consiste souvent en un cadre et une barre de titre. La majorité des gestionnaires sait de plus gérer plusieurs bureaux virtuels et des raccourcis clavier.

## X Window System

*X Window System* ou *X11* ou simplement X est un environnement graphique de type « fenêtré » qui gère l'interaction homme-machine par l'écran, la souris et le clavier de certains ordinateurs en réseau. Il est souvent appelé X Window. C'est le système standard ouvert d'interaction graphique avec l'utilisateur sur les UNIX (Linux, BSD, etc.). Le serveur X est optionnel.

## OpenBox

*Openbox* est un gestionnaire de fenêtres pour le système X Window. Il est distribué sous licence GPL.

*Openbox* est conçu pour être petit, rapide et entièrement compatible avec le ICCCM et le Extended Window Manager Hints (en). Il supporte de nombreuses fonctionnalités comme les menus d'applications ou l'affichage dynamique de différentes informations.

Son principal avantage est son extrême légèreté, qui favorise stabilité et réactivité du système, et pas seulement sur des machines peu puissantes.

Son interface très simple rend son utilisation très facile. Par contre son paramétrage peut demander des compétences minimales en informatique, surtout si on passe directement par les fichiers de configuration et non par des programmes comme obmenu, obconf et lxappearance.

Openbox peut s'utiliser seul, sans environnement de bureau, ou en remplacement du gestionnaire de fenêtres intégré dans un environnement de bureau.

### Installation de OpenBox

        # apt-get install x-window-system-core 
        # apt-get install xdm numlockx xterm xserver-xorg
        # apt-get install openbox
        # apt-get install obconf obmenu

## RunLevel

Le niveau d'exécution (*runlevel*) de Linux contrôle le choix des processus ou services qui sont démarrés automatiquement par le système (ou, plus exactement, par Init). Le niveau d'exécution est désigné par un chiffre de 0 à 6. Les niveaux d'exécution 0, 6 sont réservés respectivement à l'extinction du système, au redémarrage.

Debian définit sept niveaux d'exécution (0-6).

        0      (arrête le système) 
        1 - S  (simple utilisateur / mode minimal)
        2 à 5  (modes multi-utilisateurs)
        6      (redémarre le système). 

L'installation par défaut de Debian ne fait pas de différence entre les niveaux d'exécution de 2 à 5. Vous pouvez les personnaliser à votre guise. Le niveau d'exécution 1 est utilisé pour la maintenance du système. Il lance le minimum de services pour éviter de possibles problèmes.

Votre système démarre au niveau d'exécution spécifié dans */etc/inittab*. 

Par exemple

        id:2:initdefault:
        --> lance le système au niveau d'exécution 2
            par défaut dans Debian

Les niveaux d'exécution peuvent être modifiés manuellement en modifiant les scripts de contrôle dans */etc/init.d* et les liens symboliques dans */etc/rc0.d ... /etc/rc6.d*. Veuillez lire attentivement les instructions contenues dans les références ci-dessous. Comme la modification manuelle est une tâche fastidieuse, on vous recommande de vous servir d'un éditeur de niveau d'exécution. Avec Debian, installez le paquet *sysv-rc-conf*. Vous pouvez ensuite modifier les niveaux d'exécution en ouvrant simplement un terminal en tant que super-utilisateur puis en exécutant le programme *sysv-rc-conf*.

Vous pouvez aussi changer le niveau d'exécution pendant l'exécution. Utilisez seulement les niveaux 1 à 5. Utilisez la commande *init [runlevel]* ou *telinit [runlevel]*. La seconde est préférable.

