# Git

Git is a Distributed Version Control System (VCS) created by Linus Torvalds, also known for creating and maintaining the Linux kernel! Version Control is a system for tracking changes of code for developers. The advantages of Git Version Control are:

* Separation of code features and environments into branches

* Ability to navigate to a particular version(commit) without removing history

* Ability to manage version(commit) in various ways, including combining them

## More Resources

Git actually has a **TON** of resources to learn from online, and this one is probably not the best one out there. It will be more tailored to knowing what **we** need rather than everything.

Having said that, Git, at a basic level, isn't that complicated at all. It's just a way to manage files and versions. But, if you feel you don't understand everything fully, you can try one of the following resources as well - they are great!

[Learn Git in Y minutes](https://learnxinyminutes.com/git/) (Actually a great website for learning programming in a brief, worth checking out regardless, in my opinion)

[Learn Git Branching Game](https://learngitbranching.js.org/) (A cute game for learning git interactively, I personally think it's a bit more complicated and text-heavy than it should, but super nice regardless)

[WPILib's Introduction to Git](https://docs.wpilib.org/en/stable/docs/software/basic-programming/git-getting-started.html) (All WPI docs are great, and so is this one)

## What We Will Not Learn

Git is traditionally supposed to be managed through the terminal(a place where we can execute system commands - the hacker thing you see in movies). This is can be a bit harder to learn, and for no reason! We have tools in our code editor(Intellij IDEA) that makes it easier to manage Git through a graphical user interface.

We will only learn the concepts behind git, and not how to do each thing in specific.

## Vocabulary

Before we jump into managing our files and versions using Git, we should all have a shared vocabulary of all of these Git terms:

* **Repository**: The directory containing all our code. This term is commonly abbreviated as "repo".

* **Commit**: A particular saved state(version) of the repository, which includes all files and additions.

* **Branch**: Grouping a set of commits. Each branch has a unique history, although branches can be created from other branches, then they will have a shared base history.

* **Push**: Update the remote repository(where we store our code, on Github) with your local changes.

* **Pull**: Update your local repository with the remote changes(that other members might have done).

* **Merge**: Combine various changes from different branches into a single history


## Repository

Our project consists of many files and folders. The root of the project, is called the repository. Everything inside the repository is tracked, versioned and can be commited(unless specified explicitly).

## Commit

This is a snapshot of the current project state. When you commit, you save a version of the project.

Commits are done in the commit side bar. We can specify the changes we want to commit(we can choose to only commit some of the changes), specify a commit message(what we changed or added), and click commit!

As easy as that, we just made our first commit.

## Branch

A branch is a divergence in the history of the project.
We can create a branch for a specific feature we want to add, while other team members continue to work on the project. When the new feature is ready, we can merge it into the main working branch.

### The `main` branch

Each git repository has the `main` branch. This is the default branch that represents the main working version of the project.

This branch is usually "protected", which means that we can't push to it directly. Instead, we must create a seperate branch for what we want to add, and when it's ready, merge it by a *Pull Request*(we will learn about pull requests later).

This is to ensure that multiple team memebers would be able to work on the code at the same time, and then merge everything together.

## Push

While Git is a program we run locally on our computer, in order to collaborate with other team members, we need a centralized place to save our project and versions to, so everyone can synchronize.

For that, we have a cloud based service called [GitHub](https://github.com). GitHub is just the place we store the code.

The action of sending our code to GitHub is called "Pushing". Push is a manual action we should do after every commit, commiting without pushing will result in the new commit not showing on GitHub.

We will talk more about GitHub and it's advanced features later.

## Pull

While pushing is the action of sending our code to GitHub, "Pulling" is the action of receiving code from GitHub.

Pulling is a manual action that we do when we want to synchronize our local version with the cloud saved version that another team member might have changed.

## Merge

When having multiple branches with diffrent histories, we might want to combine them into one.

Let's say we worked on a feature on the branch `new-feature`. While we worked on that, another team memeber worked on `another-feature`. What happens now? how do we combine them both into the `main` branch?

This is called merging. This is a magic operation that Git can do to combine diffrent histories into one branch.

As Git is not magic, we sometimes can have conflicts between histories(called "merge conflicts") that need to be resolved before merging.

Merging is commonly done via Pull Requests in Github.

