1. Configure GitHub & push a change

a. Git init -> initiate a repository
b. git config --global init.defaultBranch main or
c. Git branch -m -> Give branch a name
d. Git add . ->Add all files in the folder
e. Git commit -> Commit changes to the repository (and comment)
f. git remote add origin https://github.com/dietrichDB/lab_demunt_thursday.git -> Add your remote repository
g. Git push -> Push the changes
h. git push --set-upstream origin master (first time only)
e. Verify online at your repository files have been added.

2. Download something from git

After adding the remote repo, you can just do "git pull" to retrieve.

git init (to make the folder a git repo)

and after that

git pull https://github.com/dietrichDB/lab_demunt_thursday.git master

to pull its contents


If you want to store credentials for your Github account, use a credential helper option:
https://www.geeksforgeeks.org/git/how-to-save-username-and-password-in-git/

Never save them unencrypted to disk;-)

*** Authenticate fix with git ***

manager-core (Windows and macOS) / osxkeychain (macOS) / libsecret (Linux)

These helpers store credentials securely in the OS-specific credential storage.

For Windows

git config --global credential.helper manager-core

For macOS:
git config --global credential.helper osxkeychain

For Linux:
git config --global credential.helper libsecret

Add your credential data to the config:

git config --global user.name “DietrichDB”

git config --global user.email “dietrich@defaultroute.be”

git config --global credential.helper cache
