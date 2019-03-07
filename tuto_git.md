<h1>GIT</h1>

Hey, this is my first tuto about Git !  
Let’s go discover Git and its environment.  
To begin not forget to install Git on your computer, on Windows I advise to choose **GitBash** software.  
For Linux no problem, Git is already installed.  
If you are prepared, you can start !

Before open a console, create an account on :octocat:Github, Bitbucket or Gitlab.  
Once the account is created, create a new <span style="color:#35d5b6;">repository</span> with the name : **tutogit**

<h2>Lexicon</h2>

<h2><span style="color:#35d5b6;">Repository</span></h2>
It represent in general a project. In your <span style="color:#35d5b6;">repository</span> we will find all files of your project.

<h2><span style="color:#1c6600;">Branch</span></h2>

It represent a timeline of <span style="color:#8c00c0;">commit</span>.  
You can create many <span style="color:#1c6600;">branch</span> with many different versions of your project.  

<img src="assets/branch-and-history.png">  

On this schema the master <span style="color:#1c6600;">branch</span> contains three <span style="color:#8c00c0;">commits</span> or snapshot (A,B,C), the numbers above a snpashot is the reference of a <span style="color:#8c00c0;">commit</span>.  
Every <span style="color:#1c6600;">branch</span> has a pointer, your branch pointer can be before the end of your <span style="color:#1c6600;">branch</span>.  
In this schema the pointer of your <span style="color:#1c6600;">branch</span> is at the end.

<h3>Two different visions</h3>

You can understand the concept of branch and its modelisation with two visions.  
Keep the best for you.

<h3>Vision by pointer</h3>

We can visualize a branch like a pointer on commit. Every commit has a parent commit so it's a chain of commit.  
A branch is just a pointer on this chain.

<img src="assets/basic-branching-1.png"> 

<h3>Vision by tree branch</h3>

<h2><span style="color:#8c00c0;">Commit</span></h2>
 
It represent an instant of your project named also snapshot.   
Git store modifications by instant of project and not by difference.   
A <span style="color:#8c00c0;">commit</span> contains a tree of all modify files, an author, his name, his reference, his parent and some other metadata.  
A parent of commit is the previous version of a <span style="color:#8c00c0;">commit</span>.

<img src="assets/commit-and-tree.png">  

In this schema *98ca9* is the reference of the <span style="color:#8c00c0;">commit</span>.  
A <span style="color:#8c00c0;">commit</span> construct a tree of files references. In tree we find only the list of modifing files

To create a <span style="color:#8c00c0;">commit</span>, we may follow this three steps :  
1) Add files to the commit tree where we would like save modifications (git add)
2) Name and save the commit (git commit)
3) Push the commit to our version manager platform (git push)

<img src="assets/commit cycle life.png">  


<h2>Command Git</h2>

<h2><span style="color:#fa7811;">git status</span></h2>
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
   Git indicated you are on a <span style="color:#1c6600;">branch</span> named *master*
2) *Your branch is up to date with 'origin/master'.*  
   It indicated the exact state of your <span style="color:#1c6600;">branch</span>  
   *origin* represent your version manager platform  
   *origin/master* represent the <span style="color:#1c6600;">branch</span> with the name *master* in your version manager platform  
3) *nothing to commit, working tree clean*  
   Nothing to <span style="color:#8c00c0;">commit</span> means you are any modify files  
   Working tree clean means the same things in this case
   

If you aren't in a git project the following error will be display
```error
fatal: not a git repository (or any of the parent directories): .git
```

<h2><span style="color:#fa7811;">git clone</span></h2>
Download your <span style="color:#35d5b6;">repository</span> where you are with your console  

```
 git clone url_of_my_project
```

For example if you would like download this project you can execute :

```
 git clone https://github.com/SamuelPelletier/tuto-Git.git
```

<h2><span style="color:#fa7811;">git add</span></h2>
Add file in a <span style="color:#8c00c0;">commit</span>.

```
git add /path/to/filename
```

A usefull option of this command is all.  
Add all files who are modified or untracked.
```
git add -A
```

<h2><span style="color:#fa7811;">git commit</span></h2>

Close and named the commit.  
When the commit is closed, git add command appends file in a new commit.

```
git commit -m"my commit title"
```

<h2><span style="color:#fa7811;">git push</span></h2>

Send all commits to our version manager platform.  

```
git push
```
<h2><span style="color:#fa7811;">git pull</span></h2>

Get all new commits from your version manager platform. 

```
git pull
```

Becarefull you can't pull if you are some files not committed.

<br><br><br><br>
For the Windows guys : 
- Right click on your desktop
- Choose **Git Bash Here**

For the Linux player : 
- Just open a command line

From here it's the same work if you are pro Windows or a Linux priest :pray:

We will import your <span style="color:#35d5b6;">repository</span> with the follwing command

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
It says too, *nothing added to commit* this sentence means our <span style="color:#8c00c0;">commit</span> is empty.  
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

We observe *index.html* is in *Changes to be comitted* so *index.html* is in the file list will be send to our version manager platform  
Git informs us that we can rollback our git add with git reset, we will see this command after.

Now we have one file in our commit but the commit is open yet.  
We need to close the commit for send it to our version manager platform  

In our case we create our first commit
```
git commit -m'First commit with index.html'
```

We will send our new creation file to our version manager platform  
```
git push
```

