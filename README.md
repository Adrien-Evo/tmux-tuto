# tmux-tuto

Ce tuto a pour but de vous faire découvrir Tmux.
Pourquoi utiliser cet outil, comment le mettre en place et comment l'utiliser.

## What is TMUX ?

Tmux est un multiplexeur de terminal. Il permet de gérer plusieurs sessions et fenêtres dans un même terminal. Similaire à l'outil Screen.


## Why TMUX ?

- Vous travaillez régulièrement sur un terminal.
- Vous travaillez sur un cluster de calcul via un terminal.
- Vous vous perdez au milieu de tout vos terminaux :
![alt text](https://raw.githubusercontent.com/Adrien-Evo/tmux-tuto/master/notmux-multi.png)   
- Vous voulez impressionner vos collègues
- Vous adorez être organisé

Si vous vous reconnaissez dans au moins une de ces catégories, Tmux est fait pour vous. 


## Comment utiliser TMUX :
### Installation
Sur linux, ouvrez un terminal :
```
sudo apt-get install tmux
```

Sur le cluster bird:
```
module load tmux
```

### Première prise en main

Sur un terminal, créez une session tmux appelée *first* (*-s* est pour session)
```
tmux new -s first
```
Détachons maintenant cette session Tmux. Nous revenons sur le terminal standard.
```
tmux detach
```
*Tmux ls* vous indique les sessions Tmux actives :

```
tmux ls
```
On peut ré-attacher la session *first* avec tmux attach -t (pour target)
```
tmux attach -t first
```
Maintenant un petit test pour illustrer une des fonctionnalités de tmux. Lancez cette commande directement après avoir attaché votre session first

```
for i in {1..100};do sleep 1s;echo "tmux $i" >> testtmux.txt;done
```
Maintenant vous pouvez fermer votre fenêtre en cliquant sur la croix de votre fenêtre.

Rouvrez un terminal et vous pouvez constater avec 
```
wc -l testtmux.txt
```

que le fichier testtmux.txt continue d'être incrémenté grace à votre petit script bash qui tourne sur votre session tmux :astonished:. Et ceci malgré la fermeture brutale du terminal. Plus efficace que `nohup commande &&` ou autre combinaison de `disown` et `&`.

## Configuration de votre tmux
Tmux lit un fichier "caché" situé sur votre "home" : 

**~/.tmux.conf**

Ce fichier vous permet de customiser votre tmux. Il est même nécessaire d'en utiliser un pour remplacer certaines commande par défaut peu pratiques. 

:point_right: Déplacer le .tmux.conf de ce github dans votre ~/.tmux.conf

Ce fichier de configuration est assez simple et regroupe des pratiques très courante chez les utilisateurs de Tmux. La deuxième prise en main va illustrer quelques-unes des commandes incluses dans ce fichier de configuration.

### Deuxième prise en main

Sur un terminal, créez une session tmux appelée *second* 
```
tmux new -s second
```

Afin d'executer des commandes Tmux, il faut commencer par utiliser le préfixe **Ctrl + a**.
Ce préfixe a été changé dans le fichier de configuration (*initialement* **Ctrl + b**). Il est nécessaire de presser ce préfixe avant de pouvoir lancer le reste des commandes.

Ici nous allons créer une nouvelle fenêtre, naviguer entre les deux fenêtres, créer des panneaux latéral et horizontal, les lister et tuer une fenêtre:
```
[prefix] + c
[prefix] + n
[prefix] + P
[prefix] + _
[prefix] + |
[prefix] + UP
[prefix] + DOWN
[prefix] + LEFT
[prefix] + RIGHT
[prefix] + w
[prefix] + x
```

![alt text](https://raw.githubusercontent.com/Adrien-Evo/tmux-tuto/master/tmux.gif)


## Copier coller :

Une façon saine de copier coller peut se faire en maintenant SHIFT et en sélectionnant avec la souris. Puis clic milieu tout en maintenant shift ou l'on veut coller. Simple, efficace et utilise le clipboard système (copier coller dans tmux et hors tmux possible)

## Liens divers et variés

General intro :
https://pmihaylov.com/tmux-terminal-multiplexer/

https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/

Petit tuto sur les fichier.conf de Tmux qui regroupe la plupart des raccourcis du fichier de configuration de ce tuto
https://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/

Une cheatsheet:
https://gist.github.com/MohamedAlaa/2961058

Tuto en 5 partie
https://medium.freecodecamp.org/tmux-in-practice-series-of-posts-ae34f16cfab0

Github page with lots of links on tmux
https://github.com/rothgar/awesome-tmux

Tao of Tmux
https://tmuxp.git-pull.com/en/latest/about_tmux.html

Config super technique
https://github.com/samoshkin/tmux-config

Une autre config super technique
https://github.com/gpakosz/.tmux
