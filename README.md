## Rummikub

Rummikub est le jeu à réaliser dans ce projet. Nous le codons en C avec la biliothèque SDL2. Pour jouer au Rummikub, il vous faut:
2 à 4 joueurs.
52 tuiles sur lesquelles sont inscrits des chiffres de 1 à 13. Les chiffres peuvent être de couleurs jaune, rouge,
orange ou bleu. Chacune de ces 52 tuiles existent en deux exemplaires.
4 tuiles joker sur lesquelles apparaît le visage d’un bonhomme coloré (un joker orange , jaune , rouge et bleu) . Ces tuiles vous permettront deremplacer n’importe qu’elle autre tuile.
4 chevalets pour poser vos tuiles.Le but du jeu.
Être le premier à poser toutes ses plaques en formant des combinaisons de chiffres de la manière la plus judicieuse.
Pour commencer la partie, chaque joueur pioche 14 tuiles qu’il pose ensuite sur son chevalet.
Afin de déterminer qui commencera, chaque joueur pioche une tuile. C’est celui qui aura le plus grand chiffre qui
débutera.
Pour qu’un joueur puisse débuter, il faut que la ou les combinaisons qu’il dépose sur la table valent 30 points minimum.
Si ce n’est pas le cas, le joueur pioche une tuile et c’est au tour d’un autre joueur.
Il sera peut-être obligé de piocher plusieurs tours avant de pouvoir poser ces tuiles.
Vous allez essayer de vous débarrassez de vos tuiles soit en créant une combinaison, à condition que le nombre de tuile
soit de 3 minimum, soit en complétant ou modifiant les combinaisons déjà posées sur le plateau de jeu.
Vous pouvez aussi utiliser vos tuiles de façons différentes :
• Si un joueur à utiliser un joker dans sa combinaison vous pouvez le récupérer en positionnant la tuile qu’il
remplaçait. ATTENTION le joker doit être utilisé immédiatement dans une autre combinaison.
• Vous pouvez également rajouter une tuile à l’extrémité d’une combinaison de façon à récupérer la tuile qui se
trouve à l’autre extrémité. (Exemple : La suite 234 est posée, positionnez le 1 et ainsi vous pouvez retirer le 4
afin de l’utiliser immédiatement dans une autre combinaison).
• Si vous souhaitez utiliser une tuile déjà positionnée dans une combinaison vous pouvez mais vous devez
absolument la remplacer par une autre tuile.
• Vous pouvez également diviser en deux une suite déjà positionnée. (Exemple : Si la suite 678910 est sur la
table, vous pouvez la séparer en 678 et rajouter le 11 et créer la suite 91011.)
• Si une combinaison comporte plus de 3 tuiles vous pouvez en retirer une afin de l’utilise.
Le joueur qui pose le plus rapidement ses tuiles gagne la partie.
Les autres joueurs doivent donc additionner les points restant sur leur chevalet. Ces points seront des points négatifs. Un
joker qui reste sur votre chevalet vous coûtera 30 points négatifs.

NB : S'il vous plaît ,lisez attentivement le Guide du projet afin de mieux comprendre le dossier project_algo.

 # Guide du projet
 
  Un conseil faite le sur une machine linux , pour ne pas avoir trop de mal . Toutes installation considéré ici sont sur machines sous Unix/linux . 
 
