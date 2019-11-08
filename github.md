# GitHub

GitHub is open source tool for version control and source code management.
It provides access control and several collaboration tools such as bug tracking and task management.

# Git installation and usage steps

1.Install GitHub on linux(sudo apt-get install git).

2.Configure GitHub(git config --global user.name "user_name", git config --global user.email "email_id").

3.Creating local repository(git init Mytest, Initialized empty Git repository in /home/akshay/Mytest/.git/, cd Mytest).

4.Creating README file to describe the repository(gedit README, gedit README).

5.Adding repository files to an index(git add README).

6.Committing changes made to index(git commit -m "some_message").

7.Creating repository in GitHub, Go to github.com and press "+" to create new repository the name should be as the one created in local repository(git remote add origin https://github.com/user_name/Mytest.git).

8.Pushing the files in local repository to GitHub repository(git push origin master).

# If u want change the existing repository

- git remote set-url origin REPOSITORYURL.git





