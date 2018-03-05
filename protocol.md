# Protocol

A simplified overview of the process:
- [Fork the repository](https://help.github.com/articles/fork-a-repo/).
- Add your code.
- Submit a [_pull request_](https://help.github.com/articles/creating-a-pull-request/) to the project owner.

## Step 1: Forking a repository

By creating a "fork," you are producing a personal copy of someone else's project [^1]; in this case, a repository owned by Strategic Machines.

To fork a repository and get a working copy of it on your computer:
1. On GitHub, navigate to the repository you wish to fork.
1. In the top-right corner of the page, click __Fork__ [^2].

That's it. You just forked the repository.

## Step 2: Create a local clone of your fork

Now that you've forked the repository to which you'll be contributing, you need to get a copy of it on your computer. To achieve this: 

1. Navigate to __your fork__ of the repository on GitHub
1. Under the repository name, click __Clone or Download__.
1. Copy the given URL.
1. Open the Terminal in your computer.
1. Navigate to the directory where you want to clone the repository
1. Type `git clone` and then paste the URL copied in bullet point 3 of this section. It should look like this, with your GitHub username and the repository's name instead of `YOUR-USERNAME` and `YOUR-FORK`: 
    -  `$ git clone https://github.com/YOUR-USERNAME/YOUR-FORK`
1. Press __Enter__. This will start the cloning process.

That's it! Now you have a local copy of your fork.

## Step 3: Configuring Git to sync your fork with the original repository.

As stated previously, when you fork a repository, you're making a personal copy of the original. The original repository is called the _upstream_. Over time, the upstream will change; new files will be added (or removed), bugs will get fixed, updates will be made. Sooner or later you will, more than likely, need to update your fork in order to bring in changes from the upstream (it's also good practice to regularly sync your fork with the upstream repository)  [^3]. To do this, you can configure Git to pull changes from the upstream repository into the local clone of your fork [^4].

After you're done creating a local copy of your fork:

1. Navigate to the original repository on GitHub.
1. Under the repository name, click __Clone or Download__.
1. Copy the clone URL
1. In your computer's terminal, go to the directory where you cloned your fork.
1. Once in said directory, type `git remote -v` and press __Enter__. This will show you the repository that is currently configured as the remote for your fork.
    ```
    $ git remote -v
    origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
    origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
    ```
1. Type `git remote add upstream`, and then paste the URL copied in bullet point 3 of this section. It should look like this:
    - `git remote add upstream https://github.com/ORIGINAL-OWNER/ORIGINAL-REPOSITORY.git`
1. Type `git remote -v` again. You should now see the URL for your fork as `origin`, and the URL for the original repository as `upstream`.
    ```
    $ git remote -v
    origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
    origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
    upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
    upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)
    ```
You've successfully specified an upstream repository for your fork! If, at any point, __you need__ to sync your fork with the upstream repository, you only need to run [a few Git commands](https://help.github.com/articles/syncing-a-fork/)

#### 3.1 Syncing your local fork with the original repository

Before syncing your fork with upstream, __make sure you've completed the previous steps in this section__. When you're ready:

1. Open the Terminal in your computer.
1. Make sure you're in the directory of your local project.
1. Type `git checkout master`. If you aren't in it already, this command will switch you to the `master` branch of your local fork.
    - To check which branch you're currently on, type `git branch`.
1. Type `git fetch upstream`; this will fetch the branches and their respective commits from the upstream repository [^5]. 
1. Type `git merge upstream/master`; this will merge the changes from `upstream/master` into your local `master` branch. By doing this, your fork's `master` branch will be synced with the upstream repository __without losing your local changes__.

## Step 4: Create a branch

## Step 5: Merge you branch with your local master

## Step 6: Push to your fork on GitHub

## Step 7: Submit a pull request to the owner of the repository.




[^1]: [Forking Projects](https://guides.github.com/activities/forking/) - A guide by GitHub
[^2]: [Fork a Repo: Fork an example repository](https://help.github.com/articles/fork-a-repo/#fork-an-example-repository) - GitHub Documentation
[^3]: [Fork a Repo: Keep your fork synced](https://help.github.com/articles/fork-a-repo/#keep-your-fork-synced) - GitHub Documentation
[^4]: [Fork a Repo: Configure Git to sync your fork with the original repositotry](https://help.github.com/articles/fork-a-repo/#step-3-configure-git-to-sync-your-fork-with-the-original-spoon-knife-repository) - GitHub Documentation
[^5]: [Syncin a fork](https://help.github.com/articles/syncing-a-fork/) - GitHub Documentation