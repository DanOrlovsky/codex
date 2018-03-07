# Protocol


A simplified overview of the process:
- [Fork the repository](https://help.github.com/articles/fork-a-repo/).
- Add your code.
- Submit a [_pull request_](https://help.github.com/articles/creating-a-pull-request/) to the project owner.

## Step 1: Forking a repository

By creating a "fork," you are producing [a personal copy](https://guides.github.com/activities/forking/) of someone else's project; in this case, a repository owned by Strategic Machines.

To fork a repository and get a working copy of it on your computer:
1. Go to the repository you wish to fork on GitHub.
1. In the top-right corner of the page, click __Fork__.

That's it. You just forked the repository.

---

## Step 2: Create a local clone of your fork

Now that you've forked the repository to which you'll be contributing, you need to get a local copy of it on your computer. To achieve this: 

1. Go to __your fork__ of the repository on GitHub.
1. Under the repository name, click __Clone or Download__.
1. Copy the given URL.
1. Open the Terminal in your computer.
1. Navigate to the directory where you want to clone the repository
1. Type `git clone` and then paste the URL copied in bullet point 3 of this section. It should look like this, with your GitHub username and the repository's name instead of `YOUR-USERNAME` and `YOUR-FORK`: 
    -  `$ git clone https://github.com/YOUR-USERNAME/YOUR-FORK`
1. Press __Enter__ to start the cloning process.

That's it! Now you have a local copy of your fork.

---

## Step 3: Keeping your fork in sync with the original repository.

As stated previously, when you fork a repository, you're making a personal copy of the original. The original repository is called the _upstream_. Over time, the upstream will change; new files will be added (or removed), bugs will get fixed, updates will be made. Sooner or later you will, more than likely, need to update your fork in order to bring in changes from the upstream (it's also good practice to [regularly sync your fork](https://help.github.com/articles/fork-a-repo/#keep-your-fork-synced) with the upstream repository). To do this, you can [configure Git to pull changes](https://help.github.com/articles/fork-a-repo/#step-3-configure-git-to-sync-your-fork-with-the-original-spoon-knife-repository) from the upstream repository into the local clone of your fork.

After you're done creating a local copy of your fork:

1. Go to the original repository on GitHub.
1. Under the repository name, click __Clone or Download__.
1. Copy the clone URL
1. In the terminal, go to the directory of your project.
1. Inside the project's folder, type `git remote -v` and press __Enter__. This will show you the repository that is currently configured as the remote source for your fork.
    ```
    $ git remote -v
    origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
    origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
    ```
1. Type `git remote add upstream`, paste the URL copied in bullet point 3 of this section and press __Enter__. It should look like this:
    - `git remote add upstream https://github.com/ORIGINAL-OWNER/ORIGINAL-REPOSITORY.git`
1. Type `git remote -v` again. You should now see the URL for your fork (on GitHub) as `origin`, and the URL for the original repository as `upstream`.
    ```
    $ git remote -v
    origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
    origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
    upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
    upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)
    ```
You've successfully specified an upstream repository for your fork. If, at any point, you need to _sync your fork with the upstream repository_, all you need to do is run [a few Git commands](https://help.github.com/articles/syncing-a-fork/)

#### 3.1 Pulling changes from the original repository into your fork.

Before syncing your fork with the upstream, __make sure you've completed the previous steps in this section__. When you're ready, go to the Terminal and:

1. Make sure you're in the directory of your local project.
    - To check your _present working directory_ by entering `pwd`.
1. Type `git checkout master`. If you aren't in it already, this command will switch you to the `master` branch of your local clone.
    - To check which branch you're currently on, type `git branch`.
1. Type `git fetch upstream`
    - This will [fetch the branches and their respective commits from the upstream repository](https://help.github.com/articles/syncing-a-fork/). 
1. Type `git merge upstream/master`
    - This will merge the changes from the `upstream/master` branch into your local `master` branch. By doing this, your clone's `master` branch will be synced with the upstream repository and you __won't lose local changes__.

---

## Step 4: Create a branch

Branches are ideal when you need to work on specific features or fixes of a project in an isolated environment. This allows you to safely experiment with ideas without affecting the `master` branch until your code is ready to be merged. When taking on __work items__ from the marketplace (link to markeplace?), you will be creating a _descriptively named branch_. In other words, a branch with a name that describes the work you will be doing in it; the feature you might be adding, the bug you might be fixing. 

To create a new branch for your workitem, make sure you're in the directory of your project. Then: 

1. Type `git checkout -b` followed by the name of the branch.
    ```
    $ git checkout -b work-item7
    Switched to a new branch 'work-item7'
    ```
That's it! You're ready to start working on your new branch. For the sake of brevity and to keep these guidelines focus specific, we won't delve deeper into the subject of branching. However, if you want to learn more about it, we reccommend you read [this page](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging) from the Git documentation.

---

## Step 5: Merge you branch with your local master

Once you're done developing in your branch, you can merge it __into__ your local `master` branch. To do this:

1. Make sure you have commited all your work before switching back to `master`. In
  other words, make sure that there are no _unstaged and uncommited_ files left in your branch, otherwise Git won't let you switch branches.
1. Type `git checkout master` to switch back to `master`.
1. Type `git merge work-item7` (in your case, the name of your branch); this will merge the branch you just worked on into your `master` branch.

---

## Step 6: Push to your fork on GitHub

Great, now the work you did in your branch has been implemented into your `master` branch. But this updated `master` exists only locally on your computer. If you go to __your fork__ of the originally repository on GitHub, you'll notice that your local changes aren't there... yet.

After you've succeeded in merging your branch into `master`, it's time to push these changes to your fork on GitHub. At this point, all you have to do is run one command in your terminal:

1. `git push`

Now go back to your fork on GitHub and refresh the page; your local changes are now there!

---

## Step 7: Submit a pull request to the owner of the repository.

Pull requests are created to propose changes and collaborate to a repository, but before going any further, let's do a brief recap. By this point you have: 

- Finished your work in a __local__ branch
- Merged that branch into your __local__ `master` branch
- Pushed those changes to the __remote__ `master`.

This means that the work you did on your computer has been uploaded to your fork on GitHub; at _this_ point, your fork is in sync with your clone. Great!

Now you need to create and [submit a pull request](https://help.github.com/articles/creating-a-pull-request/) to Strategic Machines so that your work can be reviewed and, if approved, merged into the original repository (also known as the upstream). To submit a pull request:  

1. Go to your __Fork__ on GitHub.
1. Under __Clone or download__, click on __Pull request__.
1. 

---