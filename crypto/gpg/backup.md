
# How to backup and restore gpg keys

You can create a backup just by copying the whole *~/.gnupg* directory. But this is not safe and it is not a recommend way to backup the keys as it may lead to some bugs.

Or just export the secret keys:

    $ gpg --export-secret-keys > secret-backup.gpg

You only need the secret keys as they are used to decrypt data. But you can export public keys to. To generate an ASCII version of a user's public key to file *public.key* (e.g. to distribute it by e-mail):

    $ gpg --export --armor --output public.key user-id


Later you can restore keys using the *--import* option:

    $ gpg --import secret-backup.gpg

## Read more

[Linux: GPG-keys, Pass – passwords manager, and passwords import from a KeePass database](https://dev.to/setevoy/linux-gpg-keys-the-pass-passwords-manager-and-passwords-import-from-the-keepass-database-1j8f)

[GnuPG in Arch wiki](https://wiki.archlinux.org/index.php/GnuPG#Export_your_public_key)