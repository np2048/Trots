
# Python path and directories tips

## Imports

    import os
    import sys

## Get directory of the current script

    path = os.path.dirname( os.path.abspath( sys.argv[0] ))

## Change working directory

    os.chdir(path)