
# Create new Git repository from command line

## git clone

The easiest way to create a repository is to create it on GitHub (or other similar service) and then clone it into a local directory:
    
    $ git clone https://github.com/USERNAME/REPOSITORY

If you already have some files in the directory of the repo then you can move them to a temporary dir, clone the repo, move the files back and commit:
    
    $ git add .
    $ git commit -m 'Start'
    $ git push

This is the most simple way.

## GitHub command line tool

You can creat a repository on GitHub using official command line utility:
https://github.com/cli/cli

    $ gh repo create NAME --description "New repo"

Detailed manual available at the official documentation website:
https://cli.github.com/manual/
