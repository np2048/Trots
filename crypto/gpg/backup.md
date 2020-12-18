
# How to backup and restore gpg keys

You can create a backup just by copying the whole *~/.gnupg* directory. But this is not safe and it is not a recommend way to backup the keys as it may lead to some bugs.

Or just export the secret keys:

    $ gpg --export-secret-keys > secret-backup.gpg

You only need the secret keys as they are used to decrypt data. But you can export public keys to. To generate an ASCII version of a user's public key to file *public.key* (e.g. to distribute it by e-mail):

    $ gpg --export --armor --output public.key user-id


Later you can restore keys using the *--import* option:

    $ gpg --import key.gpg

After you import a key from a backup you'll have to make this key trusted. If you skip this step you will get an error on encrypt step:

    gpg: [KEY_ID]: There is no assurance this key belongs to the named user
    gpg: [stdin]: encryption failed: Unusable public key
    Password encryption aborted.

To mark the key as trusted execute:

    $ gpg --edit-key KEY_ID
    gpg> trust

where:

**KEY_ID** — is the ID that you can get from the error message

    Please decide how far you trust this user to correctly verify other users' keys
    (by looking at passports, checking fingerprints from different sources, etc.)
        1 = I don't know or won't say
        2 = I do NOT trust
        3 = I trust marginally
        4 = I trust fully
        5 = I trust ultimately
        m = back to the main menu
    Your decision? 5
    Do you really want to set this key to ultimate trust? (y/N) y


## Read more

[Linux: GPG-keys, Pass – passwords manager, and passwords import from a KeePass database](https://dev.to/setevoy/linux-gpg-keys-the-pass-passwords-manager-and-passwords-import-from-the-keepass-database-1j8f)

[GnuPG in Arch wiki](https://wiki.archlinux.org/index.php/GnuPG#Export_your_public_key)