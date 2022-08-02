## Introduction

We have learned in a previous lesson that **Git is a VCS for keeping track of changes you make to files and folders in your projects**. So far, we know that theoretically, and let’s see how all this looks in practice.

## Creating a Repository

Let’s start by creating a directory to play with Git. Navigate to desktop and create a folder called *git-practice*:

```
// we assume you are already on Desktop
$ pwd
// => /Users/<your-username>/Desktop
 
$ mkdir git-practice
$ cd git-practice
$ touch data.txt
$ code .
```

Add some text to `data.txt`. Feel free to change the data:

```
Name: Ironhacker
Age: 25
Favorite Color: Yellow
```

### `git init` and the hidden `.git` folder

We discussed in the previous lesson how we use Git to keep track of changes in files and folders on your local machine, but how is this done?

**Don’t assume this happens all the time since that is not the case**. To be able to track the changes you made in your file, the first thing you have to do is **to initialize this folder as a git repository**. *We will explain this.*

Inside `git-practice` folder, run the following command:

```
Copy
$ git init
```

*You should have `git` installed on your computer. You can check it out by running the following command in the terminal*:

```
Copy
$ git --version
```

*The output should be your git version, something like `git version 2.33.1`*. (If you see some other numbers, they should be the same or greater than this number.)

`git init` is the command to signal to Git that the folder you are currently in will now be a [Git repository](https://en.wikipedia.org/wiki/Software_repository). From the point forward, Git will track all changes to the files and folders inside of that folder.

However, remains the same question - how does it keep track of these changes?

Let’s run an `ls` command to show hidden folders and files inside of the folder:

```
$ ls -a
# => .        ..       .git     data.txt
```



![:exclamation:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/exclamation.png) `# =>` denotes a return value. You do not have to type this into your terminal.



In addition to data.txt, we have a new folder called `.git`. We did not create this directory ourselves - Git did when we ran the `git init` command.

**The `.git` repository is where Git keeps track of all of the changes you make, and \*much\* more**. There is no point in going into the specific details of the folder now. However, we will reference it as the lesson progresses.



![:bulb:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/bulb.png) If for some reason you run `git init` in a folder you didn’t intend to make a git repository, you can simply remove the `.git` folder using `rm -rf`:

```
$ git init # => to initialize folder as Git repository
$ rm -rf .git # => to remove git (tracking)
```



**Be careful, though. `rm -rf` is a dangerous command that can erase everything on your system if misused**.



### Where to create a `.git` repository/ where to run `git init`?

(*We will use naming git repo/repository, but you can see it the same as git folder/directory. Repo/repository is more common though.*)

It may be easier to begin this by telling you where to **not create it**, and why.

Most of the time, you will want to create the Git repository in a specific project folder.

**You do not want to create a Git repository in a high-level folder, such as `Documents`, or your home(`~`) directory.** Why? Git keeps track of the folder and *all subfolders of that folder*. This means that if you create a Git repository in your home(`~`) directory, you will be tracking all of the changes to files and folders on your local user’s computer.

This is bad because:

- it is unnecessary;
- when you go to create a Git repo later on inside of a project, you may run into issues;
- when you eventually want to store your Git repos on GitHub later, you may accidentally push sensitive information. ![:-1:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/-1.png)

At Ironhack, you will be creating *many* projects and folders to track with Git. Take a look at the following tree to give you an example of where you should be creating Git repos:

```
├── project-1
│   ├── index.html
│   └── style.css
├── project-2
│   ├── index.html
│   └── style.css
├── project-3
│   ├── index.html
│   └── style.css
├── project-4
│   ├── index.html
│   └── style.css
└── project-5
    ├── index.html
    └── style.css
```

In this folder, we have five projects, all with an *index.html* and *style.css*. We suggest creating your git repository **in each project**, as so:

```
├── project-1
│   ├── .git
│   ├── index.html
│   └── style.css
├── project-2
│   ├── .git
│   ├── index.html
│   └── style.css
├── project-3
│   ├── .git
│   ├── index.html
│   └── style.css
├── project-4
│   ├── .git
│   ├── index.html
│   └── style.css
└── project-5
    ├── .git
    ├── index.html
    └── style.css
```



**The following are examples of how \*not\* to structure the directory:**

![:x:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/x.png)



```
├── .git
├── project-1
│   ├── index.html
│   └── style.css
├── project-2
│   ├── index.html
│   └── style.css
├── project-3
│   ├── index.html
│   └── style.css
├── project-4
│   ├── index.html
│   └── style.css
└── project-5
    ├── index.html
    └── style.css
```

![:x:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/x.png)



```
├── .git
├── ironhack
│   ├── .DS_Store
│   ├── project-1
│   │   ├── index.html
│   │   └── style.css
│   ├── project-2
│   │   ├── index.html
│   │   └── style.css
│   ├── project-3
│   │   ├── index.html
│   │   └── style.css
│   ├── project-4
│   │   ├── index.html
│   │   └── style.css
│   └── project-5
│       ├── index.html
│       └── style.css
└── prework
    └── git-practice
        ├── .git
        └── data.txt
```



## Viewing Changes: `git status`

Let’s return to our `git-practice` folder. We have already run `git init`, and Git is keeping track of our changes. We currently have one file in the folder - *data.txt*.

How can we tell what Git is keeping track of? The answer is a command that you will use very often while working on projects: **`git status`**.



**`git status`** tells us what files and folders are being tracked, and what their current status is according to Git.



```
Copy
$ git status
```



![git-status](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-status.png)



Git is telling us that we should pay attention to right now is the one that says **Untracked files**. `data.txt` is *untracked* because we have created it on our file system, but have not told Git to watch it yet.

We will return to and reference Git status as we continue the lesson, but let’s figure out how to add a file for Git to track.

## Staging Changes: `git add`

### Staging a Single File

Currently, `data.txt` is on our file system, but not being tracked by Git. Files and folders in this state are referred to as our **working directory**. To track these files with Git, we must *add* them to our *staging area*.



The staging area is a place where we have notified Git that something will be tracked.


![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_258b1f574550a0838d42ae2a6f84bdd1.png)

To add a file to the staging area, let’s use the `git add` command:

```
$ git add data.txt
$ git status
```



![git-status-2](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-status-2.png)



Now instead of saying “Untracked Files”, Git is telling us that `data.txt` is staged, and in the section *changes to be committed*.

We will discuss committing shortly, but for now, we can see that Git is now tracking our file.

### Staging Multiple Files

Often in projects, we will want to stage multiple files at the same time. This can be done in a few different ways.

Let’s add some new files to play around with this:

```
$ touch file1.txt file2.txt file3.txt file4.txt file5.txt
$ git status
```



![git-status-3](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-status-3.png)



Currently, `data.txt` is *staged*, but the other five files are not.

Let’s stage `file1.txt` and `file2.txt`.

```
$ git add file1.txt file2.txt
$ git status
```



![git-status-4](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-status-4.png)



On second thought, I would like to stage all of the files in my project:

```
$ git add .
$ git status
```



![git-status-5](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-status-5.png)



Everything is staged!

### Un-staging Files - `git reset`

It looks like we actually don’t want to add `file5.txt` to our staging area. We have made a mistake, so let’s fix it. We can use the `git reset` command to remove a file from the staging area.

```
$ git reset file5.txt
$ git status
```



![git-status-6](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-status-6.png)



Now, `file5.txt` is back in our working directory, and is no longer staged!

## Saving Changes: `git commit`

### What is a *Commit*?

The question you may have been asking before this point is: *staging for what?* The answer lies in the screenshots. You have noticed files in the staging area are labeled with **“Changes to be committed”**.

A *commit* in Git **is a snapshot of the state of the files and folders in your project, as well as the content in them**.

Your projects are going to be evolving and changing with time. As you add content and modify them, their *state* changes. As their state changes, commits will capture that point in time.

![:bulb:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/bulb.png) **State** in computer science and web development is a term used to describe the status of an object, folder, files, etc. and its attributes or contents.

If `data.txt` contains: `"Hello"` and we modify that file to say: `"Goodbye"` the *state* has changed.



![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_fac448c90eead6e3e84bf404b3999f85.png)



Using commits in Git will:

- help you revert mistakes to a previous working version (kind of *undo* button thing);
- enable you to collaborate with other developers on your projects without colliding and
- keep track of *who* made changes, and *when* they did it.



For example, check out this sample commit log of a project’s evolution:



![git-log](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-log.png)



### How to Make Commits

We can make commits using the `git commit` command. This will take any files in our staging area, and create a new commit to our repository.

Let’s take a look at the following diagram for some more visual insight:



![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_9e61fd9a3290806c060a20547f3ad946.jpg)



We have already added files to our staging area from our working directory, and now we need to move them permanently to our repository. The state of our project will forever be frozen in that snapshot.



```
$ git commit -m "Initial commit - Create files, add data"
$ git status
```



![:bulb:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/bulb.png) `git commit -m` means we will provide a message with our commit. This will become more useful later, but for now, note that you should leave a **detailed and descriptive message** about what you have done in that commit.

**Make a commit message in the present tense - as someone gave you a ticket on which they told you what to do**.

This is useful when you need to figure out what changes you have made in the past, and when they were done.

*What happened to our files?* When we create commits, it removes the files from the staging area, because they have been committed. The only remaining file is `file5.txt`, which we did not add to the staging area.

Great. Now our files are committed and stored in Git, but how can we see commits that we have made previously and what we have done?

## Revisiting and Viewing Commits: `git log`

At some point in the future, it is likely we will want to view all of the changes to our project. Besides, we may want to revert our project to a previous snapshot.

The `git log` command is used to view commits and data about those commits. Let’s give it a run and see what happens:

Run the following to see the historical log of the commits that are made in the project:

```
Copy
$ git log
```



![:bulb:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/bulb.png) Press `q` to exit the log dialog screen in your terminal.

Contained in this dialog is our commit and some data about that commit. Each commit has:

- **Commit SHA**(for example: `commit 905616a7252c247f3244bf6ca00faeeba324a26f`) - You can think of this as a unique ID for each commit. This can be used in the future to revert to this commit, remove the commit, or combine multiple commits.
- **Author** - The author attribute is useful when working with teams to see who did what.
- **Date** - Date when the commit was created.
- **Message** - The message we left when making the commit. This gives us some context as to what was done at that point. **This is why it is crucial to leave detailed and descriptive commit messages**.

Let’s make another commit and see how the log changes:

```
$ git add file5.txt
$ git commit -m "Add file5 to repo"
$ git log
```

Now you should see the last commit showing the message you just added - something along these lines:



![git-log-2](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-log-2.png)



Our newest commit just showed up!

![:bulb:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/bulb.png) Like most Git commands, `git log` is extremely customizable in how the output can be formatted. Check out the [Advanced Git Log](https://www.atlassian.com/git/tutorials/git-log) article for more details.

## Quick Reference

Here you have the most important commands - don’t try to memorize them but instead keep this reference open every time you go through this process (with the time and repetition you will know these by heart):

**Initialize a repository**

```
Copy
$ git init
```

**View changes in the repository**

```
Copy
$ git status
```

**Adding files**

- single file

```
Copy
$ git add <file-name>
```

- all files

```
Copy
$ git add .
```

**Committing file(s) to staging area**

```
Copy
$ git commit -m"<commit-message>"
```

**View changes history**

```
Copy
$ git log
```

## Summary