1 - installation de la SDL2:

 Voici la commande d'installation sur linux  :
  sudo apt-get install libsdl2-dev. Pour une machine n'étant pas sous linux, téléchargez une machine virtuelle (virtualbox par exemple), il est cependant possible d'installer la SDL sur un autre système que linux mais c'est complexe. Nous avons essayé de rendre notre projet dynamique, pour qu'il ne soit pas nécessaire d'installer séparément la SDL, mais nous n'avons pas réussi. Dans les améliorations possibles, il serait intéressant de commencer par ce point, plus d'informations sur : https://wiki.libsdl.org/SDL2/Installation.
  
  2 - installation de quelques librairies additionnelles pour la SDL :
  
  L'installation de la SDL_ttf et de la SDL_image n'est pas trop difficile si on a bien compris celle de la SDL. Pour installer la SDL_ttf sur linux, il faut taper la commande suivante : sudo apt-get install  libsdl2-ttf-dev . Pour la sdl_image, la commande est : sudo apt-get install libsdl2-image-dev. La SDL_ttf permet d'écrire du texte sur notre fenêtre et la SDL_image permet d'afficher des images(autres que le format bmp) sur la fenêtre.
  
  NB : Il ne faut pas oublier d'inclure ces bibliothèques dans le fichier include.h qui se trouve dans le fichier include ou bien de les mettre simplement au niveau de l'entête de notre fichier.c, par exemple #include "SDL_ttf.h". On peut installer ces fonctionnalités à partir du site Web de SDL: https://www.libsdl.org/projects/SDL_image/ pour la SDL_image et https://www.libsdl.org/projects/SDL_ttf/ pour la SDL_ttf.
  
  Plus rapide : vous pouvez tout aussi bien tapez la commande suivante  pour tout installer rapidement ,voici la commande : sudo apt-get install libsdl2-dev libsdl2-ttf libsdl2-image-dev . 
  
  
 3 - guide d'utilisation du dossier Rummikub (le dossier principal du projet) : 
 
 Pour commencer , lorsque vous entrez dans le dossier Rummikub, avec un `cd Rummikub` vous verrez 2 dossiers (include et src) et 3 fichiers (makefile, README.md que vous êtes entrain de lire en ce moment, et un fichier pour la licence) .
  - Dans le dossier include se trouvent tous les fichiers d'entêtes du projet notamment , defs.h qui contient toutes les définitions   des constantes écritent dans les fichiers sources , destroy.h qui contient les prototypes des fonctions  pour libération des réssources quant-on quitte la SDL ou l'un de ses composants , include.h est le fichier où est contenu tous les #include du projet , notemment la librairie SDL , stdio etc ... vous remarquerez que dans tous nos fichiers sources du projet( voir project_algo/src) , il y'a un seul chemin qui est : "../include/include.h . Et enfin deux autres fichiers du dossier include , notamment init_draw.h qui contient tous les prototypes des fonctions principales du menu , jusqu'à l'implémentation du Rummikub et le fichier structures.h qui contient toutes les structures du jeu . 
  - Dans le dossier src , sont contenus tous les fichiers sources et quelques autres dossiers importants , notamment le dossier images qui contient toutes les images des tuiles , le dossier bouton qui contient tous les boutons du menu du jeu , et fonts contient la police des écritures du menu . Pour le menu du jeu , c'est le fichier display_text.c où est contenu toutes les fonctions du menu , jusqu'à l'évènement pour ouvrir(lorsqu'on clique sur commencez)  la fenêtre principale du jeu . Les fichiers sources s'occupant de la fenêtre s'ouvrant lorsque l'on clique sur "commencez" sont : init.c, dessin_rendu1.c, input.c, destroy.c (pour mieux comprendre lisez s'il vous plaît les fichiers sources énumérés ci-contre dans l'ordre). Et enfin, le main.c appelle une seule fonction(execution)  qui fait tout le travail .
  
  4 - compilez le projet pour lancer le jeu : 

- make , pour compiler. Il crée un fichier exécutable prog que vous pouvez exécuter par la suite . Puis faites un make clean pour enlever les fichiers objets. 
NB: commande à exécuter en entrant dans le dossier du projet (project_algo) . Si cela ne marche pas faite celle-ci à la place . 

- gcc main.c display_text.c init.c dessin_rendu1.c input.c destroy.c $(sdl2-config --cflags --libs) -lSDL2_ttf  . 
NB : vous devez être dans le dossier src du projet pour que cette commande marche .
  
  Lien utile : 

- https://github.com/Nylls241/project_algo.git

- https://www.parallelrealities.co.uk/tutorials/#shooter

- https://wiki.libsdl.org/SDL2/APIByCategory

- https://wiki.libsdl.org/SDL2/Installation

- https://www.youtube.com/watch?v=Lwx9rSgwoDg&list=PLrSOXFDHBtfEh6PCE39HERGgbbaIHhy4j&index=23
  
  // Rédigé par Nylls Gersan BOUTOTO
