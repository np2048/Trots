# GnuPG — Symmetric encryption

If you want to encrypt your data just for yourself i.e you are not planning to share it with other people than symmetric encryption is the best choice:

    $ gpg --symmetric message.txt
    # Prompts you for a passphrase
    # Creates message.txt.gpg (binary)
    
    $ gpg --armor --symmetric message.txt
    # Same, but ASCII format output instead of binary
    # Creates message.txt.asc (ASCII)
    
    # Specify the encryption algorithm
    $ gpg --symmetric --cipher-algo AES256

    # Specify output file
    gpg --output message.txt.gpg --symmeteric message.txt
    
    # Encrypt and sign (all in the single output file)
    gpg --sign --symmetric message.txt

**-c, --symmetric** use symmetric encryption