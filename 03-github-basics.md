## What is GitHub?

As previously discussed, GitHub is a tool to collaborate with others (DVCS) using Git. In short, GitHub allows us to host our Git repositories in the cloud so that others can share them.

GitHub also has features for:

- **Managing Repos** - Team collaboration can be tricky. When multiple people are working on the same project, it is hard to find a source of truth and manage who can change the repository. GitHub has features to facilitate this.
- **Project Management** - With open source projects, it is often difficult to state the general direction of the product, transparently display which features are being implemented, and the priority of those features.
- **Social Networking** - GitHub has features to search and find other developers, find repos with a specific language, and follow/unfollow other coders.
- **Organizations and Team Management** - If you have a company or a project in which multiple people are working, you can create an *organization* or a group of people with varying permissions and abilities on the repo.

…and many more.

Currently, we have a local Git repository. As it is, we can’t share this repository with anyone, so let’s change that.

## Create an Account

First things first: if you haven’t done so already, go to [Github](https://github.com/) and create an account.



![github-signup](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/github-signup.png)



![:exclamation:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/exclamation.png) Please, save your *username* and *password* in a safe place. Lots of students forget their GitHub account information. ![:smiley:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/smiley.png)

## Creating a GitHub Repo

There are quite a few ways to create a GitHub repo, but let’s talk about the simplest first. The easiest way to get up and running is to visit GitHub.

Click the plus sign in the upper right-hand corner of the page, and then click “New Repository”:



![github-new-repository](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/github-new-repository.png)



You will be presented with the following page. Fill in the data as it is in the screenshot:



![github-create-new-repo](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/github-create-new-repo.png)



A few things to note about this page:

- **Repository name** (*mandatory*) - This is the name of the repository as it will appear on GitHub. *This does not have to match with the name of your local repository and can’t have any spaces*.
- **Description** (*optional*) - Helpful for outsiders that may stumble upon your project on GitHub.
- **Public / Private** - If your repository is public, that means anybody can discover your project from Google or your profile. Real-world projects frequently will be private repos, so only those that are collaborators can view it. All your repositories during your Ironhack journeys should be public. That will allow your teacher/TAs to check your work, and your future employers can see how you progressed.

Leave the rest as defaults for now and click “Create Repository”. You will then be taken to a page that looks like the following:



![github-create-new-repo-2](hhttps://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/github-create-new-repo-2.png)



What we will take special note of is the following section “**…or push an existing repository from the command line**”, since we already have a local repo on our computers:



![github-create-new-repo-3](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/github-create-new-repo-3.png)



GitHub gives us some instructions here, but let’s take a more in-depth look.

*In case you see the default branch name being different than in the screenshot, that is ok - sometimes you can see `master` and sometimes `main`. Both are in use.

## Adding a Remote Repository: `git remote`

Our remote repository and local repository are two entirely different repos. When we make changes locally, we will have to *push* them to our remote repository - which lives on GitHub (the online cloud). When we want to grab changes that our collaborators made on their computers and pushed into GitHub repo, we will have to *pull* them to our local repository.

![:arrow_up:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/arrow_up.png) - **push** => take changes made locally to a remote repo that lives on GitHub ![:arrow_down:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/arrow_down.png) - **pull** => take changes others made on the same repo and pushed to Github to your local repository

The first step in this is connecting the two repos. This can be done using the `git remote add` command while supplying a few options:

- **alias** - you create an alias in your system for the **remote** repository, which will be pointing to the GitHub repo. It is very common to call this alias **[`origin`](http://stackoverflow.com/questions/9529497/what-is-origin-in-git)**, which we will advise you to do all the time except now. Since this is the learning process and we want you to understand that *origin* is a *remote* repo hosted on GitHub, we will call it *origin* (just for now).
- **GitHub repository URL** - a unique URL that GitHub provides for each repository.

Navigate to your `git-practice` folder on your computer if you are not already there, and run the following:

```
$ git remote add origin https://github.com/your-github-username/git-practice.git
 
# "origin" is a shorthand name for the remote repository where we will push the changes 
# and where from we will pull the changes when our collaborators make them. 
# "origin" is used instead of original repository's URL - and thereby makes referencing much easier
```

To sum it up - we are using `origin` as an alias for our first GitHub project.

![:bulb:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/bulb.png) **You can retrieve the link used in the previous code snippet to your GitHub repo here:**

![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_244a3335704e057b99d686910433978a.png)

This is telling your local GitHub repo: "Add a remote repository called *origin*, and have it point to `https://github.com/your-github-username/git-practice.git`".

We can view a list of remote repos attached to our current local repository by running `git remote` with no options:

```
Copy
$ git remote -v
```



![github-git-remote-origin](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/github-git-remote-origin.png)



You can have as many or as few remote links as you would like. GitHub is only one remote Git hosting service. There are others such as Bitbucket, Gitlab, and many more.



![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_5a42d33001d6f29b90393f7adc87dd3a.png)



Now that our local repository and remote repository are connected via a remote, let’s push some code!



## Adding changes to a remote repository: `git push`



Adding to a remote repository is pretty simple in most situations. We use the `git push` command, along with a couple of options to push our local repository to our remote repository (the first a couple of steps stay the same, you have to do: 1. `git add .`, 2. `git commit -m"some message"` and then push changes to remote repo):

```
# to add all the changes that are made in the repo
$ git add .
$ git commit -m"add a descriptive message"
$ git push origin master
```



![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_f2a5fa0599b3473665aa37a5a767ca0f.gif)



- **`git-push`** - command to push code from a local to a remote repo;
- **`origin`** - an alias of a remote repository we want to push to. Eventually, we may have multiple remote repositories; therefore, we have to name them. However, you will most likely during the bootcamp use the default name which is `origin`, so this command will look like: `git push origin master`;
- **`master`** - the branch we are pushing to on GitHub. We will dive into branches later on.

The command line may prompt you for a username and password, but hold for a second before proceeding. The next couple of lines are important before you go ahead and add your credentials.

### Token authentication requirements for Git operations



![gh-announcement-related-to-tokens](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/gh-announcement-related-to-tokens.png)



> Source: [The GitHub Blog - Token authentication requirements for Git operations](https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/)

What does this mean for us developers? To put it in simple English, after the changes that happened in late 2021 in GitHub authentication process we still *can* use passwords to login to GitHub but to be able to *push* changes to owned or forked repositories, we have to use Personal Authentication Tokens.

Let’s do the set up and enable you to push changes you made in the repository locally to your remote repository on GitHub.



#### Create a Personal Access Token



To successfully create the Personal Access Token, follow the guidelines provided by GitHub organization: **[Creating a token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-token)**.



*Hint 1*: When on step that requires you to set up the *Expiration*, click on the drop down menu and select **Custom** to be able to use calendar picker to set up the custom expiration date. Since you are using all your repositories for learning purposes, we recommend setting up the expiration for 6 months at least so you don’t have to go through the process of updating the token too often. Once the token expires, you will be asked to generate a new token.

*Hint 2*: When asked to *Select scopes*, select **repo**. All the other options are considered as more advanced and not necessary for to be defined for now.

*Hint 3*: After you *generate token*, make sure you copy it to somewhere safe as you will need it at least 2 more time - tp make a first push to your repo and to update your GitHub keychain credentials.

Creating and saving personal token is the last thing you have to do in this step. Proceed to learn how to use it.



#### Using a token on the command line



Once you have a token, you can enter it instead of your password when performing Git operations over HTTPS. Follow the guidelines provided by GitHub organization: **[Using a token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#using-a-token-on-the-command-line)**.



As shown in the provided guidelines, you would **use personal token when \*cloning\* a repo or \*pushing\* to a repo when you are asked to enter your password**.

To push the changes you made in the local repo to your GitHub repo:

```
$ git push origin master
 
Username: your_username
Password: your_token
```



If you are not prompted for your username and password, your credentials may be cached on your computer.

Follow the steps listed below based on your machine:

- **Mac OS**

  You can update your credentials in the keychain to replace your old password with the token.

  Follow the guidelines provided here to successfully update your GitHub credentials on your keychain: **[Updating your credentials via Keychain Access](https://docs.github.com/en/get-started/getting-started-with-git/updating-credentials-from-the-macos-keychain#updating-your-credentials-via-keychain-access)**.

  *Hint*: When you open the keychain and in the search bar type “[github.com](http://github.com/)” you should be able to update the credentials. You should **paste the token in the password field and save the changes** you made.

- **Windows OS**

  You can update your credentials in the [Credential Manager](https://support.microsoft.com/en-us/windows/accessing-credential-manager-1b5c916a-6a16-889f-8581-fc16e8165ac0) to replace your old password with the token.

  1. Go to Credential Manager from Control Panel
  2. Windows Credentials
  3. Find `git:https://github.com`
  4. Edit - on *Password* paste your GitHub Personal Access Token
  5. Save the changes

- **Linux OS**

  Make sure you have locally configured git client with username and email:

  ```
  $ git config -l 
  # user.name=your_username
  # user.email=your_email
  ```

  If you don’t have it configured, follow the steps:

  ```
  $ git config --global user.name "your_github_username"
  $ git config --global user.email "your_github_email"
  ```

  Now when you try to clone GitHub repo or to push to it, you will be prompted to enter your username and password but instead password you should paste the token.



Refresh GitHub, and you should see the code that you have committed!



![gh-files-on-gh-after-pushing](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/gh-files-on-gh-after-pushing.png)



## Pulling From a Remote Repository: `git pull`

Occasionally GitHub repos will have changes that we don’t have on our local computer. This can happen when teammates push code to the repo, or when we update code on GitHub manually.

In this situation, we have to use `git pull` to pull code to our local repository from GitHub.

Let’s start by modifying a file on GitHub. On the repo’s page, click `data.txt`.

On the following page, click the “Edit this File” button:



![gh-edit-file](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/gh-edit-file.png)



Modify anything you want in that file and then click “Commit Changes”:



![gh-commit](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/gh-commit.png)



You have just made a commit to the repository on GitHub, which means that the file has gone through some change in the remote repository on GitHub, but if you open the file locally, nothing has changed.



![gh-updates-vs-local-file](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/gh-updates-vs-local-file.png)



To pull our most recent commit from GitHub, we have to use `git pull`:

```
Copy
$ git pull origin master
```



![img](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_78962c431f06d9d34e095a506d7aac3c.gif)



![git-pull](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/prework/installations/git-pull.png)



As you saw, the command `git pull` takes two arguments. The first being the **remote alias** and the second being the branch.

If you take a look at `data.txt`, it should have your updates from GitHub!

## Quick Reference

Here you have the most important commands you should have learned in this lesson:

**Add a remote repository**

```
Copy
$ git remote add <alias> <github-url>
```

**Pushing to Remote Repository**

```
Copy
$ git push <alias> <remote-branch-name>
```

**Pull changes from GitHub**

```
Copy
$ git pull <alias> <remote-branch-name>
```

However, remember, before being able to push your code to the remote repository, you have to do all the steps we covered in the previous lesson:

1. `git init` => we run this command only once, only when initializing git repo
2. `git add .`
3. `git commit -m"commit message in present tense"`
4. `git push remote-name master`

In the meantime, at any point, you can and should check the changes with `git status`.

## Summary

In this lesson we talked about:

- what GitHub is,
- how to push code from your local repository to the remote repo on GitHub,
- how to pull code from a GitHub repo to our computer (super useful when working with a team)

Git and GitHub are very complex subjects, but the commands shown to you in the last two lessons can take you pretty far.

From now on, use Git to track changes in all of your projects, adding and committing every step of the way. At the end of each day, make sure to push those changes to a GitHub repo. This will get you ready for the course and your future career as a web developer, as any company you apply for will expect you to have some working knowledge of a VCS.