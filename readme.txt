Git is a version control system.
Git is free.
# Install Git.
sudo apt install Git
# Configure Git.
git config --global user.name "cmy"
git config --global user.email "chenmingyi@nibs.ac.cn"
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