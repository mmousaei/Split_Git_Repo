# Split_Git_Repo

Splitting a subfolder out into a new repository

You can turn a folder within a Git repository into a brand new repository.

If you create a new clone of the repository, you won't lose any of your Git history or changes when you split a folder into a separate repository.

## Open Terminal.

## Change the current working directory to the location where you want to create your new repository.

## Clone the repository that contains the subfolder.

    git clone https://github.com/USERNAME/REPOSITORY-NAME

## Change the current working directory to your cloned repository.

    cd REPOSITORY-NAME

## To filter out the subfolder from the rest of the files in the repository, run git filter-branch, supplying this information:

     FOLDER-NAME: The folder within your project that you'd like to create a separate repository from.
     

     BRANCH-NAME: The default branch for your current project, for example, master or gh-pages.
     

        git filter-branch --prune-empty --subdirectory-filter FOLDER-NAME  BRANCH-NAME 
        # Filter the specified branch in your directory and remove empty commits
        Rewrite 48dc599c80e20527ed902928085e7861e6b3cbe6 (89/89)
        Ref 'refs/heads/BRANCH-NAME' was rewritten

   The repository should now only contain the files that were in your subfolder.

## Create a new repository on GitHub.

## At the top of your new GitHub repository's Quick Setup page, click 

to copy the remote repository URL.

### Tip: For information on the difference between HTTPS and SSH URLs, see "Which remote URL should I use?"

## Check the existing remote name for your repository. For example, origin or upstream are two common choices.

```
git remote -v
origin  https://github.com/USERNAME/REPOSITORY-NAME.git (fetch)
origin  https://github.com/USERNAME/REPOSITORY-NAME.git (push)
```

## Set up a new remote URL for your new repository using the existing remote name and the remote repository URL you copied in step 7.

```
git remote set-url origin https://github.com/USERNAME/NEW-REPOSITORY-NAME.git
```

## Verify that the remote URL has changed with your new repository name.

```
git remote -v
```

## Verify new remote URL

```
origin  https://github.com/USERNAME/NEW-REPOSITORY-NAME.git (fetch)
origin  https://github.com/USERNAME/NEW-REPOSITORY-NAME.git (push)
```

## Push your changes to the new repository on GitHub.

```
git push -u origin BRANCH-NAME
```
