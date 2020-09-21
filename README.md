# Practice working with Git and GitHub

This exercise will guide you through a few key aspects of using Git and GitHub.

By the end of this exercise, you will:
* Know how to create a new repository on GitHub
* Get experience working with local git commands
* Practice navigating and working with command line / terminal commands
* Refresh some basic HTML and CSS

## Prerequisites:
1. Know the basics of how to access and [use your terminal](https://docs.google.com/presentation/d/1rSFTvrLGcTpBszYUOPTsXnL4EfD217g55PAUoIMHogw/edit#slide=id.g9911c0ea01_0_7)
2. Have Git installed on your machine
    - You can check if you have `git` by typing `git version` into your terminal. If you don't get a version number in response, [follow the instructions here on how to install it](https://github.com/git-guides/install-git)
3. Have a GitHub account
    - [Sign up here](https://github.com/join) if you haven't already

## Recommended configuration
There's definitely no single "right answer" when it comes to what development environment is best... try a few things out and see what works for you. The options available may also depend on your OS. As a MacOS user, I personally use and would recommend the following:

* **Code editor:** [Visual Studio Code](https://code.visualstudio.com/)
    * Available for Mac, Windows, and Linux. Free
* **Terminal:** Integrated terminal within Visual Studio Code
    * To access, go to the Terminal menu --> New Terminal (or keyboard shortcut `ctrl` + `~`)
    * I've also used [iTerm2](https://www.iterm2.com/) as a standalone terminal in the past, and would recommend it if you use a different code editor. Also free.
* **Fancy GitHub command line theme:** Some folks noticed my command line configuration during section, which is indeed very handy to see the status of a local git repo. That said, setting it up is not particularly beginner-friendly, so please proceed with caution, and potentially opt to instead set this up with Julia in office hours rather than trying to figure it out on your own. You can find instructions [here for iTerm2](https://gist.github.com/kevin-smets/8568070), and [here for Visual Studio Code](https://gist.github.com/480/3b41f449686a089f34edb45d00672f28) (they share some overlap).

## Core exercise: Building a new project from scratch
Let's imagine you're ready to build a snazzy new prototype in HTML and CSS (ahem, you in Assignment 5). Great! For that, you'll be starting off with a fresh new repository of your own, rather than cloning or forking existing code as we did in section on Sept. 21 -- more on cloning and forking later. 

### 1. Create a new repository on GitHub
First, you'll want to create a new repository that will host your code on GitHub. From a GitHub page, click the + button on the top right, or go straight to [this page](https://github.com/new). 

Give your repository a descriptive name (e.g. `hello-git-exercise`)

I'd recommend adding at least a README file, so check that box.

### 2. Clone your GitHub repository to your local machine
Now, we want to create a local home for this repository so you can start building on it. To do this, you'll want to *clone* the GitHub repository.

Within your terminal, make sure you're within the directory where you want your project code to live. For example, I have a folder called `Developer` where I like to keep code projects, so I would `cd` to that directory.

Once you're in the right place in your terminal, clone your GitHub repository (recommended via HTTPS). If you're looking at your GitHub repository (should be at a URL like https://github.com/jcambre/hello-git-exercise), click the green "Code" button, make sure the HTTPS option is selected, and copy the URL (which should look something like https://github.com/jcambre/hello-git-exercise.git) to your clipboard.

Then, in your local terminal, clone the repository:

```
git clone https://github.com/jcambre/hello-git-exercise.git
```
(where you've of course swapped out the URL for your own URL that's on your clipboard)

> **Now, importantly:** At this particular step, you might be prompted to log into GitHub within your Terminal. To log in, you will first need to *set up a personal access token*. When prompted for your username, input your actual username (e.g. in my case, `jcambre`). The personal access token is what you paste in instead of your password. [Follow these instructions](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token) on setting up a personal access token, and note that when you paste (or type) anything in response to the password prompt, nothing will show up. You just have to trust that it was pasted correctly, and hit enter.

At this point, you should have a copy of the GitHub repository on your local machine. You can check this by issuing an `ls` (list) terminal command, which should show a new folder with the same name as the repository (e.g. `hello-git-exercise`).

Change directories (`cd`) into the folder. If you `ls` within that folder, there should be a file that corresponds to the nearly-blank `README.md` file that GitHub generated for you when the repository was created.

Pat yourself on the back! You now have a local and remote repository for your project's code.

### 3. Create some basic HTML and CSS content
Time to add some code to your project!

First, create a new branch to develop your changes. When you first clone or create a repository (before October 1, 2020), the default branch will be named `master`. Note: thankfully, GitHub is [moving away from this problematic default](https://github.com/github/renaming) to instead name the default branch `main`.

You will want to create a new branch to isolate the particular feature or set of functionality you're working on. In this case, we'll create a branch for `basic-content`. We can create this through the following command:

```
git branch basic-content
```

You won't see a confirmation message in the terminal, but the branch has been created. You can see that it (and all other local branches) exists through the command `git branch`. The branch that you're currently working on is identified by an asterisk.

To switch to the new branch, type:
```
git checkout basic-content
```

Now that you're on this new branch for development, open your project folder within your code editor of choice. Again, at this point, it'll only have whatever files GitHub auto-generated for you.

Create a new file called `index.html`. As a bit of a refresher from previous labs (and good prep ahead of your next assignment), add the following to it:
* Create opening and closing `html` tags
* Within the `html` tags, add a `head`
* Within the `head`, add a `title`
* Add a `body`
* Within the `body`, add a header tag (can say anything, but if you're feeling uninspired, you can always go for the quintessential "Hello World")

Now, add a CSS file to the project, and call it something like `style.css`
* Add a style to turn the background color of the page to `#f1f1f1`

And then ensure that the CSS file is loaded within your HTML. You can preview what your webpage looks like by simply opening the local HTML file within your web browser.

### 4. Create a commit for your changes locally within Git
If your changes look good once you've previewed them, then it's time to create a local commit -- think of it as similar to a snapshot of a key moment in time for development.

First, check what the state of the repository is:
```
git status
```

This should tell you that you have two new "untracked" files. You need to *add* these such that Git knows they're a meaningful part of the repository, and are worth including in the version history. To do this, you can add each file individually:

```
git add index.html
git add style.css
```

Or, if all of the untracked files should be tracked, you can add all of them with this command:
```
git add *
```

At this point, issue the command
```
git status
```
once again. You should now see that the new files are "changes to be committed."

Now, time to actually commit your changes! Issue the following command to commit:
```
git commit -m "Added initial HTML and CSS files with basic page structure"
```

(You can change whatever is in between the quotes, since that's the *message* that will describe the commit. These should be as concrete as possible, while still being fairly succinct.)

Tada! You now have a commit that you've created locally. If you type `git log`, you'll see it (and the commit message) along with other prior commits.

### 5. Push your local changes to GitHub
You've made local changes, including creating the HTML and CSS files and adding content to them, but those changes aren't automatically propagated to GitHub. To get them into The Cloud™ that is GitHub, you'll need to *push* your local changes to the remote repository (what we set up in step 1).

Because you *cloned* your own freshly created repository, Git/GitHub should already "know" the appropriate link between your local Git repository to the remote GitHub repository. In other words, it'll "know" to update the code in your GitHub repository because that's where the folder initially came from. To check that this is the case, issue the following command in your local terminal:

```
git remote -v
```

This should return something like
```
origin  https://github.com/jcambre/hello-git-exercise.git (fetch)
origin  https://github.com/jcambre/hello-git-exercise.git (push)
```

Note that "origin" is just the default identifier for the remote repository.

At this point, try to actually push your changes to your remote repository with the following command:

```
git push origin git-practice
```

Those last two parameters (`origin`, and `git-practice`) correspond to the remote repository identifier, and to the branch name. The command will effectively create a new branch that copies the existing content that you have in your current local branch (`git-practice`) into a branch on the GitHub repository with that same name `git-practice`.

If you didn't already sign in using HTTPS when cloning the repository, follow the steps mentioned above for using a [personal access token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token).

At this point, if you were able to push successfully, you should now see your changes reflected on GitHub! There should be a banner if you look at the GitHub repository quickly enough, but if not, the branch will live at something like https://github.com/jcambre/PUI2020/tree/hello-git-exercise/basic-content

### 6. Merge your branch's changes into the main branch
If you're satisfied with the changes that you've made within the new branch, you can turn it into a *pull request*, which is a sort of candidate set of code to be merged into the main / master branch. With your homework assignments (because they are individual projects and not collaborative), this isn't entirely representative of the "real-world" coding experience where someone else might review and merge your code. That said, it's still helpful to get practice using branches, creating pull requests and keeping your primary branch well-maintained.

Once you create and merge a pull request through the GitHub interface, the code from that branch will be incorporated into the default branch. Remember that at that point, you'll still need to `pull` locally so the updates on GitHub are reflected within your local default branch. Specifically you would do something like:

```
git checkout master
```
(or `git checkout main` once the naming changes have gone into effect)

Then, to update your local version of your primary branch with the newly incorporated pull request on GitHub:

```
git pull origin master
```
(or `git pull origin main` once the naming changes have gone into effect)

Hooray! You've now done a full cycle of creating and updating local / remote commits.

## For even more practice...
When you track code like HTML and CSS files within GitHub, it isn't automatically rendered as a website. You're really just uploading the raw contents of those files for tracking differences between versions. That said, GitHub *does* offer a true [hosting option to turn a repository into a live website](https://pages.github.com/).

If you want to experiment a bit and get a head start (given that this will very likely be a part of future assignments and handy to do for personal portfolios or other experiments), try to figure out how to turn your repository into a live site, keeping in mind that it will be public :)