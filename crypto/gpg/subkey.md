# GnuPG — Add a subkey

Subkeys are like the normal keys, except they're bound to a master key pair. Subkeys can be revoked independently of the master keys, and also stored separately from them. 

    $ gpg --list-keys
    $ gpg --edit-key USER_EMAIL
    gpg> addkey
    
    ...
    
    gpg> save
