# GIT

Salut, C'est mon tout premier tuto Git !  
C'est partit pour découvrir Git et son environement.  
Pour commencer n'oubliez pas d'installer Git sur votre ordinateur, sur Windows je vous conseille d'utiliser **GitBash**.  
Pour Linux aucun problème, Git est déjà installé par défault.  
Si vous êtes prêt, vous pouvez commencer !

Avant d'ouvrir une invite de commande, créé un compte sur :octocat:Github, Bitbucket ou Gitlab.  
Une fois le compte créé, créé un nouveau "répertoire" (repository) avec le nom suivant : **tutogit**

## Lexique

## Répertoire

Un répertoire représente en général un projet. Dans votre répertoire vous allez trouver tous les fichiers de votre projet.

## Branche

Une branche représente une succession de commit.  
Vous pouvez créée plusieurs branches qui contienne chacune des version différente de votre projet.  

<img src="assets/branch-and-history.png">  

Sur ce schéma la branche nommé *Master* contient trois commits ou instantanés (A,B,C), le nombre au dessus des instantanés sont leus identifiants.  

### Deux visions différentes

Vous pouvez comprendre le concept de branche avec deux visions.  
Retenez celle qui vous conviens le mieux.

### Vision par pointeur

Cette vision est la plus proche du fonctionnement de Git.

Dans cette vision une branche est un pointeur avec un nom (ex: Master) qui fait référence a un commit.  
Tout les commits ont au moins un parent qui est commit, cela signifie que c'est une chaîne de commit.  
Une branche n'est qu'un nom de pointeur sur cette chaîne.

<img src="assets/basic-branching-1.png"> 

<br><br>

Quand vous créez une nouvelle branche avec git checbout -b, vous créez en réalité un nouveau pointeur avec un nom à l'emplacement où vous êtes.

<img src="assets/two-branches.png"> 

Dans cet exemple: git checkout -b testing

<br><br>

Git a besoin de savoir sur quelle branche / pointeur vous êtes. Pour cela vous êtes vous même un pointeur nommé *HEAD*.  
Vous pouvez vous dépacer de branche en branche facilement car vous êtes représenté par un pointeur qui pointe en général sur des branches.

<img src="assets/head-to-testing.png"> 

Dans cet exemple : vous êtes sur la branche *testing*, quand vous utilisez git checkout, vous déplacez votre pointeur *HEAD*.

<br><br>

Quand vous travaillez, vous faites des nouveaux commits, ces commits sont ajoutés à la fin de la chaîne.

<img src="assets/advance-testing.png"> 

Dans cet exemple : vous avez créé un nouveau commit identifié par l'id *87ab2* sur la branche testing. Quand vous commitez, votre pointeur de branche et votre pointeur *HEAD* se déplace vers ce nouveau commit automatiquement. Mais les autres branches reste à leur place. Par conséquent vous avez des branches qui sont en retard.  
Git pull raméne un pointeur à la fin de la chaîne.

<br><br>

Si vous voulez revenir a un instant précédant, vous pouvez git checkout sur une branche sou sur un commit.

<img src="assets/checkout-master.png"> 

