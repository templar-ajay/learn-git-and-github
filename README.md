# use this repo  to learn and revise git commands 
=======
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

- tracked files *files present in previous commit*
- untracked files *files not present in previous commit*

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

*git by default doesn't track .md files*

**Global Ignore File**

- git config --global core.excludesfile [file]

**Clearing the Cache**

- git rm -r --cached . 

*rm tells to remove -r tells to remove recursively -used to delete multiple files*

**Deleting and Renaming Files**

git rm <file-name>
git mv <file-name> <new-file-name> // used to rename or movefiles

*for example to move index.html to docs/index.html -$ git mv index.hmtl docs/index.html*

git log --oneline  

*compact view of git logs*

**Differences**

- git diff
- git diff --color-words

*better alternative - Git Lens extension*

**Changing History**

- git commit --amend
- git commit --am "New Commit message"
- git commit --amend --no-edit

- git reset <sha1 of previous commit>

then stage the changes
and commit them

*example -$ git reset 782b1a4*

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

*shows the list of stashes*

- git stash apply 

*applies the changes of the stash and preserves the stash*

- git stash pop 

*applies the changes of the stash and deletes the stash from the stash list*

- git restore . 

*restores the code to original by removing stash changes*


**Git Clean**

- git clean
- git clean -n // dry run 
- git clean -d // directories
- git clean -f // force

for example to remove FAkeDocs/jj.txt
- git clean -fd 

*will remove FAkeDocs directory - can also try out "-i" with "-d"*

**GitHub**

-  Cloud Repository 
-  Collaborative Development
- Project Management
*create issues and assign them to developers*

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

