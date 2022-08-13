# Use this repo to learn and revise git commands

**Installing Git**

on linux
`sudo pacman -S git`

adding git-autocomplete.bash to profiles.bash for git to support auto completion in git 

1. copy the git-completion.bash file from github to local machine in `home` directory with this command - 
`curl https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash -o ~/.git-completion.bash`

2. find `.bash_profile` in home directory -
`cd`
`ls`
now check if there's a `.bash_profile` file , if yes then open it with code or nano in command line - 
to open in code run -

`code  .bash_profile`

then paste the following code at the end of the file -

````bash
if [ -f ~/.git-completion.bash ]; then
  . ~/.git-completion.bash 
fi
````


autocomplete suggestions are now enabled in git :wink:

**Git configure**

open command line and type - 

3 places to config git 
- --system configures the setting systemwide for all users
- --global configure the setting for the current user on his all repos
- --local configures the setting only on the current project

`git config --global user.name "*enter-your-github-username-here*>"`

`git config --global user.email "*enter your github email here*"`

`git config --global color.ui true` to use colors in git shell (improvse readablility)

`git config --global core.editor "code --wait"` sets up code as default text editor 

`git config --global credential.helper store` stores the PAT on the first time you enter it after running this command , and uses it to automatically authenitcate your command line with github so that you don't have to manually enter it every time you make a pull or push request

now for example lets clone a repo to our local machine from github

copy the github repo url and add ".git" at the end of it

now the url is https://www.github.com/example-user/example-project.git

copy this url to the clipboard .

on the command line navigate to the folder where you want to store the repos of github , for me it's the `~/repos` folder

`cd repos/`

then run 

`git clone *paste the url from clipboard here*`

example - `git clone https://github.com/templar-command0/learn-git-and-github.git`

this will clone the repo locally in a folder and name the folder with the project name 
in my case the folder path is `~/repos/learn-git-and-github`

then enter the project using 

`cd *project-name*`

example `cd learn-git-and-github`

then follow the below tutorial to generate your PAT to access github from command line.

**Accessing Github from Command Line using PAT**

- goto github.com 
- click on dropdown on topright of your screen on side of your profile pic -> select settings

- scroll to the bottom of the left panel and select `developer settings`

- then select personal accesss tokens
- and create a token with repo permission 
- i also give it delte repo permission
then copy the generated token to clipboard.

go back to the command line and make sure you are in your project folder , to check run 

`pwd`

it shows the path of the directory you are currently in 

then run 

`git push`

it will prompt you for the user name 
enter your username
don't enter your password
enter your PAT instead , paste it by ctrl+shift+v
and press enter

if it succeeds then run the git push command again and see that it doesn't ask for authentication again 

it it fails check the PAT you copied , if you lost it by accident 
follow the **Accessing Github from Command Line using PAT** again to generate a new PAT and enter it again it should work.



**Staging Files**

- git add --all
- git add -A
- git add .
  // the period is the shortcut in linux to access the current directory
  **Commit**
- git commit -m "first commit" // -m for specifyinga commit message

**Git environments**

- working
- staging
- commit

**Files States**

- tracked files _files present in previous commit_
- untracked files _files not present in previous commit_

**Tracked Files**

- Unmodified
- modified
- staged

**Viewing Satus**

- git status

**Restoring Files**

- git restore .
- git checkout .

**Why Ignore Files**

- Sensitive info // authentication tokens, api keys , passwords
- Personal Notes // to-do items
- System Files // mac uses a .DS_store file , vs code uses a .vscode file to save local preferences

**.gitignore**

.DS_Store
.vscode/
.authentication.js
node_modules
notes/
\*\*/\*todo.md //here backward slashes are used to tell eiditor to not treat asterisk specially

_git by default doesn't track .md files_

**Global Ignore File**

- git config --global core.excludesfile [file]

**Clearing the Cache**

- git rm -r --cached .

_rm tells to remove -r tells to remove recursively -used to delete multiple files_

**Deleting and Renaming Files**

git rm <file-name>
git mv <file-name> <new-file-name> // used to rename or movefiles

