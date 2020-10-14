
# GNU Privacy Guard quick start

## Initialize the key chain

    $ gpg --gen-key

## Symmetric encryption

If you want to encrypt your data just for yourself i.e you are not planning to share it with other people than symmetric encryption is the best choice:

    $ gpg --symmetric message.txt
    # Prompts you for a passphrase
    # Creates message.txt.gpg (binary)
    
    $ gpg --armor --symmetric message.txt
    # Same, but ASCII format output instead of binary
    # Creates message.txt.asc (ASCII)
    
    # Specify the encryption algorithm
    $ gpg --symmetric --cipher-algo AES256


## List available keys

    $ gpg --list-keys

## Change expiration date of a key

    $ gpg --list-keys
    $ gpg --edit-key USER_EMAIL
    gpg> expire
    
    Changing expiration time for the primary key.
    Please specify how long the key should be valid.
             0 = key does not expire
          <n>  = key expires in n days
          <n>w = key expires in n weeks
          <n>m = key expires in n months
          <n>y = key expires in n years
    Key is valid for? (0)

Press &lt;Enter&gt; for the default value: 0 (key never exipires) or enter a number and a letter corresponding to expiration period. 

For example. Key expires in 3 years:

    Key is valid for? (0) 3y

Key expires in 7 days:
    
    Key is valid for? (0) 7

When you finished editing a key enter the save command to apply the changes:

    gpg> save

<a name='version'></a>

# View supported by current version algorithms list

    $ gpg --version

## Read more

[GPG Tutorial](https://www.devdungeon.com/content/gpg-tutorial#encrypt_symmetrically)

