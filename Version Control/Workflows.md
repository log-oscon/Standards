# Workflows

## Commit Messages
Please, apply these seven rules:

1. Separate subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain *what* and *why* vs *how*

Example:
```
Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here
```
(Reference: [Chris Beams - Git Commit](https://chris.beams.io/posts/git-commit/)
)


## Pull Requests
The only possible way to push code to Production is through a Pull Request.

There are certain conditions for the merge to happen:
* There must be at least two approvals
* If the code has a functional impact, that can be tested, there must be a third approve from a meber of the functional team


### Description
If you use JIRA or other issue tracker, put references to them in the body:

```
Resolves: #123
See also: #456, #789
```


## Branching from Source Branch
Sometimes you need to keep on working, but at the same time your next step requires code that is still under review. If you find yourself in this situation there is one thing you should never do: **convert your PR to a [WIP] and continue dumping code into it**.

Instead you should branch from the branch which has the changes you require to proceed (the source branch of the PR).


### Guidelines

There is one way to resolve this branching into a successful merge of all your changes, it is based on a simple principle: **You are in control of your PRs**.

* Create your PR with the branch you branched from as the destination. (PR Cascade)
* Keep track of relations between PRs and your branches (take a note in the PRs or on a personal medium).
* Never merge intermediate PR<sup>1</sup>
* Merge from top:
    * Never merge before all branches in a cascade are approved.
    * Start the merge from the PR for last branch you created
* Merge from bottom:
    * This merge solutions requires two steps and can be more confusing. Avoid it if you can, in favor of "Merge from top".
        1. Merge the PR from your first branch (usually this will be the one that points to `master`)
        2. Go into the next PR (i.e. the one from the branch that was created from the PR you just merged) and update the destination to `master` (or the branch that the PR you merged pointed to).
* All your merges must never change the diff of the PRs that still have not been approved.

**Note:** As stated above, you are in control and this is key. You are responsible for any code that may have not actually made it to the final destination (mainly `master`). Furthermore, if a mistake is made you must restore the PRs for approval with as little code as possible in each and **never** a One Time Urgent Mega Hyper Monstrous PR On Steroids!

**1** Imagine a cascade with 4 PRs, this means that you created a PR for each of the following branches: branch-1 (PR#1), branch-2 (PR#2), branch-3 (PR#3) and branch-4(PR#4). Additionally, each branch was created from the previous.

```
master
    |
    branch-1 (PR#1)
        |
        branch-2 (PR#2)
            |
            branch-3 (PR#3)
                |
                branch-4 (PR#4)
```
In this case we have two intermediate PRs: PR#2 and PR#3.