_for example to move index.html to docs/index.html -$ git mv index.hmtl docs/index.html_

git log --oneline

_compact view of git logs_

**Differences**

- git diff
- git diff --color-words

_better alternative - Git Lens extension_

**Changing History**

- git commit --amend
- git commit --am "New Commit message"
- git commit --amend --no-edit

- git reset <sha1 of previous commit>

then stage the changes
and commit them

_example -$ git reset 782b1a4_

**Rebasing**

- git rebase <branch>/<commit>
- git rebase --interactive <branch>/<commit>
- git rebase -i HEAD~//
- git rebase -i --root

**Branches**

- git branch

**copying a branch**

- git switch -c NAME //here -c copies the current branch to new branch with name = NAME
- git checkout -b NAME

**Switch Branch**

- git switch <branch-name>

**Merging**

- git merge <branch-name> //mergers the <branch-name> branch in current branch.

**Deleting a Branch**

- git branch --delete NAME
- git branch -d NAME
- git branch -D NAME

**Git Flow**

- Feature/Fix Branch
- Make Changes
- Merge to Master
- Delete old branch

**Stashing Code**

git stash

- git stash list

_shows the list of stashes_

- git stash apply

_applies the changes of the stash and preserves the stash_

- git stash pop

_applies the changes of the stash and deletes the stash from the stash list_

- git restore .

_restores the code to original by removing stash changes_

**Git Clean**

- git clean
- git clean -n // dry run
- git clean -d // directories
- git clean -f // force

for example to remove FAkeDocs/jj.txt

- git clean -fd

_will remove FAkeDocs directory - can also try out "-i" with "-d"_

**GitHub**

- Cloud Repository
- Collaborative Development
- Project Management
  _create issues and assign them to developers_

**working with github**

- set up remote
- Push
- Fetch / Pull

**Remotes**

- git remote add NAME url
- git remote remove NAME
- git rename OLDNAME NEWNAME
- git remote -v

**Git Push**

- git push REMOTE BRANCH
- git push --set-upstream-to origin main
- git push -u origin main // --set-upstream
- git push --all
- git branch --set-upstream-to <origin/remote-branch>

**Organizing Projects**

- Contributors
- Issues
- Labels
- Milestones
- Projects

**Syncing GitHub**

Clone - make a copy on the repository on our local machine

Fetch - downloads information from the remote

Pull - git pull

1. git clone "url + .git"
   ex- git clone https://github.com/templar-command0/multiple-products-page.git

2. git fetch
3. git branch // shows branches on local
4. git branch -a //shows all branches on local and remote
5. git pull
6. git branch --set-upstream-to=origin/main main
7. git pull


# Working with `.md` markdown files 

**Add Heading**
\# means <h1> heading
\#\# means <h2> heading which is smaller than h2
\#\#\#\#\#\# means <h6> heading which is the smallest 

examples of h1 heading 

# H1 heading 
## h2 heading 
### h3 heading 
#### h4 heading
###### h6 heading 

**images**

```text
![alternate text here](https://www.imageUrlHere.com)
```
if you don't use the ! sign at the start then it will show as a link with the alternate text as link name and image url as the href of the link

for example-

```
[this is my image link](https://avatars.githubusercontent.com/u/100400299?s=400&u=014eefa677c44994f49f819fd0d24a60b7f05943&v=4)
```
the above code will render like this - 
[this is my image link](https://avatars.githubusercontent.com/u/100400299?s=400&u=014eefa677c44994f49f819fd0d24a60b7f05943&v=4)

```
### [My Github Profile Link](https://github.com/templar-command0/)
```
this code will render this 
### [My Github Profile](https://github.com/templar-command0/)

**create ordered and unordered lists**
```
- Unordered list Item 
- Unordered list second item 
  - unordered sub list 
  - unordered sub list item 2

1. ordered list item1 
  1. ordered sub-list item 1
  2. orderd sub-list item 2 
```

below is the depiction of the above code

- Unordered list Item 
- Unordered list second item 
  - unordered sub list 
  - unordered sub list item 2

1. ordered list item1.
2. ordered list item2
  1. ordered sub-list item 1
  2. orderd sub-list item 2 

