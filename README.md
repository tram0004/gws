gws
===

`gws` is a bash helper to manage workspaces composed of git repositories.

Functionalities
---------------

This script offers some functionalities, among which:

  * It uses a list of projects, named `.projects.gws`, containing many projects
    described by its name, its repository url, and optionaly an upstream url,
    like:

        work/theSoftware | git@github.com:You/theSoftware.git
        perso/gws        | git@github.com:You/gws.git         | git@github.com:StreakyCobra/gws.git

  * It can use an ignore list, named `.ignore.gws`, containing regular
    expressions which discard some specific projects, for instance to disable on
    your home computer the work-related projects.

  * It can clone non-existing repositories from the projects list (but not
    supress them in case of removal, you have to do it yourself for safety
    reason. Notice that there is the `check` functionnality to identify
    unlisted repositories).

        gws update

  * It can monitor all listed repositories in one command (uncommitted, untracked,
    branches not synced with origin, ...).

        gws status

    or simply

        gws

  * It can check the workspace for unlisted repositories (for example removed
    ones).

        gws check

Context
-------

If you are, like me, a Linux programmer/hacker/coder who use heavily git, you
certainly have a directory in your home folder named `dev`, `workspace`, `code`
or something else that contains all the projects you are working on. For
instance my currently is:

    dev
    ├── archlinux
    │   ├── aur
    │   └── habs
    ├── perso
    │   ├── gws
    │   ├── imaxplore
    │   └── teafree
    ├── config

where `aur`, `habs`, `gws`, `imaxplore`, `teafree`, `config` are git
repositories.

Since I use at least two different computers, one laptop and one at work, I like
to have the same folder structure on both. Of course remembering which project
was added recently and in which folder is tedious.

So I started to thing about using git submodules to register all projects on
which I am working and syncing them with git between the two computers. But
clearly git submodules are not usable because they are working on specific
commit and are not following branches.

No worry. The problem is pretty trivial, so I decided to start write a little
bash script that read a simple list of repositories, and clone them if they
don't exist. And then, commit by commit, the script as grown to finally become
a helper to sync, monitor and check workspaces.

I thought it can be useful to other people, so I made a little cleanup, write
a small documentation, and there it is. I hope you will enjoy it!
