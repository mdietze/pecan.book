GIT Overview
============

Git is a free & open source, distributed version control system designed
to handle everything from small to very large projects with speed and
efficiency. Every Git clone is a full-fledged repository with complete
history and full revision tracking capabilities, not dependent on
network access or a central server. Branching and merging are fast and
easy to do.

In the rest of the document I will talk about URL’s to clone the code.
There a few URL’s you can use to clone a project, using https, ssh and
git. You can use either https or git to clone a repository and write to
it. The git protocol is read-only.

#### PEcAnProject GitHub location: https://github.com/organizations/PecanProject
* PEcAn source code: 
 * https://github.com/PecanProject/pecan.git
 * git@github.com:PecanProject/pecan.git
* BETYdb source code:
 * https://github.com/PecanProject/bety.git
 * git@github.com:PecanProject/bety.git

Useful References
-----------------

* [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html) by
Scott Chacon (Git evangelist and Ruby developer working on GitHub.com)
* [Stackoverflow highest voted questions tagged "git"](http://stackoverflow.com/questions/tagged/git?sort=votes&pagesize=50)
* [Visual Git Tutorial](http://pcottle.github.com/learnGitBranching/)

Quick Start:
------------

Introduce yourself to GIT

    git config --global user.name "FULLNAME"
    git config --global user.email you@yourdomain.example.com

Get the remote repository locally:

    git clone URL

To update local repository to latest:

    git pull

To add new files to to local repository:

    git add <file>

To commit changes

    git commit <file|folder>

To update remote repository:

    git push

Show graph of commits:

    git log --graph --oneline --all

GitHub and fork
---------------

You can fork a project on github. This allows you to create your own
copy of the code. When you do the fork a copy of the code is created and
placed in your personal space. This is your personal copy, you can
clone, branch and push things back here. If you have a branch or some
code you want to merge back in the main branch you do a pull request.
This is the way for external people to commit code back to PEcAn and
BETY. The pull request will start a review process that will eventually
result in the code being merged into the main copy of the codebase.

See https://help.github.com/articles/fork-a-repo for more information, 
especially on how to keep your fork up to date with respect to the original.

GIT Workflow
------------

* GIT encourages to branch "early and often"
 * Branch before working on feature
 * One branch per feature
 * You can switch easy between branches
 * Merge feature into main line when branch done

        git branch <name of branch>
        git checkout <name of branch>
        repeat 
          write some code
          commit
        until done

        git checkout master
        git merge <name of brach>
        git push

If during above process you want to work on something else, commit all
your code, create a new branch, and work on new branch. As said before,
each feature should be in it’s own branch (for example each redmine
issue is a branch, names of branches are often the issue in a bug
tracking system).

Once you are all done with a branch you can delete it using `git branch
-d <name of branch>`

GitHub notes:
-------------

Easiest way to get working with GitHub is by installing the GitHub
client. More instructions for your specific OS and download of the
GitHub client, see https://help.github.com/articles/set-up-git.
This will help you setup an SSH key to push code back to GitHub. To
checkout a project you do not need to have an ssh key and you can use
the https or git url to check out the code.

Working with Rstudio
--------------------

Rstudio is nicely integrated with many development tools, including git and GitHub. 
It is quite easy to checkout source code from within the Rstudio program or browser.
The Rstudio documentation includes useful overviews of [version control](http://www.rstudio.com/ide/docs/version_control/overview) and [R package development](http://www.rstudio.com/ide/docs/packages/overview). 

Once you have git installed on your computer (see the [Rstudio version control](http://www.rstudio.com/ide/docs/version_control/overview) documentation for instructions), you can use the following steps to install the PEcAn source code in Rstudio.

### For "read-only" version:

1.  install Rstudio (www.rstudio.com)
2.  click (upper right) project
 *   create project
 *   version control
 *   Git - clone a project from a Git Repository
 *   paste https://www.github.com/PecanProject/pecan
 *   choose working dir. for repo

### For development:

1.  create account on github
2.  create a fork of the PEcAn repository to your own account https://www.github.com/pecanproject/pecan
3.  install Rstudio (www.rstudio.com)
4. generate an ssh key 
 * in Rstudio: 
  * `Tools -> Options -> Git/SVN -> "create RSA key"`
  * `View public key -> ctrl+C to copy`
 * in GitHub
  * go to [ssh settings](https://github.com/settings/ssh)
  * `-> 'add ssh key' -> ctrl+V to paste -> 'add key'` 
2. Create project in Rstudio
 *  `project (upper right) -> create project -> version control -> Git - clone a project from a Git Repository`
 * paste repository url `git@github.com:<username>/pecan.git>`
 * choose working dir. for repository

References:
-----------

* Scott Chacon, ‘Pro Git book’,
[http://git-scm.com/book](http://git-scm.com/book)
* GitHub help pages,
[https://help.github.com](https://help.github.com)/
* Main GIT page,
[http://git-scm.com/documentation](http://git-scm.com/documentation)
* Information about branches,
[http://nvie.com/posts/a-successful-git-branching-model](http://nvie.com/posts/a-successful-git-branching-model)/
* Another set of pages about branching,
[http://sandofsky.com/blog/git-workflow.html](http://sandofsky.com/blog/git-workflow.html)