Dans cet exemple : vous avez exécuté git checkout master  
Si vous avez exécuté git checkout *f30ab*, votre HEAD est détaché (d'une branche) et vous ne pourrez pas faire de git pull pour amener le pointeur à la fin de la chaîne vu que vous n'êtes plus sur une branche. 

<br><br>

Quand vous travaillez avec d'autre personne, chaque collègue peut créé des branches et de commiter dessus. Cela peut séparer la chaîne principale en plusieurs morceaux.   

<img src="assets/advance-master.png"> 

<br><br>

Une fois le travail terminé sur une branche, nous voulons ramener le travail effectué sur la branche master.  
Pour faire cela il faut que nous fusionnons les branches avec la commande git merge.    
Quand git fusionne deux branches, il créé un nouveau commit (commit merge) qui a deux parents : 
- le dernier commit de la branche master
- le dernier commit de votre nouvelle branche

Attention cette étape peut générer des conflits.  
Nous avons vu qu'une branche n'est en réalité qu'un pointeur sur un commit donc si vous supprimez une branche cela n'a aucune importance car vous n'avez supprimer que le pointeur mais pas les commits créés. Mais une fois la branche supprimé il est plus difficile d'accéder à ces commits.  

<img src="assets/basic-merging-2.png"> 

Dans cet exemple : vous avez fusionné *iss53* dans *master*
git merge iss53  
Si *C3*,*C4*,*C5* ne sont que des fichiers différents, vous n'aurez pas de conflit.  
Mais si le même fichier est modifier, vous risquez d'avoir des conflits.  

## Pourquoi rebaser plutot que de merger ?

Merge : 

<img src="assets/basic-rebase-2.png"> 

Rebase :

<img src="assets/basic-rebase-3.png"> 

### Lisibilité

Nous avons vu comment qu'un commit de merge fait référence a deux parents.   
Un rebase rejoue tous les commits sur une branche depuis une autre branche.
En therme de lisibilité, le rebase est meilleure car l'ensemble des commits apparaissent dans la branche lors du rebase alors qu'avec un merge nous disposerons que d'un gros commit qui nous renvois sur la branche qui a été mergé. 

### Importer une branche

Dans certain cas vous avez créé une autre branche comme sur ce schéma.  

<img src="assets/interesting-rebase-1.png"> 

Vous avez une branche nommée *server* créée depuis la branche *master*, vous avez également une branche *client* créée depuis la branche *server*.  
Problème : Comment importer *C8* et *C9* ?

La meilleure strategie est de rejouer les commits *C8* et *C9* à la fin de la branche master.  

<img src="assets/interesting-rebase-2.png"> 

Dans cet exemple, vous avez exécuté sur la branche master git rebase client.  

### Vision par branche d'arbre

Vous pouvez voir un projet git comme un arbre qui pousse.   
La racine de votre arbre c'est le commit initial.

<img src="assets/tree.png"> 

Dans un projet git le tronc  de votre arbre est la branche master car c'est la première branche.  
Une branche est composée par différent commit qui font grandir votre arbre.  
Dans ce schéma :  
- Les points bleus et verts sont des commits
- Les points rouges et oranges représentent les création de branches

Quand vous créé un projet git avec seulement un commit, vous obtenez cette représentation :  

<img src="assets/first-commit.png"> 

Dans cet exemple : nous avons un bamboo, le tronc est représenté par le branche master en vers, les commits sont resprésenté par les points oranges et le super panda représente votre position c'est à dire la *HEAD*.  
Actuellement vous êtes sur le premier commit.  

<br><br>

<img src="assets/git-commit.png"> 

Dans ce cas vous souahaitez ajouter une nouvelle fonctionnalité *user*, pour cela vous créez un nouveau commit *user commit* contenant votre fonctionnalité.  
Votre bamboo grandit avec les commits et le panda suit les commits.  

<br><br>

Il est possible de créé différentes branches pour travailler à plusieurs.  
Chaque collègues a son propre panda et peut travailler sur la même branche que vous.

<img src="assets/git-checkout.png"> 

Dans cet exemple vous avez créé une branche *admin* provenant du commit *user commit*.  
Nous remarquons que votre panda n'a pas de commit face à lui car Git ne créé pas de commit lors d'une création de branche.  

<br><br>

Quand vous souhaitez travailler sur plusieurs fonctionnalités, vous pouvez créé plusieurs branches avec différents commits dessus.  

<img src="assets/git-branch.png"> 

A ce moment, vous souhaitez ramener les commits de votre branche admin sur la branche master.  

<img src="assets/git-merge.png"> 

La command git merge créé un commit attaché à vore branche admin.  
Si vous supprimez la branche admin, vous ne perdez pas les commits qui sont dessus, vous oubliez simplement le chemin pour y accéder.  

<br><br>

Vous pouvez aussi utiliser git rebase pour ramener vos fonctionnalités. Le résultat est similaire mais permet d'avoir une meilleure vue de votre projet. Un rebase permet de copier à la fin tous les commits de différence d'une branche à une autre.  

<img src="assets/git-rebase.png"> 

## Commit
 
Un commit représente un instant du projet  nommé également instantané (snapshot).  
Git enregistre les modifications par instant comme une photo au lieu de calculer des différences.  
Un commit contient un arbre de fichier modifier, un auteur, un nom, un identifiant, un parent et d'autre informations.   
Le parent d'un commit est l'instantané précédent donc le commit d'où on vient.  

<img src="assets/commit-and-tree.png">  

Dans ce schéma *98ca9* est l'identifiant du commit.   

Pour créé un commit, vous devez suivre les étapes suivantes : 
1) Ajouter les fichiers que vous souhaitez sauvegardé au commit (git add)
2) Nommer, verouiller et sauvegarder le commit (git commit)
3) Envoyer les modifications dans votre platerfome de versionning (git push)

