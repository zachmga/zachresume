# About Git Submodules

Git submodules allow us to keep a Git repository as a subdirectory of another Git repository. This lets us clone another repository into our project and keep commits separate. 

Often a code repository will depend on external code. This external code can be incorporated in a few different ways- it can be copied and pasted directly into the main repository, and through a language package management tool like Ruby Gems or NPM. However, neither of these approaches allow you to track edits and changes to the external repository. These approaches have their drawbacks, specifically losing any upstream chagnes to the external repository (when copying/pasting) and requiring installation and version maangement at all places the origin code is deployed. 

If you need to maintain strict version management over your external dependencies, it can make sense to use a Git submodule. Here are some good use cases:

- When an external compoent or subproject is changing quickly or upcoming hcanges will break the API, you can lock the code to a specific commit for safety
- You have a component that isn’t updated very often and you want to track it as a vendor dependency
- When you are delegating a piece of the project to a third party and you want to integrate their work at a specific time or release.

A Git submodule points to a specific commit in another external repository. Submodules are static and only track specific commits, they do not track Git refs or branches and are not automatically updated when the host repository is updated. 

If we want to add an existing Git repository as a submodule of the repository that we’re working on, we’ll use the `git submodule add` command, with the absolute or relative URL of the project you would like to start tracking. 

By default, submodules will add the subproject into a directory named the same as the repository. You can add a different path at the end of the command if you want it to go elsewhere:

```
git submodule add <remote URL> <directory where we want to clone the remote>
```

If you run `git status` after adding a submodule, you’ll notice a few things:

First, there’s a new `.gitmodules` file. This is a configuration file that stores the mapping between the project’s URL and the local subdirectory that you’ve pulled it into. 

```
[submodule <name of submodule>]
	path = Submodule
	url = remote_url
```

If you have multiple submodules, you’ll have multiple entries in this file. The file itself is version controlled with your other files, just like your `.gitignore` file. It’s pushed and pulled with the rest of your project. 

If you are cloning a project that has submodules, you’ll need to initialize those submodules:

```
git clone /url/to/repo/with/submodules
git submodule init
git submodule update
```

`git submodule init` copies the mapping from the .gitmodules file into the local `./.git/config` file. `git submodule init` accepts a list of submodules as well, so you don’t have to add every submodule in a project if you don’t need it.