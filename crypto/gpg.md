
# GNU Privacy Guard quick start

## Contents

[Initialize the key chain](#init)

[Symmetric encryption](#sym)

[Decrypt a messge](#decrypt)

[List available keys](#list)

[Add a subkey](#sub)

[Change expiration date of a key](#expire)

[Verify a signature](#sig)

[View supported by current version algorithms list](#version)

[Read more](#more)


<a name="init"></a>

## Initialize the key chain

    $ gpg --generate-key

<a name='sym'></a>

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

    # Specify output file
    gpg --output message.txt.gpg --symmeteric message.txt
    
    # Encrypt and sign (all in the single output file)
    gpg --sign --symmetric message.txt

**-c, --symmetric** use symmetric encryption

<a name='decrypt'></a>

## Decrypt a messge

    $ gpg -d FILENAME

    # Decrypt and put output in decrypted.txt
    gpg --decrypt FILENAME > decrypted.txt

<a name='list'></a>

## List available keys

    $ gpg --list-keys

In the current version it doesn't show **KEY_ID**. To get the id of a key enter in edit mode and you'll see KEY_ID of each key in the list:

    $ gpg --edit-key USER_EMAIL

Below the Hello message you'll find the list of the keys including KEY_ID:

    sec  rsa3072/MDNSODSD2982DDS
    created: 2020-10-14  expires: 2029-10-12  usage: SC  
    trust: ultimate      validity: ultimate
    ssb  rsa3072/2ELDNS2LLL9DNB8
    created: 2020-10-14  expires: 2022-10-14  usage: E   
    ssb  rsa4096/9CCLDHS99LShs78
    created: 2020-10-14  expires: 2025-10-13  usage: E   
    
The KEY_ID :

- **MDNSODSD2982DDS** secret key id
- **2ELDNS2LLL9DNB8** subkey id
- **9CCLDHS99LShs78** subkey id

Quit the edit mode when you finished:
    
    gpg> quit


<a name='sub'></a>

## Add a subkey

Subkeys are like the normal keys, except they're bound to a master key pair. Subkeys can be revoked independently of the master keys, and also stored separately from them. 

    $ gpg --list-keys
    $ gpg --edit-key USER_EMAIL
    gpg> addkey
    
    ...
    
    gpg> save

<a name='expire'></a>

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

<a name='sig'></a>

## Verify a signature

Let's say you want to download a software package from a website. It is wise to make sure that it wasn't tampered by someone. You can verify the software signature to do so if it is provided by the developers.

The verification process consists of a few steps:

1. Download the public key for the signature. 
1. Make sure that the key is not tampered. You can achieve it by using the [Web of trust](https://en.wikipedia.org/wiki/Web_of_trust). Read the documentation on the site that you download the software from to find some tips about the verification process. 

Mainstream developers such as associated with *Debian* or *Gnome* often provide keys packages that you can install using your package manager. 

In *Arch Linux* you can also install *debian-keyring* package (it's in AUR) and use it to verify the keys:  
    
    $ pamac build debian-keyring

3. test



<a name='version'></a>

## View supported by current version algorithms list

    $ gpg --version

<a name='more'></a>

## Read more

[GPG Tutorial](https://www.devdungeon.com/content/gpg-tutorial#encrypt_symmetrically)

[GnuPG in Arch Linux wiki](https://wiki.archlinux.org/index.php/GnuPG)

