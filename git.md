# init & basic
git init

git config --global user.name "Your Name Comes Here"
git config --global user.email you@yourdomain.example.com
git config [init.defaultBranch]
git config --global alias.<name> "str"
git config --global credential.helper cache # save the login cache

git config --list --show-origin
git config <key>

git <verb> -h
git <verb> --help
git help <verb>
man git-<verb>

# file operation
git add . / git add xxx

git rm xx # unchanged; index&file or index(when file is deleted); xx can be file or directory
git add xx # update index; rm files from index when they're deleted
git rm -f xx # can be changed; index & file
git rm --cached xx # index only; can be changed
rm xx # remove file only, not index

git mv <from> <to>
#	git automatically detect file rename after git add & git rm

# commits
git commit -m "msg"
git commit -a # add modified file & commit
git commit -v
git commit --amend
#	sha-1


# log
git diff # index & current
git diff --cached # commit & index
git difftool

git status
git status -s # short format

git ls-files
#	count lines: git ls-files | xargs wc -l

git log # commit author date info v
#	styles
git log -p # complete diff v
git log --stat # diffstat
git log --summary # output creations, renames, mode changes, ...
git log --stat --summary # v
git log --graph # v
git log --oneline # one line output & 7 digits of sha-1 v
git log --pretty=xx # default:medium; oneline,reference,short,medium,full,fuller,format:"xxx"

git log --pretty=format:"%C(yellow)%h %C(cyan)%>(12)%ad %Cgreen%<(7)%aN%Cred%d %Creset%s" # whole oneline format

#	filters
git log -2 # show recent 2
git log --since=<time> --until=<time> # relative or absolute
git log --author=<name> --committer=<name>
git log --grep=<pattern> --all-match # match log info
git log -- <dir/file name> # introduce chg to dir/file; always the last option
git log --no-merges # skip merge commits
git log --all # show commits from all branches
git log --reflog # lost commits included


# branch
git branch # list
git branch <name> # create
git branch -v # show last commits
git branch -a, --all # show local & remote
git branch --move <old> <new> # rename
git branch --vv # print sha1 & upstream
#	update the rename to remote
git push --set-upstream origin corrected-branch-name
git push origin --delete new

git switch <name>
git switch -c <name> # create & switch
#	old: git checkout [-b]

#	merge
git merge <name>
#		Fast-forward: merge ahead
#		conflicts:
git diff
git commit -a
git branch -d <name>
git branch -D <name> # delete without merging



# gitignore
glob syntax:
	* ** ! ?
	[abc] [a-z0-9]
	beginning/end /
in command: add '\' or '""'

https://github.com/github/gitignore
can be nested

# undo
git restore <file> # index -> worktree
git restore --staged <file>, -S <file> # commit -> index
git restore --source <tree> <file> , -s <tree> <file> # commit -> worktree, <tree> can be HEAD
git restore --source <tree> --staged --workflow <file> , -SW <file> # commit -> index & worktree
# --workflow is dangerous

git reset --hard <commit>

git reflog # show commits visited

# tags
git tag
git tag -l <str> , --list <str> # tag matching str
git ehow <version> # info

git tag -a <version> -m <str> [<commit>]
git tag <version> [<commit>]
git tag -d <version>
git push <remotename> <version>
git push <remotename> --tags # all li tag & anno tag
git push <remotename> --follow-tags # only anno tag
git push <remotename> --delete <version>

git checkout <version>
git branch <name> <version>
git switch -c <name> <version>

# remote
git clone <repository> [<dir>]
git clone <repo> -o <name> # remote name; default "origin"

#	fetch: get all data from server; only one connecting to the internet
git fetch <name>
git fetch --all # all remotes & branches

git push <remote> <branch> 
git push <remote> <localbranch>:<remotebranch>

git pull # fetch & merge; one branch

#	track: git pull
git branch <branch> [--track] <remote>/<branch> # only one; git switch has 3 shortcuts
git switch -c <branch> [--track] <remote>/<branch>
git switch --track <remote>/<branch>
git switch <remotebranch> # auto add the branch

git branch [<branch>] (set-upstream-to |set-upstream-to=|-u )<remotebranch> # set the branch to track a rmtbranch; <branch> default cur branch
#	@{upstream} | @{u}: refers to upstream branch

todo: all switch & branch

git remote
git remote -v # links
git remote add <name> <link>
git remote show <name>
git remote rename <old> <new>
git remote rm <name> , remove <name>

# stash
git stash [push]
git stash --keep-index 
git stash (--include-untracked | -u) # stash & del untracked files
git stash (--all | -a) # also ignored files
git stash list # accepts option same as git log
git stash apply [stash@{<number>}] # default: most recent; conflicts: use git add first
git stash apply --index 
git stash pop # apply&delete
git stash branch <name> # apply & start a new branch & drop

git clean # rm untracked files
	-f # force
	-d # subdir
	-x # ignored too
	-n | --dry-run # a dry run
	-i # interactive

# github

ssh-keygen -t rsa -C "youremail@example.com"

# problems
git merge 2 repos
`git merge master  --allow-unrelated-histories`
