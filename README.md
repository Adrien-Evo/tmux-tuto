# tmux-tuto

Ce tuto a pour but de vous familiariser avec tmux. Pourquoi utiliser cet outil, comment le metttre en place et comment l'utiliser.

## What is TMUX ?

Tmux est un multiplexeur de terminal. Il permet de gérer plusieurs sessions et fenetres dans un meme terminal.

## Why TMUX ?

- Vous travaillez regulièrement sur un terminal.
- Vous travaillez sur un cluster de calcul via un terminal.
- Vous vous perdez au milieu de tout vos terminaux
- Vous voulez impressionner vos collègues
- Vous adorez être organisé

Si vous vous reconaissez dans au moins une de ces catégories, Tmux est fait pour vous. 


##Comment utiliser TMUX :
### Instalation

sudo apt-get install tmux

On, the cluster
module load tmux

###Première prise en main
tmux new -s first

tmux detach

tmux ls

tmux attach -t first

for i in {1..100};do sleep 1s;echo "tmux $i" >> testtmux.txt;done

Maintenant vous pouvez fermer votre fenetre avec Ctrl + C ou just cliquer sur fermer


Vous pouvez constaster avec wc -l testtmux.Txt que le fichier contine d'etre incrémenter avec votre petit script bash qui tourne sur votre session tmux. Et ceci malgré la fermeture brutale du terminal

tmux kill-session

###Configuration de votre tmux
Tmux lit un fichier "caché" situé sur votre "home" : ~/.tmux.conf

Ce fichier vous permet de customiser votre tmux. Il est meêm nécessaire d'en utiliser un pour remplacer certaines commande par défault de tmux qui sont peu pratique

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