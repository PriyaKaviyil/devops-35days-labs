Day 6 Notes



\#adding a file

git add package.json

\#commiting a file

git commit -m "chore: add package.json"

\#getting log

git log --oneline

\#pushing to remote repo

git push -u origin main

\#stash

echo "incomplete feature" > feature.txt

git status             # See untracked file

git stash push -m "WIP: incomplete feature"

git status             # Working dir is clean

git stash list         # See the stash

git stash pop





\# === 8. Explore log ===

git log --oneline — compact one-line per commit

git log --oneline --graph --all — ASCII branch graph

git log --author="name" — commits by person

git log --since="2 days ago" — recent commits

git show a1b2c3d — see what a commit changed

git diff HEAD\~1 HEAD — diff last two commits



HEAD — current commit

HEAD\~1 — one commit back

HEAD\~3 — three commits back

HEAD^ — same as HEAD\~1



\# === Setup (do once per machine) ===

git config --global user.name  "Your Name"

git config --global user.email "you@example.com"

git config --global core.editor "code --wait"

git config --global init.defaultBranch main

git config --list              # Verify config



\# === Start a project ===

git init                       # New repo in current dir

git clone https://github.com/user/repo.git

git clone repo.git my-dir      # Clone into custom dir



\# === See what's happening ===

git status                     # Untracked / modified / staged

git diff                       # Unstaged changes (vs last commit)

git diff --staged              # Staged changes (what will be committed)

git diff HEAD\~1                # Changes since last commit



\# === Stage + commit ===

git add file.txt               # Stage specific file

git add .                      # Stage ALL changes (use carefully)

git add -p                     # Interactive: choose hunks to stage

git commit -m "feat: add login"

git commit --amend             # Fix last commit message (before push)



\# === Undo ===

git restore file.txt           # Discard working dir changes

git restore --staged file.txt  # Unstage (keep changes in working dir)

git reset HEAD\~1               # Undo last commit (keep changes staged)

git revert abc123              # Safe undo — creates a new "undo commit"



**# === Remote management ===**

git remote -v                  # List remotes

git remote add origin URL      # Add GitHub remote

git remote set-url origin URL  # Change remote URL



\# === Sync with remote ===

git fetch origin               # Download (don't merge)

git pull                       # fetch + merge

git pull --rebase              # fetch + rebase (cleaner history)

git push origin main           # Push to remote

git push -u origin main        # Push + set upstream tracking

git push --force-with-lease    # Safe force push (after rebase)



\# === Stash (temporarily shelve work) ===

git stash                      # Save dirty state, clean WD

git stash push -m "WIP: login" # Named stash

git stash list                 # Show all stashes

git stash pop                  # Apply last stash + drop it

git stash apply stash@{1}      # Apply specific stash (keep it)

git stash drop stash@{0}       # Delete a stash



**git add -p (patch mode)** lets you choose exactly which lines to stage within a file. Edited 3 unrelated things in one file? Stage them as 3 separate logical commits. Reviewers love this.



\# === diff ===

git diff                    # Working dir vs last commit

git diff --staged           # Staged vs last commit

git diff main feature-x     # Between two branches

git diff HEAD\~3 HEAD -- app.js  # One file, 3 commits back



\# === stash — save incomplete work ===

\# Scenario: mid-feature, urgent hotfix needed

git stash push -m "WIP: user dashboard"

git checkout main           # Switch to main for hotfix

\# ... fix the bug, commit, push ...

git checkout feature/dashboard

git stash pop               # Restore your work



\# === Useful aliases — add to \~/.gitconfig ===

git config --global alias.st  "status -sb"

git config --global alias.lg  "log --oneline --graph --all --decorate"

git config --global alias.cm  "commit -m"

git config --global alias.aa  "add -A"

git config --global alias.undo "reset HEAD\~1"



\# Now you can use:

git st        # Short status

git lg        # Pretty graph log

git undo      # Undo last commit



\# === Show file history ===

git log --follow -p src/auth.js  # All commits that touched this file

git blame src/auth.js            # Who wrote each line

git log --all --full-history -- "\*.secret"  # Find deleted file history

