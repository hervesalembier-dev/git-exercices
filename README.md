Example Git repository
======================

This repository shall explain the Git data model

Master
------

The master branch is the default branch, this is on default checked out when the
repository is cloned

hello_world.c instructions
--------------------------
gcc -Wall hello_world.c -o hello
./hello



## site decrivant les commandes git avec toutes les options
https://git-scm.com/docs
https://www.miximum.fr/blog/git-rebase/

## Définition variable => fichier, dir associé => porté
--local => .git/ => projet

--global => ~/.gitconfig => user

--system => /etc/gitconfig => machine 

## configure le git et les info de connexion
git config --global user.name "root"

git config --global user.email hervesalembier@yahoo.fr

## crée des alias des commandes
git config --global alias.br branch

git config --global alias.ci commit

git config --global alias.st status

git config --global alias.last 'log -1 HEAD'

git config --global alias.hist 'log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short'

##
git config --global init.templatedir ~/.git_template

## affiche la configuration global de git
cat ~/.gitconfig

## edit le fichier de config global dans l'éditeur par défaut
git config --global -e

## edit le fichier de config local dans l'éditeur par défaut
git config -e

## défini l'éditeur par défaut
git config --global core.editor vim

## afficher les logs
git log

git log -1

git log -1 --stat

git log --pretty=oneline 

git log --oneline -4

git log --author=Hervé

## liste des fichiers inclu dans le git via add
git ls-files --stage

## effectue un add et un commit
git commit -am "message"

## supprimer, déplacer, renomer un fichier en effectuant un add automatiquement
git rm fichier
git mv fichier1 fichier2

## supprime de git sans supprimer le fichier
git rm --cached fichier

## affiche la différence entre le repertoire de travail et l'index 
git diff

## affiche la différence entre le repertoire de travail et le dernier instantané
git diff --staged


## affiche la différence entre l'index et la zone de transfert
git diff HEAD

## affiche la différence entre un commit et la zone
git diff 9798dd7..HEAD

## affiche ??
git blame fichier

## Supprime tous ce qui a pas commit et revint à l'état du dernier commit !! (commande non reversible)
git reset --hard HEAD

## Efface l'ensemble des modification pour arriver au commit désigné (commande réversible)
git reset hashDuCommit

## Remplacer le sommet de la branche actuelle en créant un nouveau commit
git commit -m "Message" --amend

## Remplacer le contenu d'un commit sans modifier le message
git commit --amend --no-edit 

## met un tag (comme la version) sur un commit
git tag v1.1

## met un tag (comme la version) sur un commit précis
git tag v1.1 idCommit

## pousse les sources vers le depot avec les tags
git push origin branch --tags

## supprime un tag 
git push origin :refs/tags/v1.1

## crée une branch
git checkout -b nombranch

git branch nombranch

## vérifie que le nom de branch est correct
git check-ref-format --branch nombranchatester

## merge une branche dans le master
git merge branch master

## merge une branche dans une branche
git merge branche autreBranche

## supprimer une branche
git branch -d mabranch

## réapplication des commits sur une branche
git rebase

## donne le type de l'objet
git cat-file -t 2fcd9bc

## donne une partie de l'arborescence du fichier ou liste les fichiers selon l'objet
git cat-file -p 2fcd9bc

## Efface les fichiers inutiles et optimise le depot local
git gc

## affiche l'état en manière abrégé
git status -s

## affiche les branche
git branch

## ajoute une branche nombranche
git branch nombranche

## détruit une branch
git branch -d nombranch

## affiche les branches à distance
git branch -r

## affiche toutes les branches en mode verbeux
git branch -av

## choisit la branche courante
git checkout nombranche

## merge une branche dans le master
git merge newbranch

## sauvegarde le travail dans une planque
git stash

## affiche la liste des sauvegardes
œ

## recharge la dernière sauvegarde
git stash pop

## modifie le serveur distant en mode upstream : permet d'associer une branche local à une branche distante
git remote add upstream https://github.com/hervesalembier-dev/calc2.git

## affiche les serveur distant ou sont stocké les dépot
git remote -v

## Ajout un dépot distant via ssh
git remote add git@gitlab.com:univlille/webforce3-2020/herve-salembier/flask-for-dummies.git

## Ajout un dépot distant via https
git remote add https://gitlab.com/univlille/webforce3-2020/herve-salembier/flask-for-dummies.git

## crée une branche depuis un branche distante
git branch nombranche origin/nombrancheDistantels

## Prend le patch qui a été introduit lors d’une validation et essaye de l’appliquer sur la branche courante
git cherry-pick d003b91

## Réapplique un commit au sommet du master dans la branche courante ou pseudo branch en cas d'erreur
git rebase idCommit

## met à jour sans les branches locals
git fetch

## annule un merge
git merge --abort

## 
git rebase -Xours origin/master

## ajoute un arbre de travail 
git worktree add -b features ../super_calc_features origin/features

## affiche la liste des arbre de travail
git worktree list

## supprime l'arbre de travail et efface 
rm -Rf ../super_calc_features/

## Nettoye le worktree
git worktree prune

## ajoute un module => A étudier
git submodule add https://github.com/hervesalembier-dev/sub_ui.git sub_ui

## affiche les modules => A étudier
git show :.gitmodules

## A étudier
git submodule update --init 
git submodule status

## afficher le contenu d'un fichier avec git
git log -1
 
récupérer l'id et l'utiliser

git cat-file -p 13dcada077e446d3a05ea9cdbc8ecc261a94e42d

récupérer l'id du tre et l'utiliser

git cat-file -p 34fa038544bcd9aed660c08320214bafff94150b

récupérer l'id du fichier à lire et l'utiliser

git cat-file -p 92f046f17079aa82c924a9acf28d623fcb6ca727

## afficher le pointeur sur le dernier commit
git cat-file -p master

git cat-file -p HEAD

cat .git/refs/heads/master

## affiche le commit associé à ce tag
git cat-file -p v1.0
