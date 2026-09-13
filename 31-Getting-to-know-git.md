---
layout: guide
---

# Getting to Know Git
**by Dirk Colbry**

<img src="https://git-scm.com/images/logos/downloads/Git-Logo-2Color.png" width="70%">

```Git``` is a version control system that is used by programmers all over the world. If you want to use programming then you should learn how to use ```git```.  This tutorial is just the first step in learning ```git```. It is a complex tool with with a lot of functionality this tutorial tries to present only some of the commands based on what you nee to do. The three basic categories are:

1. Consumer of files (the class files)
2. Producers of files (your files)
3. Collaborators to files (code reviews)

Resources for these tutorials can be reviewed here:

- [Git Slides](https://docs.google.com/presentation/d/1bDvwJJ5umOEFuoXqekOe9_aFOhX3Pudgv9_EiI-P0eA/edit)
- [Entire Git Video Playlist](https://www.youtube.com/playlist?list=PLqPfbT7gwVP_AlE6HeDQUJsG4nUbGyeh3)

Watch the following video for a brief overview of git and this tutorial:

<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/HuQFjov9CQI" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

## Table of Contents


### [Part one - Consuming Files](#Consuming_Files)
* [Installing git](#Installing_Git)
    * conda install 'git'
* [Cloning a repository](#Cloning_a_repository)
    * What is git
    * git clone
    * git status
    * git log
* [Cleaning/Updating a cloned repository](#Cleaning_Updating_a_cloned_repository)
    * git pull # (our first conflict)
    * git diff
    * git checkout

### [Part two - Producing Files](#Producing_Files)
* [Making your own repository](#Making_your_own_repository)
    * git init
    * folder structure
* [Updating your Repository](#Updating_your_Repository)
    * git add
    * git rm
    * git mv
    * git commit
    * git push
* [Your First Branch](#Your_First_Branch)
    * git branch
    * git checkout
* [Pulling in a new branch](#Pulling_in_a_new_branch)
    * git merge

### [Part three - Collaborating](#Collaborating)
* [Making a Merge/Pull Request on a shared repository<](#Shared_Repository_Merge_Request)
* [Issuing a pull/merge request](#Issuing_a_pull_merge_request)
* [Managing the Upstream](#Managing_the_Upstream)
    * git config -l 
    * git remote add 
    * git fetch
    * git rebase

<a name="Installing_Git"></a>
## Installing Git

In order to effectively clone a directory you will need to install ```git``` on your computer. 

How to install git will depend on the computer you are working on and it's operating systems. Many \*nix based operating systems (Linux, MacOS, etc) may have git already installed.  To check if git is installed open a command prompt on your system and type the following:

```bash
git --version
```

If ```git``` is installed you should see the version number. If not, you will get something like "Command not found error" If git is already installed you should be all set to go.  If not, continue on with the remainder of the instructions.

For this tutorial we will assume that you already have ```conda``` Installed.  The ```conda``` command is a cross-platform installation system. It is primarily installed with Anaconda Python distributions but has support for many other programming languages and commands (including git).  Open up a command prompt on your system and see if you can run the following command:

```bash
conda --version

```

If conda is installed you should see it's version number if not try installing it from the [Anaconda Python website](https://www.anaconda.com/).  

Once you have conda working you should be able to install ```git``` using the following commands:

```bash
conda install git
```

That should be it. Test ```git``` again by opening the command prompt and typing ```git --version``` like we did above. 

Although not required for using ```git```, if you are using windows, I highly recommend also installing the ```md-base``` package which provides a nice set of  \*nix commands that will work on the windows command line.  Many of these commands will be used in the demo videos so having them installed should help you follow along when you are watching the videos:

```bash
conda install m2-base
```

-----
<a name="Consuming_Files"></a>
# Part one - Consuming Files

<a name="Cloning_a_repository"></a>
## Cloning a repository (Consumer)

Most people's introduction to ```git``` is when the come across some software on [github.com](http://github.com) they want to download.  Downloading a ```git``` repository is called cloning.  For example, lets download an example git repository called ```git_practice_repository``` using the following command:

```bash
git clone git_practice_repository
```

This should create a folder in your current directory with the name ```git_practice_repostory``` change into this directory using the following command:

```bash
cd git_practice_repository
```

List the contents of the directory using (```dir``` on windows and ```ls``` on everything else)

<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/sNcxGBk2W78" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

A summary of the commands used in video:

```bash
git clone URL
cd FOLDER
ls
jupyter notebook
```

<a name="Cleaning_Updating_a_cloned_repository"></a>

## Cleaning/Updating a cloned repository (Consumer)

It may be possible that the developer has made some changes to the repository and posted them on their git website. You can use the ```git pull``` command to pull in the changes to your repository.

```bash
git pull
```
<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/rRRNUUyxJ_I" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

Problems can occur if both you and the developer make changes to the same file.  ```git``` is smart and can figure out how to automatically "merge" many changes but if there is a conflict you may have to figure out what to do.  The easiest thing you can do is:

1. Delete your changes
2. Rename your files (effectively getting rid of your changes
3. Add/commit your changes (This one is advanced and will be covered later)

First, check to see what files are in conflict by running the ```get status``` command:

```bash
git status
```

You can look at the changes you made by running the ```git diff FILENAME``` command.  This should show you what you added (Lines with a + before them) and what you deleted (lines with a - before them)


Once you have determined what you want to keep, make a copy of the file with a different name and then move on to the next step. 

You can also reset (overwrite) all of the changes to your local files by "checking out" the original file.  The ```git checkout FILENAME``` command gets a copy of the file file before your changes were made and overrides your changes.  

```bash
git checkout FILENAME
```

Once all of the conflicts have been removed you can then go back and pull in the changes from the developer:

```bash
git pull
```

<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/bLHxdHKv1_c" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>


Review of commands used in video:
```bash 
git fetch
git status
cp FILENAME BKUPFILENAME
git diff FILENAME
git checkout FILENAME
git pull
```

-----
<a name="Producing_Files"></a>
# Part two - Producing Files


<a name="Making_your_own_repository"></a>
## Making your own repository

Now that we are more familiar with git we can make your own repository.  If you plan on using one of the web services such as [Github](http://github.com) or [Gitlab](http://gitlab.com) (there are many others) then you can use their web interface to create a new project and then just clone the empty repository to your local machine. Often the web interfaces have some nice features to add some default files that are common in most repositories (ex. README.md and .gitignore)

However in this step we are going to assume that you have a directory with a few files already in it that you want to turn into a git repository.  In this case you can just change to the git directory and issue the following git initialization command:

```bash
git init .
```
(**_Note:_** the dot in this command. It said to initialize the "current" directory and is very important to include)

Once you have successfully initialized the directory you can add files using the following commands (substitute these FILENAMES with yours):

```bash
git add FILENAME1 FILENAME2 FILENAME3
git add FILENAME4
git commit -m "Initial commit"
```

**_WARNING_** ```git``` repositories work best with text based files.  


<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/IAAv4DjYYUA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>


Review of commands used in video:
```bash
git init .
git add FILENAMES
git commit -m "DESCRIPTION"
git status
```

Here is a tutorial on how to create a new git repository using the [MSU GitLab](http://gitlab.msu.edu) website:

<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/6_cegMFG0Pw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>


Review of commands used in video:
```bash
git clone PROJECT
cat > FILENMAE
git add FILENAME
git status
git commit -m "DESCRIPTION"
git log
git push
```

Similarly, here is a tutorial on how to create a new git repository using the [GitHub.com](http://github.com) website:

<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/dpeHlFm8SYU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>


Review of Commands used in video:

```
git clone URL
ls -lah
git status
```

<a name="Updating_your_Repository"></a>

## Updating your Repository

Now that you have created a repository you want to get good at committing changes.  It is important that modifications are committed early and often so that git can do what it does well and track your files.  Committing files is a two step process.

1. First you want to use the ```git add FILENAME``` command to add new files or files you have changed to your "cart". Ideally the changes are related to each other. 


```bash
    git add FILENAME
```

2. Once all of the files have been added to your "cart" you can commit them by using the ```git commit -m "COMMIT MESSAGE"``` command.  In this case the "COMMIT MESSAGE" is a note describing what you did.  It is important that the note is a good description so you can find it later if you need it.  

```bash
    git commit -m "COMMIT MESSAGE"
```

Once you have committed your changes you may also want to issue a ```git push``` to push your changes up to the centralized repository (github or gitlab) as a safe backup and to share with your collaborators. 

```bash
    git push 
```

<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/GTM-h5xX2Lk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

Review of commands used in video:
``` bash
ls
ls -lah
git log
cd FOLDERNAME
cat > NEWFILENAME
python NEWFILENAME.py
pytest NEWTESTFILE.py
cat status
vi FILENAME
fg
git add FOLDERNAME/FILENAME
git commit -m "DESCRIPTION
git push
```

<a name="Your_First_Branch"></a>

## Your First Branch

Branches are a powerful and important tool when using git.  However, it amazes me how many people use git without ever touching branches.  So, I guess you don't need them but once you understand how they work you can see their power and will find ways to use them all the time (sort of like git itself). 

Branches are where you should do your work.  Branches are a safe place to store changes to files.  Anytime you want to change files you should make sure you are making and committing those changes to a branch.  

To create a branch just type the following:

```bash
    git branch BRANCHNAME
```

Once you have a branch you can list all of your branches (including the default "master" branch) and see which one you are on sing the following command:

```bash
    git branch BRANCHNAME
```

To switch between branches just use the ```git checkout``` command with the BRANCHNAME:

```bash
    git checkout BRANCHNAME
```
    
<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/X0jbrdemjjs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>


Review of commands used in video:
``` bash
git status
git pull
ls
ls -lah
clear
git branch
git branch BRANCHNAME
git checkout BRANCHNAME
vi FILENAME
cat > NEWFILENAME
git add FILENAME NEWFILENAME
git commit -m "DESCRIPTION"
```

<a name="Pulling_in_a_new_branch"></a>

## Pulling in a new branch

So now we have two branches. The master branch has all of the changes made by the primary developer (ex. the instructor).  The second branch has a name you provide ("Test" in this video). This secondary branch is where you do all of your work and commit your changes.  Now you want to update your branch with changes from the master.  To do this we just need to run the ```git merge``` command and fix any conflicts.

    
<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/Byp7TFk5jYw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

Review of commands used in video:
``` bash
git branch
cat > NEWSFILENAME
vi FILENAME
git add NEWFILENAME FILENAME
git push
git pull
ls
cat FILENAME
cat NEWFILENAME
git checkout BRANCH
git merge origin master
```

## Resolving conflics in Jupyter Notebooks

Jupyter notebooks can be tricky to merge since it is in a JSON file format that gets changed each time you run the file which causes git to think you changed the file. 

<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/79hW_TzLos8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

``` bash
git 
git checkout FILENAME
git status
```

-----
<a name="Collaborating"></a>
# Part three - Collaborating
Up until now we have been mostly consumers or primary developers of our git repository. Now we want to think about how give some of our changes to other developers and be part of a community of software developers.   The goal being actual collaboration without getting into each other's way.  

<a name="Issuing_a_pull_merge_request"></a>
## Issuing a pull/merge request

The idea is that we package up all of our suggested changes inside a branch and then "send" that branch to the lead developers for review. If they like what they see they can pull or merge (two words to basically mean the same thing) our branch into their master branch.  This process has been given the name "pull request" or "merge request" depending on what system you are working on.  

The idea behind a pull/merge request is so common that [github.com](http://github.com) and [gitlab.msu.edu](http://gitlab.msu.edu) both have the commands built right into the web interface to make the process as easy as possible.  

The following video will walk you though a basic pull/merge request when you have write permissions on a repository.  This is common for small groups but less common on big opens ource software projects.  Most of the time developers do not have write permissions on the master branch (see next video for this, more common, case). 

<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/pcn6AdM0qB4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>


Review of commands used in video:
``` bash
pwd
ls
git status
git branch BRANCHNAME
git checkout BRANCHNAME
clear
vi FILENAME
cat FILENAME
git add FILENAME
git commit -m "DESCRIPTION"
git push origin BRANCHNAME
```

<a name="Forking_a_repository"></a>

## Forking a repository

A more common case for working as a collaborator to a repository is to work from your own copy (also known as a fork), develop your changes on your branch and then use github or gitlab to take your committed branch and use it to issue a pull/merge request.  

This video describes the process of forking a repository and issuing a pull request.  


<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/ZkKtzHtzEvQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

Review of commands used in video:
``` bash
git clone URL
cd FOLDER
ls
git branch BRANCHNAME
git checkout BRANCHNAME
git status
vi FILENAME
git add FILENAME
git commit -m "DESCRIPTION"
git push orign BRANCHNAME
```

<a name="Managing_the_Upstream"></a>

## Managing the Upstream (a.k.a. Brining in collaborators changes)


<center>
<iframe width="576" height="360" src="https://www.youtube.com/embed/jTWRyUIZAys" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>


Review of commands used in video:
``` bash
git clone URL
git branch BRANCHNAME
git checkout BRANCHNAME
cat > FILENAME
git add FILENAME
git commit -m "DESCRIPTION" 
git remote add REMOTENAME URL
git fetch REMOTENAME
git config -l 
git remote add 
git fetch
git rebase REMOTENAME/master
git merge origin master
```

