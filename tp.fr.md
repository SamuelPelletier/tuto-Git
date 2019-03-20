# TP FR

## Aide

1) Utiliser le plus fréquemment possible la commande **git status**
2) Pour voir l'historique de vos commandes utiliser **history**
3) Pour voir l'historique de vos commits utiliser **git log**

## Initialisation

1) Créer un compte sur Github ou Bitbucket
2) Créer un répertoire (repository) sur la plateforme de votre choix en public
3) Télécharger git bash si besoin
3) Importer ce répertoire sur votre ordinateur avec **git clone**
4) Se placer dans le dossier créer par la commande git clone

## Commit

1) Créer deux fichiers
2) Faire un commit contenant qu'un seul des deux fichiers grâce aux commandes **git add** et **git commit**
3) Envoyer le commit à votre plateforme grâce à la commande **git push**
4) Supprimer l'ajout de votre deuxième fichier en utilisant la commande **git reset**

## Travailler à plusieurs Partie 1

Nous allons simuler le fait de travailler à plusieurs.

1) Avec une nouvelle invite de commande cloner une nouvelle fois le projet en ajoutant un nom de dossier différent
2) Accéder au dossier créé

Votre premier dossier représente le premier ordinateur, le deuxième dossier représente le second ordinateur.  

3) Dans le dossier 1, créer une branche grâce à la commande **git checkout**
4) Dans le dossier 2, créer une branche
5) Créer un fichier dans chacun des dossiers et faire un commit push sur chaque branche
6) Ramener la branche du dossier 2 dans le dossier 1 grâce à la commande **git pull**
7) Ramener la branche du dossier 1 dans le dossier 2 
8) Dans le dossier 2, ramener la branche du dossier 1 sur la branche master, pour cela utiliser la commande **git merge**
9) Dans le dossier 1, ramener la branche du dossier 2 sur la branche master
10) Dans le dossier 2, mettre à jour la branche master

## Travailler à plusieurs Partie 2 

1) Dans le dossier 2, créer une nouvelle branche nommée *foo*
2) Créer un fichier avec du texte dedans
3) Faire un commit / push
4) Retourner sur la branch master
5) Créer un fichier portant le même nom que le précédent et ajouter du texte dedans différent
6) Retourner sur la branch *foo*

Une erreur doit apparaître, vous devez mettre de côté votre modification pour vous déplacer.  

7) Mettre de côté la modification grâce à la commande **git stash**
8) Se déplacer sur la branche *foo* et faire une modification.
9) Faire un commit / push
10) Retourner sur la branche master 
11) Ramener les modifications mises dans le stash grâce à la commande **git stash**
12) Faire un commit / push

## Résolution de conflit

1) Créer un nouveau fichier avec du texte dedans
2) Faire un commit / push
3) Créer une nouvelle branche
4) Créer un nouveau fichier portant le même nom que le précédent avec du texte différent dedans
5) Faire un commit / push
6) Fusionner la branche actuelle avec la branche master grâce à la commande **git merge**

Une erreur de conflit doit apparaitre.

7) Ouvrir le fichier créé avec un éditeur et corriger le conflit
8) Ajouter le fichier au commit
9) Envoyer le fichier **git push**