

## Learning goals

After this lesson, you will understand:

- what is a Distributed Version Control System (DVCS),
- how a DVCS works and why is it important,
- what is Git,
- what is GitHub
- the relation between Git and GitHub.

## Introduction

To get more familiar with this subject, start by watching this short **video - [What is Git and GitHub?](https://www.youtube.com/watch?v=uUuTYDg9XoI)** and afterward proceed to the lesson.

## What is a Distributed Version Control System?

A **Distributed Version Control System (DVCS)** or **Version Control System (VCS)** is a system that records changes to a file or set of files over time so you can recall specific versions of these files at any point later.

These systems allow you to have different versions of each file that compose your project so that you can recover an old version, in case you break some of your code (something very common).


![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_63ec103d558b61976562fec9763aba4d.png)

The DVCS usually works together with a **Code Hosting Platform**, where your team can store the project’s code and make it available to share it among members of the team.

In computer programming, **the combination of DVCS with a Code Hosting Platform helps you to work with your team. This is the most powerful tool you will use to combine code created by different team members**.

When two different team members are working on the same file, the VCS is going to help them combine their code, and pick which code to accept if both developers edit the same code.

### Why is it so important to use DVCS in development?

- **Having different versions of the same file gives you massive power over your code**. As said before, if you break something in the latest version of the code, you will be able to recover the old correct version of your code.
- It is also beneficial when you **combine code made by multiple developers into one file**, or even different files into one project. When merging the changes made on the same file but by different developers, you can face multiple conflicts between these changes. (*Don’t worry if you don’t understand this right now, you are going to learn this in-depth later on*.)
- Another cool feature that it provides you is the chance to see **who is the owner of each piece of code**. It allows you to defend how many hours have you been working, of course, but it is funnier to use it to figure out who has messed up the code. ![:bomb:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/bomb.png)

## What is Git?


![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_94d7762076588ec19ea92e8497cf3b0d.png)

**[Git](https://git-scm.com/) is a free and open DVCS** designed to handle computer programming projects with speed and efficiency. It is easy to learn and has a very high performance.

**Git runs locally**. What does it mean? It allows you to use the Version Control System on your laptop. It means that you will have **in your computer** a Version Control System, to recover all code, see what changes you have done, etc.

## What is GitHub?


![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_ffd7f69f32937d26b908851f0aaaac60.png)

**[GitHub](https://github.com/)** is a **code hosting platform** for revision **control and collaboration**. It lets you and others work together on projects from anywhere.

With GitHub, you can do a bunch of things when collaborating on a project:

- control different versions of the code,
- create different branches,
- fork repositories,
- do pull requests,
- see other’s people projects (and learn how they code),
- comment on other’s people code.

*Most of the previously mentioned things probably sound like gibberish, but not for too long. Some of these concepts will be covered now, some during the course but in the end, the most important thing is you will learn what is, when and how to use these tools*.

## How are Git and GitHub related?

At this point, you might notice how Git and GitHub are related.

![:star2:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/star2.png)![:star2:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/star2.png)![:star2:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/star2.png) **Git** allows you to control your code in your *local machine*, while **GitHub** will enable you to **collaborate** with your teammates by *pushing and pulling* the code you and the others have been working on.

![:+1:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/+1.png) Super simplified:

- Git => your Version Control System on a local level (in your laptop);
- GitHub is your team’s Version Control System.

Let’s see an example to understand better how does it work in a two-developer environment.

### How does it work?

(*There will be some terms we’ll use that you won’t understand at this point, but this is okay - try to understand the process overall, and then you will quickly pick up the rest*).

![:helicopter:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/helicopter.png) Help:

- *push* meaning making the code that was made locally, on your laptop, available online (on GitHub) so the others can use it;
- *pull* meaning taking the code from online platform (GitHub) to your laptop so you can re-use it and add/remove things from it.

Okay, now you are ready. ![:wink:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/wink.png)

In the chart below, you can see a typical scenario where two different developers work on a file collaboratively. There are two developers involved here, Mary that will create the file and push it to GitHub, and Bob that will pull this file, make some changes, and push it back to GitHub to share these changes with Mary:



![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_3a5c4dacbd59302f132a8e6b0534464f.png)



Without getting into **how \*exactly\*** the process is executed, and what the commands are, let’s take a look at a high-level view of how two developers can collaborate on a project.

![:one:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/one.png) **File creation**

First of all, Mary creates a file called `file.txt`. Once the file is created, she adds some content to it. Let’s suppose she adds `Hello, world!` and saves the changes. At this point, neither Git nor GitHub have been involved in the workflow.

![:two:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/two.png) **Add the file to git**

Once the **file is ready to share, Mary has to commit it to Git**. (*You are going to learn how to add and commit files to Git in future lessons .*) The most important point here is that **once the file is added and committed into Git, Git generates the first version of the file**.

![:bulb:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/bulb.png) In this step of the process, we have a `file.txt` in our local machine, and we have the *v1* of this file stored into the Mary’s Git locally, on her machine.

![:three:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/three.png) **Push/Pull changes to GitHub**

Once Mary has the file in her local Git repository, she is ready to push this file to GitHub. (*Don’t stress how this will happen, we will get there soon*). By doing this, Mary allows her teammate, Bob, the chance to get this file and make some changes to it.

To do so, Bob has to pull the changes from GitHub to his computer. When Bob pulls the changes from GitHub, two things happen:

- The `file.txt` is added to Bob’s Git repository, on his local machine.
- Automatically, a version of the file appears in Bob’s project, also locally.

![:four:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/four.png) **Update the file**

Once Bob has the file on his computer, he changes the content, and adds the following:

```repl
Hello, world!
Hello, Mary! Thanks for sharing this file! :)
```

Again, as Mary did before, Bob has to add and commit the files to his Git repository before he is able to push them to GitHub. When Bob commits the file changes to his Git repository, Git creates version 2 (*v2*) of the file.

**Current Status**



At this stage, before Bob pushes the changes to GitHub, Mary has **version 1** of the file, while Bob has **version 2** of that same file.

Once Bob has committed the files into his Git repository, he can send them to GitHub by pushing all the changes.

![:five:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/five.png) **Getting the last changes**

Finally, Mary can pull the file from GitHub to her laptop. Again, this means that the file version will be added into her Git local repository, and the file in her project will be automatically updated.

![:white_check_mark:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/white_check_mark.png) **Controlling Versions**

Now, both developers have all both versions of the file in their Git repositories, and the latest version of the file in their project folder. That means they can check out version 1 or 2 whenever they want, to check out who did which changes and what changes are included in each version.

## Summary

In this lesson, you have learned:

- what a Distributed Version Control System is,
- what is Git and GitHub, and
- how two developers can collaborate by using Git and GitHub as a team.