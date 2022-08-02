## Introduction

GitHub is a platform that encourages *social coding*, and because of this, GitHub has features that promote collaboration.

In this lesson, we are going to discuss a few topics related to code-sharing and play a bit with a remote repository to test them out.

## Forking

### What is Forking?

**Forking a repository is taking someone else’s code, and creating your copy of it.** Eventually, the changes you make in the fork may be included in the original repository. On GitHub, this means taking someone’s remote repo and copying it to your own remote repo.

*Don’t forget*:

- remote repos live on GitHub so with forking you are making a copy of someone’s repository hosted on GitHub and the copy you are making will be hosted on your GitHub profile,
- everything related to forking happens online, on GitHub.

![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_805f8fefe6d70684ee1cdc7fb6add29f.gif)

Sounds like plagiarism, huh? Not really. There are a few different scenarios where this is fine:

- **Open Source Contributions** - Most public GitHub repos are there for you to contribute to. Whether it is [express.js](https://github.com/expressjs/express) or [jQuery](https://github.com/jquery/jquery), they openly welcome contributions. The only method to do this efficiently is by forking their repositories.
- **Creating a new project** - Sometimes, you or a group of people may not like how an open-source project is being run. If the project is open-sourced and properly licensed, then you can fork the project and run your own version. Check out this list of [forked software projects](https://en.wikipedia.org/wiki/List_of_software_forks).
- **Submitting work here at Ironhack** - We have a central repo of all of the exercises you will be working on during the course. To submit your work during the course, you will be making forks of these repos.

### How to Fork

Luckily, forking on its own is super simple. Navigate to [Ironhack’s GitHub practice](https://github.com/ironhack-labs/lab-github-practice) repo and click the fork button in the upper-right corner of the page:



![git-fork](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-fork.png)



In the following dialog, choose your own account as the place to fork:



![git-fork-2](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-fork-2.png)



Now you have your own version of our repo!



![git-fork-3](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-fork-3.png)



The question now is, **how do we get this repo onto our local machine**? So this is where the cloning comes in to save.



## Cloning

### What is Cloning?

**Cloning a repository is simply taking a remote repository (remote repository is the repository that lives on GitHub) and copying it to your local machine**.

This can be useful in a couple of different scenarios:

- You have created a fork of a project and now need to copy it to your computer so you can make some changes and be able to make these changes available to others;
- You are collaborating on a project where someone has invited you to their repo as a *contributor*, such as a private repo at a company, so you need to copy it to your computer and start making some changes.



![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_79b2326077f2cd47beedda69c7ef3d91.gif)



### How to Clone

Now that we have forked our own version of the exercise repo, we need to copy it to our computer so we can work on it.

![:tada:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/tada.png) **On your own copy of the repository**_, click the **Code** button, and copy the link to your clipboard:



![git-clone-copy-url](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-clone-copy-url.png)



Then, in your terminal, navigate where you would like to clone the repo. In the below example, we assume you might have a “code” repository on your Desktop and you would like to place the clone there:

```
$ cd Desktop/code # You can create this directory if you don't have it
$ git clone < paste here link you just copied to your clipboard >
# example: git clone https://github.com/sandrabosk/lab-github-practice.git
```



At this moment you could be asked to enter your GitHub username and password to be able to successfully clone the repository. This being said, you would be presented with something along these lines:

```
$ git clone https://github.com/sandrabosk/lab-github-practice.git
Username: your_username
Password: your_token
```



If you carefully read the previous lesson about “GitHub Basics” and if you followed the steps to create the **Personal Access Token**, you would enter the token instead of the password (you should copy the token and paste it to the password field).

If you missed doing this step and you don’t have the token, please refer back to the lesson “GitHub Basics” and find the paragraphs that explain how to **Create a Personal Access Token** and **Using a token on the command line**. Follow the steps given there and when you have created a token, make sure you save it and use it to be able to proceed with the cloning process.

If nothing of the above happened, then the last case scenario is that you are presented with a warning in your terminal:

```
# remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
# remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
# fatal: unable to access "..." : The requested URL returned error: 403
```



If this happens, this means you missed doing the Personal Access Token setup so go ahead and create the token (refer to the steps provided in the “GitHub Basics” lesson) and repeat the step where you clone the repo. If you are still getting the warning and you are not prompted to enter your username and password, open up the keychain to replace your old password with the token. This step is also described in detail in the previously mentioned lesson so if unsure what to do, check out the guidelines provided there.



If everything worked out, you should have a new folder called `lab-github-practice` in the “code” repository (locally):

```
# when inside "code" repo run
$ ls
# => lab-github-practice
```



**Cloned repositories already have a Git repo in it. \*You do not need to run `git init` again\*.**



```
$ cd lab-github-practice
$ ls -a
# .          ..         .git       index.html
```

Open the repo in VSCode:

```
Copy
$ code .
```



In case you run into an error opening the files using `code .` command, you might want to check this link [“code .” Not working in Command Line for VSCode on OSX/Mac - StackOverflow](https://stackoverflow.com/questions/29955500/code-not-working-in-command-line-for-visual-studio-code-on-osx-mac).



**Exercise**

In the `index.html` of the portfolio site we have just cloned, there is some filler text that you should fill in with your own data.

- Where it currently says **Welcome to Ironhacker’s Page**, fill in your own name for Ironhacker.
- In the two lists **Things I like** and **Things I don’t like**, fill in the `li`s with your own data.

After you have made the changes, *add* and *commit* those changes. The repository is now on our computer, and we have made changes. Now let’s find out how to submit our changes to the master repo of the original owner (in our case, that’s Ironhack since we forked the original repo from Ironhack at the very beginning).



## Pull Requests

### What is a Pull Request?

**A pull request is a way of notifying the owner of the original repository that you have made some changes and would like to \*merge\* those changes into their repository, at the owner’s discretion**.

To understand why you would make a pull request, you first need a slightly different perspective. Right now, you are *one* person, working on *one* file, in *one* project.

In your professional ventures, open-source projects, and even later in the course, when you collaborate on some group exercises, it can be *very tricky* to manage which changes are made, how they are made, and avoid conflicts.

For example, let’s take a look at all of the people trying to contribute to the `express.js` framework, which we will use later in the course - [ExpressJS GitHub - Pull Requests](https://github.com/expressjs/express/pulls).

These are people who have all forked the repository, made some changes, and then created a pull request. Why?

- **It gives the owner of the repository a chance to review the code before including it in the codebase -** Open source projects are *open* after all, but they do have standards. Often project owners will want to review code to make sure there aren’t breaking changes or even dangerous hacks in the PR (pull request). In other cases, it may also be your boss checking your code out to make sure you are doing a good job.
- **It leaves room for discussion between interested parties** - In open source projects, there are often many stakeholders who want to approve or deny features before they are included in the project. For instance, check out [this pull request](https://github.com/expressjs/express/pull/2874). Don’t worry about the subject matter, it won’t make sense for quite a while, but you’ll get there. ![:wink:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/wink.png)



### How to Pull Request

Your local changes to our practice project should be staged and committed by now…*right*? The next step is to push to your repo.

If you remember in a previous lesson, we had to add a *remote* to our repo to be able to push to GitHub. A bonus of cloning a repo from GitHub is that the remote is already connected:

```
$ git remote -v
# origin    https://github.com/<your-github-username>/lab-github-practice.git
```

![:bulb:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/bulb.png) Remember that the remote name `origin` is simply GitHub convention for the name of your remote repository. In the previous example, it was called `github-repo`, and can be called anything. By default, though, GitHub will name the remote `origin` when you clone a repository.

The next step, after we made some changes, is to *push* those into your own repository:

```
$ git add .
$ git commit -m"add things i like"
$ git push origin master
```

If this succeeded, you will be able to see the commit message you created (image 1) and the changes in the file you made (click on the commit message to see the view as on image 2 below) :



![git-push-to-fork](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-push-to-fork.png)



![git-push-to-fork-details-view](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-push-to-fork-details-view.png)



Now you are ready to move on to the pull request.

When on **your GitHub** and after navigating to the repo you previously forked `lab-github-practice` and click on **Contribute** and then **Open pull request**:



![git-open-pr](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-open-pr.png)



After clicking on it, you will be redirected to the **original** repository, which you originally forked, and you will see the changes you made. You will be prompted to create a new pull request by clicking on the button **Create pull request**:



![git-open-pr-2](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-open-pr-2.png)





**Click "Create pull request"**



Finally, you will be presented with a dialog box asking for a title and description of the pull request. Typically, this will be used to describe the changes you have made. At Ironhack, we use this as a tool to check your work.

- In the title, include your name and the campus you are attending; “Ironhacker - Miami” and “Fork exercise completed”.
- In the description, leave one (or many) of your learnings or struggles in learning how to use git and GitHub.

Hit the “Create pull request” button, and that is it!



![git-open-pr-3](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-open-pr-3.png)



## Quick Reference

Here you have the most important commands you should have learned in this lesson:

**Cloning project**

```
Copy
$ git clone <repository-url>
```

![:+1:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/+1.png) To keep in mind: You don’t have to fork someone’s repository to be able to clone it - these two are completely independent commands. You will have to fork first only if it is expected from you to submit/show changes you made and to make them available to other collaborators on the same project. In any other case, you can click on the `Clone or download` button and grab the link and in your terminal run `git clone <the-url-of-project-you-want-to-clone>`.

## Summary

In this lesson, we discussed collaboration on GitHub:

- **forking** repository - creating a copy of a remote repository on your GitHub,
- **cloning** repository - downloading a remote git repository to your machine using **`git clone`**.
- **merging** the changes you made locally on your computer and pushed on your GitHub into the forked repo with the original repo using a **pull request**.

Collaboration is one of GitHub’s primary purposes. Using the tools that we have highlighted in this section, you can do so many things, among which is submitting work at Ironhack and working on a dev team in the real world.