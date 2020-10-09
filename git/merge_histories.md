
# fatal: refusing to merge unrelated histories

If you encounter this error when merging two branches try the following option:

    $ git merge master --allow-unrelated-histories

Replace **master** with your branch name which you want to merge with your current working branch.