<img src="assets/commit cycle life.png">  

## Conflit

A conflict is a Git error, it appears when you try to merge two branchs and in these branchs you have modified the same file.  
Git can't find which file would you like to keep.  
To continue, you may resolve conflicts.  

To know which files are in conflict you can use git status :
```
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)

    both modified:      index.html

no changes added to commit (use "git add" and/or "git commit -a")
```
In this example, index.html is in conflict.  
*both modfied* means this file is modified on the both branch.  

To fix a conflict you may open files in conflict and change inside lines you would keep or remove.  

In file, conflicts are always marked with the following syntax :

```
<<<<<<< HEAD:file
code of the branch where you are
======
code of the branch that you want merge
>>>>>>> branch_to_merge:file
```

You may choose between the first part and the second part.  
Some tools and editors can help you to fix more quickly.  

<img src='assets/basic-merging-2.png'>

```
<<<<<<< HEAD:index.html
<div id="footer">contact : email.support@github.com</div>
======
<div id="footer">
 please contact us at support@github.com
</div>
>>>>>>> iss53:index.html
```

In this example, we would like to merge *iss53* in *master* but we have a conflict in *index.html*.  

## Gitignore

## Command Git

## git status
Display the state of your git project

```
git status
```
The following response is the simplest response
```
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

We will look line by line this response :  
1) *On branch master*  
   Git indicated you are on a branch named *master*
2) *Your branch is up to date with 'origin/master'.*  
   It indicated the exact state of your branch  
   *origin* represent your version manager platform  
   *origin/master* represent the branch with the name *master* in your version manager platform  
3) *nothing to commit, working tree clean*  
   Nothing to commit means you are any modify files  
   Working tree clean means the same things in this case
   

If you aren't in a git project the following error will be display
```error
fatal: not a git repository (or any of the parent directories): .git
```

## git clone
Download your repository where you are with your console  

```
 git clone url_of_my_project
```

For example if you would like download this project you can execute :

```
 git clone https://github.com/SamuelPelletier/tuto-Git.git
```

## git add
Add file in a commit.

```
git add /path/to/filename
```

A usefull option of this command is all.  
Add all files who are modified or untracked.
```
git add -A
```

## git commit

Close and named the commit.  
When the commit is closed, git add command appends file in a new commit.

```
git commit -m"my commit title"
```

## git push

Send all commits to our version manager platform.  

```
git push
```
## git pull

Get all new commits from your version manager platform. 

```
git pull
```

Becarefull you can't pull if you are some files not committed.

## git checkout

Change your position to another branch.

```
git merge my_branch
```

If you add -b parameter, you create a new branch (In french : tiret b comme bouvelle branche)

```
git merge -b my_branch
```

## git merge

Merge a branch with another branch. the branch where you are will be merge with the branch in parameter.

```
git merge my_branch
```

Becarefull you can rise conflicts.

## git rebase

Replay all commits of a branch on another branch.  
The result of this command is like git merge.

```
git rebase branch_to_bring_back
```

Becarefull you can rise conflicts.

<br><br><br><br>
For the Windows guys : 
- Right click on your desktop
- Choose **Git Bash Here**

For the Linux player : 
- Just open a command line

From here it's the same work if you are pro Windows or a Linux priest :pray:

We will import your repository with the follwing command

```
git clone my_git_repo_url
```
Nice you have write your first git command ! 🎉

Let's go in this great folder 
```
cd tutogit
```

You have just download a git project, now we can begin to manage our git project.  
You can note you have already a folder name *.git*. This folder store all your modify in your git project.

We will configure our username and our email
```
git config --global user.name "my_username"
```
```
git config --global user.email "my@email.com"
```
We can check our repository with git status
```
git status
```

We will create a new file in our folder.
```
touch index.html
```

We will try again git status for see the difference.
```
git status
```
We will be interested in this response to the previous one.

```
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        index.html

