
# Git create a repository from command line

## git clone

The easiest way to create a repository is to create it on GitHub and then clone it to a local directory:
    
    $ git clone https://github.com/USERNAME/REPOSITORY

If you already have some files in the directory of the repo then you can move them to a temporary dir, clone the repo, move the files back and commit:
    
    $ git add .
    $ git commit -m 'Start'
    $ git push

This is the most simple way.
