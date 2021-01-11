## How to Correctly Contribute to the Disciple Tools Repository

Keeping track of upstream, origin, and local can be a bit overwhelming sometimes. Here's a step-by-step process that shows you how to contribute to DiscipleTools and not go mad in the process. :)

Follow these steps to make sure your code gets neatly added to the Disciple Tools Theme Repository.

&nbsp;

### 1. Fork the repo
The fork will be called called **origin**

In order to fork the main DT repository, go to it and click the `Fork` button on the top-right corner of the page.

&nbsp;

### 2. Clone the fork
The cloned fork will be called **local**

`git clone https://github.com/[YOUR_GITHUB_USERNAME]/disciple-tools-theme.git`

&nbsp;

### 3. Keep your fork up to date with upstream
The original Disciple.Tools repo will be called **upstream**, but first we have to set it up.

`git remote add upstream https://github.com/DiscipleTools/disciple-tools-theme.git`


To check that everything has been set up correctly, run:

`git remote -v`

&nbsp;

**You should see something like this:**
&nbsp;

`origin	https://github.com/prykon/disciple-tools-theme.git (fetch)`

`origin	https://github.com/prykon/disciple-tools-theme.git (push)`

`upstream	https://github.com/DiscipleTools/disciple-tools-theme.git (fetch)`

`upstream	https://github.com/DiscipleTools/disciple-tools-theme.git (push)`

&nbsp;

We're almost there! Now we need to create a local branch directly from DT's upstream repository's master branch (the latest stable version of the code).

&nbsp;

### 4. Create a new local branch from upstream
Say you want to creat a new branch for the feature you want to create or for the bug you want to fix. First, we need to make sure your forked repo has the latest stable version of the code from DiscipleTools. In other words, we need to fetch the upstream code. To do this, type:

&nbsp;

`git fetch upstream`


And then create a new branch from upstream master:

`git checkout -b new-branch upstream/master`

&nbsp;

This new branch will not contain remnants of previous commits that were merged in via the squash method. You should recieve a message like the following:

`Branch 'new-branch' set up to track remote branch 'master' from 'upstream'.`

`Switched to a new branch 'new-branch'`


&nbsp;

### All set!
The 'new-feature' branch should be a mirror of the upstream repository's master branch. Check your branches by running the following command:

`git branch`

&nbsp;

### 5. Commit your code
After you work your code-writing magic, commit the changes to your fork (AKA, origin), making sure you specify the branch name that doesn't yet exist on your fork.

`git commit -am 'my new awesome commit description goes here'`

`git push origin new-branch`

&nbsp;

### 6. Send the code over to DT
In order to get your code into the official Disciple.Tools repository for all the world to enjoy, you need to create a pull request to the upstream repository.

To do this, go to your fork's Github page, select the _new-feature_ branch and Click 'Compare & pull request' and then follow the steps shown on the page.

If there are no problems, the Disciple Tools team with merge your code with the main repository.

&nbsp;

### 7. Cleaning up
After your code has been pulled into DT, you should clean up your local repo because branches can start to clutter your workspace. To do this, we recommend deleting the `new-feature` branch by typing:

`git branch -d new-feature`

And then push those changes to your fork:

`git push origin --delete new-feature`

&nbsp;

### Done!
Thanks for contribuiting your time and skill on this project. We greatly appreciate every line of code you send our way.