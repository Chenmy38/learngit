Git is a version control system.
Git is free.
# Install Git.
sudo apt install Git
# Configure Git.
git config --global user.name "cmy"
git config --global user.email "chenmy38@gmail.com"
git config user.email
git config user.name
# Create a repository.
mkdir mygit
cd mygit
pwd
git init
# Add files to the repository.
touch readme.txt
git add readme.txt
git commit -m "I wrote a readme file"  # Add a note after the -m parameter
# Check the status of files in the repository.
git status
# Read the changes.
git diff readme.txt
# Add the modified file to the repository.
git add readme.txt
git status
git commit -m "I modify the file to record the process of learning git."
# Check the status again.
git status
# Check the log of git commit.
git log
git log --pretty=oneline
# Reset git to a earlier version.
# The present version is marked as HEAD.
# The previous version is marked as HEAD^.
# The previous 100 version is marked as HEAD-100.
git reset --hard HEAD^
# To restore the newer version of git, you must get the id of the commit command. You can find it using the 'git reflog' command.
git reflog
git reset --hard 83e7
# Understanding the stage of git.
touch LICENSE
git status  # The LICENSE file is marked as Untracked files. It means we have not added this file to the git repository.
# Add the modified readme.txt and the LICENSE files to the stage.
git add LICENSE readme.txt
git status  # Now the LICENSE file is marked as a new file. It has been added to the stage.
git commit -m "understand how stage works"
# Manage changes. Remember git keep track on changes instead of files.
# Check differences between the readme.txt in the working directory and the readme.txt in the stage.
# Every time we make a change, we need to add it to the stage before we commit it, otherwise the change will not be tracked.
git diff HEAD -- readme.txt
git add readme.txt
git commit -m 'Git tracks changes instead of files'
# Suppose you make a mistake in the working directory and you have saved it. Now you want to discard all changes made in the working directory.
git restore readme.txt
# If you have staged the changes, you need to unstage the file first and then discard changes made in the working directory.
git add readme.txt
# To unstage a file:
git status
git restore --staged readme.txt
git restore readme.txt
# Delete a file.
touch readme.md
git add readme.md readme.txt
git commit -m 'Add a file and delete it.'
# Now remove the readme.md file
rm readme.md
git status
# To restore mistakenly deleted files:
git restore readme.md 
# To eliminate readme.md:
rm readme.md
git rm readme.md
git status
git commit -m 'Delete a file from the repository'
# Make a SSH key.
ssh-keygen -t rsa -C "chenmy38@gmail.com"
# Your private key is stored in the ~/.ssh/id_rsa.pub
# Link the local repository to github.
git remote add origin git@github.com:chenmy38/learngit.git
# Push local repository.
git push -u origin master
# Pull new changes to update local repository. When you have conflict with remote repository, you need to pull and fix the conflict before you push.
git pull origin master  # Essentially, this command tries to merge origin master with local master. 
git pull origin branch_name
# Delete a remote repository.
git remote -v
git remote rm origin
git push origin --delete dev
# Clone a remote repository. Note you can only see the master branch of remote repository.
git clone SSH_address/https_address
# To clone the other branch of remote repository:
git switch -c local_name origin/remote_name
# HEAD points to current branch, master.
# Fork a new branch called dev and move to the dev branch.
git switch -c dev  
# Check the current branch.
git branch
git add readme.txt
git commit -m 'Branch test'
# Switch back to the master branch.
git switch master
# All changes we made in the dev branch are lost.
# To merge the dev branch with current branch:
git merge dev
# After merging we can delete the dev branch.
git branch -d dev
# Fix conflict of merge
git switch -c feature1
# Creating a new branch is simple & fast.
git add readme.txt
git commit -m '& simple'
git switch master
# Creating a new branch is simple AND fast.
git add readme.txt
git commit -m 'AND simple'
# Creating a new branch is quick and simple.
git add readme.txt
git commit -m 'conflict fixed'
git log --graph --pretty=oneline --abbrev-commit
git branch -d feature1
# Manage branches.
git switch -c dev
git add readme.txt
git commit -m 'add merge'
git switch master
git merge --no-ff -m 'merge with no fast-forward'
git log --graph --pretty=oneline --abbrev-commit
# Remember you need to add and commit a change before switching to another branch. 
# Here is a problem. When you do not finish the work on the current and you have to switch to another branch, what should you do?
# You can save the work on the current branch temporarily and switch to another branch to complete urgent tasks. 
git stash
# After finishing urgent tasks, you then switch back to working branch, and invoke saved workspace.
git stash apply
# Or
git stash pop
# You can stash several times and invoke the specific stash.
git stash apply stash@{0}
git stash list
# To delete a unmerged branch:
git branch -D branch_name
# Add a tag
# Note tags are displayed together with commits.
git switch master
git tag v1.0
# Check all tags which are displayed temporally.
git tag 
# Add a tag to a specific commit.
git log --pretty=oneline --abbrev-commit
git tag v2.0 d386954
# Show details of a tag.
git show tag_name
git show v2.0
# Add a tag with more information.
git tag -a v3.0 -m 'More details about tags.' 95398d9
git show v3.0
# Delete a tag.
git tag -d v1.0
git push origin :refs/tags/v1.0  # Delete a remote tag.
# Push a tag.
git push origin v2.0
# Push all tags.
git push origin --tags
# To rename a file managed by git:
git mv old_file_name new_file_name



