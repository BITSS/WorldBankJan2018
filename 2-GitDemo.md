---
title : Introduction to git using GitHub Desktop
part of : BITSS World Bank Feb 2017 Workshop
time : 3 hours
author: Garret Christensen
affiliation: UC Berkeley
---


Git & GitHub Desktop Workshop
==============================
BITSS World Bank, February 2017
------------------------------
by Garret Christensen

Thanks to [Dillon Niederhut](https://github.com/deniederhut/BITSS2016) for some original materials.

Essentially, we are trying to avoid a situation like this one :

![http://www.phdcomics.com/comics/archive/phd101212s.gif](http://www.phdcomics.com/comics/archive/phd101212s.gif)

And move to a situation more like this one:

![Git xkcd comic](https://imgs.xkcd.com/comics/git.png)


### Background:
At a fundamental level, the problem is that we do not create perfect products the first time around. We add to them, remove things from them, and revise them heavily. For word processing tasks, like the PhD Comics example, this is somewhat harmless, and really is only costing you time in finding the correct document, or some embarrassment if you send the wrong document to a colleague.

You may already be collecting, cleaning, reshaping, and analyzing your data in a way that is self documenting. That is to say, you are writing it in code, and are not modifying pieces of it by hand or in a GUI. The upside to this is reproducibility. The downside is that if any of your code is the wrong version, your whole pipeline gets bunked.

A fairly common workflow setup can be seen [here](https://bids.github.io/2017-01-12-ucb/lessons/R/reproducible_workflow.html). If you teach undergrads, check out [Project TIER](http://www.projecttier.org/)'s protocol.  

The aspirational goal is that I should be able to sneak into your lab late at night, delete everything except for your raw data and your code, and you should be able to run a single command to regenerate EVERYTHING, including all of your results, tables, and figures in their final, polished form. Think of this as the “push button” or "one click" workflow.

Unlike the situation above, when you can't find the right version of your processing pipeline, analytical workflow, or data, you also lose the ability to recreate any results that you've generated. If your results are not reproducible, then they are also :

1. Not verifiable
2. Not explainable
3. not extendable

So, we need a way to know which version of our pipeline we are using and what has changed since the last version. There are many potential solutions in this space. Some people organize their revisions by hand into series of separate folders. Others use software that logs every action they take (SPSS or STATA output logs). Yet others prefer some kind of track-changes function in their GUI.

These solutions all suffer the same problem in that they force you, the user, to think about what a version is and how you are managing changes between versions. For example, if you are documenting your workflow with SPSS logs, if you want to know how you got that result you found one time last week, you have to manually search through the output from that entire day to find the code you ran but also all of the code that you ran to may or may not have led up to that result.

Git, or `git`, is software that abstracts away those details. is a version control program that helps you very accurately keep track of changes to text files, with or without collaborators. Note that .txt, .do, .R, .md, and many other files are actually text files. Others like .doc, .docx, .xls, .xlsx, .pdf, .dta, are not text files. So there's huge value in using Git and Github for your Stata script (.do) files, but there's little value in using it with your data (.dta) files. However, `git` is not particularly intuitive or user friendly. In fact, the author of `git` likes to joke that its name is a reference to how obstinate and curmudgeonly it is. The downsides here are:

1. Hard to understand
2. Hard to use correctly

However, the upsides are:

1. Never ever accidentally deleting or otherwise losing a file
2. Always being able to revert to your last working pipeline
3. Easy to discover what has changed (i.e. gone wrong), and when

Luckily for us, GitHub has built a GUI that makes working with `git` easier, although at some power cost. Many experienced users use the command line (Terminal on a Mac, Git Shell or Git Bash on Windows) to run Git, but GitHub Dekstop can do some of the simpler tasks, and that's what we'll use.

We'll likely have to use the command line to do something. If that's scary, help is [here](http://swcarpentry.github.io/shell-novice/02-filedir/), or don't be afraid to ask.

### To get started:

* Download and install a good text editor like [Atom](http://atom.io). (If you can. If you're using a computer with install limitations, just use the built-in editor.)

* Download and install the [GitHub Desktop app](http://desktop.github.com).

* [Create](https://github.com/join?source=header-home) a Github.com account and username.

## Forking

We're going to use our new GitHub account to `fork`<sup>1</sup> a repository -- a repository for this workshop, as it just so happens!

* Navigate to [github.com/BITSS/WorldBankFeb2017](github.com/BITSS/WorldBankFeb2017)
* Look for a button that says "fork" in the upper right-hand corner
* Click it!

This repository will then be copied to your own account (*not* your computer), so that you can make changes to it if you like. Since the fork exists on GitHub's servers, any changes that you push to those servers means those changes are already backed up for you.

* To avoid confusion, change the name of the repository to something like `GitWorkshop` by clicking on settings. *By they way: what's a "repository"?*

### Cloning, Creating, and Changing:
The options in the Github app under the "+" button are to add, create, or clone a repository. *Adding* is finding and telling the app that a repository is already on your computer. *Creating* creates a new repository. *Cloning* is copying an existing repository from your GitHub account.

To clone a public repository that doesn't belong to you, click the download button that is just to the left of the "Download ZIP" button on the repository's GitHub.com page, or drag and drop the URL from your browser into the open GitHub Desktop app (oddly, there is no way to type the URL directly into the app.)  

* Clone your fork of the workshop repository. Navigate to it on your computer to verify that it's there.

* What files are in there? Do you see anything you don't understand? If not, try this: [[Mac](http://www.macworld.co.uk/how-to/mac-software/how-show-hidden-files-in-mac-os-x-finder-funter-macos-sierra-3520878/)][[Windows](https://support.microsoft.com/en-us/help/14201/windows-show-hidden-files)]
If you do see the hidden files, *never ever ever* mess with them.

Now that you've succsefully cloned a repository, we'll create our own.

* Create a new repository. Give it a name like `codepoetry_<yourfavoriteanimal>` *What files are in it?*
* Create a text file called `README.md` using your text editor. Give the file three lines of text:

>Turning and turning in the widening gyre

> The falcon cannot hear the falconer;

> Things fall apart; the centre cannot hold;

* Save the file in `codepoetry`

What's different about Github Desktop?

* Click on the `README.md` file in Github Desktop.

Git keeps files in three areas. The workspace, the staging area, and the repository.
![SWC Git areas](https://swcarpentry.github.io/git-novice/fig/git-staging-area.svg)

Github Desktop automatically adds any file you change to the staging area. That's what the checkmark next to the file name means.

* Uncheck and recheck `README.md`.

* Commit, or permanently store, `README.md` by giving a concise but helpful message like `add README` in the Summary area then clicking on `Commit to master`.

* Create a second file called `regressions.do` using the Stata do file editor. Give it the lines:

`clear all`

`set more off`

`sysuse auto`

`reg price mpg`

* Save the .do file.

* Add a fourth line of text to `README.md` and save it.

> Mere anarchy is loosed upon the world,

* Uncheck `regressions.do` and commit *only* `README.md` with a message like `add line on anarchy`.

* Recheck `regressions.do` and commit it with a message like `add regressions.do`.

(We're using `add` to mean more than one thing here. Sorry.)

* Add a fifth line to `README.md`:
>The blood-dimmed tide is loosed, and everywhere

* Commit the change.
* Add a sixth line to `README.md`:
>The ceremony of innocence is drowned;

* Commit the change.


#### Undoing
There are several ways to undo things with git, not all of which are possible with Github Desktop. The GH methods are to:
1. Right click on the file on the file and Discard changes. *What areas is this dealing with? Note this is like `git reset filename` on the command line.*

2. Click on a change in the History section, and click on Revert.

3. Click on the settings gear and click Undo latest commit.

Yes, you can undo an undo. Just make sure when you are undoing changes that you are looking in your text editor at the most up to date version (close the file and reopen it.)

But what if you'd like to undo *all* the changes back to a certain point? [This is not possible in Github Desktop.](http://stackoverflow.com/questions/34790794/going-back-to-a-previous-commit-in-github-desktop) For that you have to use the command line.

* Revert the commit that added the fifth line to `README.md`.

* Revert the revert so you have the full six lines of `README.md` again.

We'll try one quick command in the command line. (See the SWC lesson [here](https://swcarpentry.github.io/git-novice/05-history/).)

* Open Git Shell (Windows) or Terminal (Mac).
* Navigate (using `cd`) to inside the folder that is the repository.
* Enter `git status` to make sure you're in your repository.
* Enter `git log` to see the record of your changes.
* Enter `git checkout <hash> <filename.txt>` where `<hash>` is the unique letter and number string refering to the place you want to jump back to and filename is the specific file.
* Verify that the file has changed back to the point you want.
* To get the latest version back, type `git checkout HEAD <filename.txt>` or `git checkout master` which will send you to the tip of the `master` branch. (I know, we haven't talked about branches yet! So let's do that now.)

Atlassian has a great [explanation](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting) of the differences between revert, reset, and checkout.  

### Branching:
Git uses branches to let you experiment on new ideas or bug fixes.

* Create, name, and sync a new `experimental` branch with the 'create new branch' button.
* Make changes to `regressions.do` making the regressions robust to heteroskedasticity, save, and commit them to `experimental`.
* Oh wait, no. Emergency, you have to go back to the main (master) branch.
* Change a different part of `regressions.do`. Add a line at the end:
`summ length`

* Merge the experimental branch into the master branch. In Github Desktop this is done by clicking on Update from. Make sure you're *in* Master and Update from experimental.

#### Conflicts
Between the experimental branch and the main branch, make and commit some conflicting changes (that is, changes to the same lines of the same file). Then try and merge. *What happens?*
* Change the regression line to read `reg price mpg weight` in master. Save and commit to master.
* Change the regression line to read `reg price mpg length, robust` in experimental. Save and commit to experimental.
* Try and merge.
* View the conflict (`<<<<<<<` `=======` and `>>>>>>>`), resolve the conflict by editing the weird part out of the file yourself, saving, and committing.

There's a conflict tutorial [here](https://bids.github.io/2017-01-12-ucb/lessons/git/).

### Publishing (pushing and pulling):

You can store stuff online at GitHub.com (or any server with Git installed), which will enable you to work on multiple computers.

Git frequently refers to `push`ing (sending) and `pull`ing (retreiving). Github Desktop simplifies this and just calls it "Sync".

To publish your repository on the web.
* Just click the Publish button.

Now we want to make sure that we can make changes online via GitHub.com, and then sync them to your computer (pulling).

* Go back and forth between making a local change, committing, and pushing it to the web, and making remote (online) changes (click the pencil button to edit, then commit at the bottom of the screen), being sure to sync between each commit. Eventually you'll screw up and not sync enough. (That is, change a file online and commit it. Don't sync. Make a contradictory change locally and commit it. Try and sync. *What happens?*)

<!--Aside: This tutorial is written in Markdown. If you want something *not* to render markdown, comment it out like this. Same as HTML.-->


### Collaborating:
Thus far we've been working solo. Now we'll collaborate. GitHub is built for this. Thousands of people contribute code to large open source coding projects without ever meeting in person. It's also great for just a few people to collaborate on simpler coding projects.

There are two ways to collaborate:

1. Make everyone you trust a collaborator. For small projects with trusted collaborators only.
2. Pull requests. For big projects--let anyone make suggestions (called pull requests) and the owner gets to choose whether to accept.

We'll probably only have time for #1.

1. Pair up with a neighbor. One of you be A and one be B for this exercise.
2. In the settings tab for A's repository on Github.com (that A published above), add B as a collaborator.
3. B accept the invitation, and clone A's repository so you have it on your own computer.
4. B make a change, commit, and sync (push) the change.
5. A sync (pull) B's changes, make your own changes, commit, and push.
6. After handing off back and forth successfully, make simultaneous conflicting changes. *How do you resolve the conflicts?*
7. Switch roles between A & B and repeat.

If we have time for Pull Request collaboration, or you have questions, we will follow Github's [guide](https://help.github.com/desktop/guides/).

### Additional Git Topics:

#### Pull Requests:
This is how you suggest changes to repositories to which you aren't a full fledged collaborator. Try this with a partner if you have time. Clone a repo you don't own, make a change, submit a pull request, and ask the owner to merge the pull request. Switch roles.

#### Command Line:
Many, if not most, experienced users will use Git via the command line. (Terminal on a Mac, the Git Shell that came with the Desktop app, Windows PowerShell, there are a lot of options. They're all where you type commands for your computer to execute.) You can read why [here](http://programmers.stackexchange.com/questions/173297/why-learn-git-when-there-are-gui-apps-for-github). Basically, it's more powerful.

There are a million and one online tutorials for Git in the command line. [Software Carpentry's](http://swcarpentry.github.io/git-novice/) is good, as is [Atlassian's](https://www.atlassian.com/git/tutorials/). The basic stuff is all nicely summarized [here](http://rogerdudler.github.io/git-guide/) in a single page.


**1.** For more on forking, see [https://help.github.com/articles/fork-a-repo/](https://help.github.com/articles/fork-a-repo/)
