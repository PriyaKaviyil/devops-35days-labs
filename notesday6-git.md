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

