---
vc-id: 0b19d19b-b025-443c-8d20-70057370a7d8
---
#GitHub 
#### On GitHub
Create a new empty repository. Thus, to avoid errors, do not initialize the new repository with README, license, or gitignore files. You can add these files after your project has been pushed to GitHub.
#### On your local machine
Install Git from e.g. [here](https://git-scm.com/install/windows) (not covered in this how-to). 

Open your OS command line interface (CLI), e.g. `Windows PowerShell` or `Windows Run`. Change the current working directory to your local project. In the following, `$` is assumed to be the prompt of your CLI. Then:

`$ git init -b local`  
Initializes the current local directory as a Git repository, branch `local`. 

Now, take care that at least a single file is available in your local directory. This is also a good moment for inserting a `.gitignore` file into your local directory. Find more information on `.gitignore` [here](https://git-scm.com/docs/gitignore).

`$ git add .`
Collects the files in the local directory and stages them for commit.  

`$ git commit -m "First commit"`  
Commits the tracked changes and prepares them to be pushed to a remote repository.  

#### On GitHub 
At the top of your repository's Quick Setup page, click to copy the remote repository URL. For example, the  `kochbuch` repo of user `nluttenberger` has the URL https://github.com/nluttenberger/kochbuch.git

#### On your local machine  
Add the URL for the remote repository where your local repository will be pushed.

`$ git remote add origin <remote repository URL>`  
Sets the new remote repository

`$ git remote –v`  
Verifies the remote URL

`$ git push –u origin local`  
Pushes the changes in your `local` repository up to the remote repository you specified as  `origin`.

Setup completed! 

For daily working with your repos, consider installing an app like [GitHub Desktop](https://desktop.github.com/download/).