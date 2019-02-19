# tmux-tuto

Ce tuto a pour but de vous faire découvrir Tmux.
Pourquoi utiliser cet outil, comment le mettre en place et comment l'utiliser.
Vous trouverez des certainement des personnes pour vous expliquer que TMux

## What is TMUX ?

Tmux est un multiplexeur de terminal. Il permet de gérer plusieurs sessions et fenêtres dans un meme terminal.

## Why TMUX ?

- Vous travaillez régulièrement sur un terminal.
- Vous travaillez sur un cluster de calcul via un terminal.
- Vous vous perdez au milieu de tout vos terminaux
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

que le fichier continue d'être incrémenté avec votre petit script bash qui continue de tourner sur votre session tmux. Et ceci malgré la fermeture brutale du terminal. Plus efficace que :
```nohup commande &&```
ou autre combinaison de disown et &.

### Configuration de votre tmux
Tmux lit un fichier "caché" situé sur votre "home" : 

**~/.tmux.conf**

Ce fichier vous permet de customiser votre tmux. Il est même nécessaire d'en utiliser un pour remplacer certaines commande par défaut peu pratiques. Copiez le contenu du .tmux.conf de ce github dans votre ~/.tmux.conf

### Deuxième prise en main

Sur un terminal, créez une session tmux appelée *second* 
```
tmux new -s second
```

Afin d'executer des commandes Tmux, il faut commencer par utiliser le préfixe **Crtl + a**.
Ce préfixe a été changé dans le fichier de configuration. Il est nécessaire de presser ce prefixe afvant de pouvoir lancer le reste des commandes

'''
[prefix] + c
[prefix] + n
[prefix] + P
[prefix] + _
[prefix] + |
[prefix] + UP
[prefix] + DOWN
[prefix] + LEFT
[prefix] + RIGHT
[prefix] + f + ENTER
[prefix] + x
'''




General intro :
https://pmihaylov.com/tmux-terminal-multiplexer/

https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/

Petit tuto sur les fichier.conf de Tmux qui regroupe la plupart des raccourcis du fichier de configuration de ce tuto
https://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/

Github page with lots of links on tmux

https://github.com/rothgar/awesome-tmux

Tao of Tmux
https://tmuxp.git-pull.com/en/latest/about_tmux.html

Config super technique

https://github.com/samoshkin/tmux-config

Une autre config super technique
https://github.com/gpakosz/.tmux