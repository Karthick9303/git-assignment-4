# Initialize the repository and create branches (if not done already)
git init
echo "Content of master.txt" > master.txt
git add master.txt
git commit -m "Add master.txt to master branch"

# Create branches
git branch public1
git branch public2
git branch private

# Add public1.txt to public1 branch
git checkout public1
echo "Content of public1.txt" > public1.txt
git add public1.txt
git commit -m "Add public1.txt to public1 branch"

# Merge public1 into master
git checkout master
git merge public1

# Add public2.txt to public2 branch and merge into master
git checkout public2
echo "Content of public2.txt" > public2.txt
git add public2.txt
git commit -m "Add public2.txt to public2 branch"
git checkout master
git merge public2

# Edit master.txt on private branch
git checkout private
echo "Updated content of master.txt on private branch" > master.txt
git add master.txt
git commit -m "Edit master.txt on private branch"

# Update public1 and public2 with private changes
git checkout public1
git merge private
git checkout public2
git merge private

# Update master with private changes
git checkout master
git merge private

# Update private with master changes
git checkout private
git merge master

# Add the remote repository
git remote add origin https://github.com/Karthick9303/git-assignment-4.git

# Push all branches to GitHub
git push -u origin --all