nothing added to commit but untracked files present (use "git add" to track)
```

Git tells us we have an untracked file named *index.html*.  
If you have a colorated console, you can note index.html is in red, red means your file isn't in a commit.   
It says too, *nothing added to commit* this sentence means our commit is empty.  
But it advises *use "git add \<file>..." to include in what will be committed*.  
In order to save the creation of our index.html, we must use the command advise and below.

In our case we add only *index.html* you can execute one of the following command :  

```
git add index.html
```
or
```
git add -A
```
<br>

We will check the new git status  
```
git status
```
You should get this response
```
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   index.html
```

We observe *index.html* is in *Changes to be comitted* so *index.html* is in the file list will be send to our version manager platform, its color change to green for represent your file in a commit  
Git informs us that we can rollback our git add with git reset, we will see this command after.

Now we have one file in our commit but the commit is open yet.  
We may close the commit to send it to our version manager platform  

In our case we create our first commit
```
git commit -m'First commit with index.html'
```

We will send our new creation file to our version manager platform  
```
git push
```

Just with the commands before you can work alone on your one compture. 😢  

If you would like work on a git project alone but on many computer you have needed the following command :  
```
git pull
```

Before you start worked on another computer, you may use this command to get back your code on this computer.  

Step 1 : Code on your first computer  
<img src='assets/work-computer1.png'>

<br><br>

Step 2 : Send your code to your version manager platform  
<img src='assets/work-manager.png'>

<br><br>

Step 3 : Get back your code on your second computer for work   
<img src='assets/work-computer2.png'>

<br><br>

Now you have found a friend to work with you.  
No problem, we will create two branchs, one for you and one for your friend.  
If you haven't a friend we will simulate one.  
  
I present you :  
<br>

<img style="width:100px;height:auto;margin-left:20px;" src='assets/Companion Cube.png'>  

The Companion Cube !  

"*This Weighted Companion Cube will accompany you. Please take care of it.*"
<br>

```
git checkout -b my_branch
```
```
git checkout -b my_companion_cube_branch
```

You are on the companion cube branch, we will simulate a collaborative work.  

```
touch companion_cube.html
```
```
git add -A
```
```
git commit -m'Add companion cube page'
```
```
git push
```

<br>

Now we will return on your branch and get back the modifications create by your new friend.  
```
git checkout my_branch
```

We will use git merge to merge your friend branch into your branch.  

```
git merge my_companion_cube_branch
```

Now your branch is at the same progress as your friend.  

It was easy but it's not always the case. We will see conflicts.  

We will write something in our file :  
```
echo "add some text" >> index.html
```
```
git add -A
```
```
git commit -m'Add text in index.html'
```
```
git push
```
```
git checkout my_companion_cube_branch
```
```
rm index.html;touch index.html; echo "add some cube text" >> index.html
```
```
git add -A
```
```
git commit -m'Add text in index.html'
```
```
git push
```

We will try to merge these two branchs like before.
```
git merge my_branch
```
```
Auto-merging index.html
CONFLICT (add/add): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

Check the status of your branch :  
```
git status
```
```
On branch my_companion_cube_branch
Your branch is ahead of 'origin/my_companion_cube_branch' by 1 commit.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both added:      index.html

no changes added to commit (use "git add" and/or "git commit -a")
```

You may resolve the conflict to continue.  

Once the conflict is fixed, add your modification to the commit : 
```
git add -A
```
or 
```
git add -index.html
```

Close the commit with :  
```
git commit
```

When Vim editor opens juste press enter or you can left with *:q*.  

