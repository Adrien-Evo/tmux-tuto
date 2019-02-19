# tmux-tuto

Ce tuto a pour but de vous familiariser avec Tmux. Pourquoi utiliser cet outil, comment le mettre en place et comment l'utiliser.

## What is TMUX ?

Tmux est un multiplexeur de terminal. Il permet de gérer plusieurs sessions et fenêtres dans un meme terminal.

## Why TMUX ?

- Vous travaillez régulièrement sur un terminal.
- Vous travaillez sur un cluster de calcul via un terminal.
- Vous vous perdez au milieu de tout vos terminaux
- Vous voulez impressionner vos collègues
- Vous adorez être organisé

Si vous vous reconnaissez dans au moins une de ces catégories, Tmux est fait pour vous. 


##Comment utiliser TMUX :
### Installation
Sur linux, ouvrez un terminal et :
```
sudo apt-get install tmux
```

Sur le cluster:
```
module load tmux
```

###Première prise en main
Sur un terminal :

Vous créer une session tmux appelée *first* . (*-s* est pour session)
```
tmux new -s first
```
Détachons maintenant cette session Tmux
```
tmux detach
```
TMux ls vous indique les sessions tmux actives :

```
tmux ls
```
On peut ré-attacher la session *first* avec tmux attach -t (pour target)
```
tmux attach -t first
```
Maintenant un petit test pour illustrer une des fonctionnalités de tmux. lancé cette commande directement après avoir attaché votre session first
'''
for i in {1..100};do sleep 1s;echo "tmux $i" >> testtmux.txt;done
```
Maintenant vous pouvez fermer votre fenêtre en cliquant sur la croix de votre fenetre

Rouvrez un terminal et vous pouvez constater
Vous pouvez constater avec wc -l testtmux.Txt que le fichier continue d'être incrémenter avec votre petit script bash qui tourne sur votre session tmux. Et ceci malgré la fermeture brutale du terminal

tmux kill-session

###Configuration de votre tmux
Tmux lit un fichier "caché" situé sur votre "home" : ~/.tmux.conf

Ce fichier vous permet de customiser votre tmux. Il est même nécessaire d'en utiliser un pour remplacer certaines commande par défaut de tmux qui sont peu pratique

Copiez le contenu du .tmux.conf de ce github dans votre ~/.tmux.conf




General intro :
https://pmihaylov.com/tmux-terminal-multiplexer/

https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/


Github page with lots of links on tmux
https://github.com/rothgar/awesome-tmux


Config super technique
https://github.com/samoshkin/tmux-config

Une autre config super technique
https://github.com/gpakosz/.tmux