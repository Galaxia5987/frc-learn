# Pull Requests

Pull Requests(Also abbreviated as "PR") are to propose and collaborate on changes to a repository. These changes are proposed in a [branch](../git.md#branch), which ensures that the [`main`](../git.md#the-main-branch) branch only contains finished and approved work.

!!! tip
    "Pull Request" is a rather confusing name. "Merge Request" describes better what it does. But Pull Request is the official name that we use.

## How Are We Doing This?

After finishing working on a branch, and wanting to merge it's changes to the `main` branch. After pushing our new changes(which can be made over a bunch of commits, it's a seperate branch and thus have a seperate history) to a branch, we can create a Pull Request.


## Creating a Pull Request

Creating a Pull Request is done on GitHub(on the web). When creating a Pull Request we need to specify the branch we want to merge into the `main` branch.

After creating a PR, we can see a discussion view, file changes, and commits.

The discussion view is for discussing the changes with mentors or other team members. Code Reviews will also be submitted and viewed in the discussion tab.

We can also see the option to request a code review from a mentor or team member. This is often required for merging, and you won't be able to merge without an approving code review from a member who has these privileges.

## Rules About Code Review

When receiving code review, we should follow these rules:

* **You can critic the review**: the reviewer isn't always right. These reviews are meant to get other people opinion on our code and discover bugs. If you think differently than what the reviewer proposes, say it!

* **Code style is important, but to a certain degree**: We don't need to argue on code style. Everyone has their idea of a perfect code. With that being said, code style should follow basic principles like [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself). Performance can be worse to a certain degree if it makes the code more readablereadible and easier to maintain.

* **Resolve conversations**: Conversations or suggestions that are done, solved or not, should be resolved. There is a a resolve button below every conversation. Click it only when the conversation is actually resovled.

* **Every proposal should have it's own commit**: When implementing a proposal, we should do it in one commit containing only the change proposed, without any unrelated things.

* **Changes made by a proposal should be mentioned**: When making a change based on a code review proposal, we should comment the commit hash(commit id, you can find it in commits view) it was made in.

## Merging

After getting an approved sign from a reviewer, you will be able to click the merge button and GitHub will merge your changes into the `main` branch!