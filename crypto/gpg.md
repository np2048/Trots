
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


<a name='init'></a>

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
1. Import the key to the **gpg keychain**:

    $ gpg --import signing.key

1. Make sure that the key is not tampered. You can achieve it by using the [Web of trust](https://en.wikipedia.org/wiki/Web_of_trust). Read the documentation on the site that you download the software from to find some tips about the verification process. 

    Mainstream developers such as associated with *Debian* or *Gnome* often provide keys packages that you can install using your package manager. 
    
    In *Arch Linux* you can also install *debian-keyring* package (it's in AUR) and use it to verify the keys:  
        
        $ pamac build debian-keyring
    
    Once it is installed you can import the keys of the top developers such as [Chris Lamb](https://en.wikipedia.org/wiki/Chris%5FLamb%5F%28software%5Fdeveloper%29) or [Philip Müller](https://www.manjaro.org/team/) into your keyring:
    
        $ gpg --keyring=/usr/share/keyrings/debian-keyring.gpg --export chris@chris-lamb.co.uk | gpg --import
        $ gpg --keyring=/usr/share/keyrings/debian-keyring.gpg --export philm@manjaro.org | gpg --import

1. Download the signature file and make sure that it has the same name that the file you are verifying but with an additional extension *.sig*

1. Run the signature verification process:

    $ gpg --verify SIGNATURE.sig

    Example: 
    
        gpg --verify manjaro-awesome-20.0-200428-linux56.iso.sig
        gpg: assuming signed data in 'manjaro-awesome-20.0-200428-linux56.iso'
        gpg: Signature made Tu 28 apr 2020 15:34:46 UTS
        gpg:                using RSA key 3B6B8D2B9293A297E1DD1F9E7605992471F3F073
        gpg: Good signature from "Frede Hundewadt <fh@manjaro.org>" [unknown]
        gpg: WARNING: This key is not certified with a trusted signature!
        gpg:          There is no indication that the signature belongs to the owner.
        Primary key fingerprint: 04BB 537F 5BC2 D399 BFA7  2F8F 17C7 52B6 1B2F 2E90
             Subkey fingerprint: 3B6B 8D2B 9293 A297 E1DD  1F9E 7605 9924 71F3 F073
    
    *Good signature* means that the file corresponds to the signature. Now let's make sure that we can trust the signature key.
    
1. Copy the *Primary key fingerprint* from the verification results and delete all space characters from it:

        Primary key fingerprint: 04BB 537F 5BC2 D399 BFA7  2F8F 17C7 52B6 1B2F 2E90
        $  echo '04BB 537F 5BC2 D399 BFA7  2F8F 17C7 52B6 1B2F 2E90' | sed 's/ //g'
        04BB537F5BC2D399BFA72F8F17C752B61B2F2E90

1. Verify the *Primary key fingerprint*:

        $ gpg --keyid-format 0xlong --check-sigs 04BB537F5BC2D399BFA72F8F17C752B61B2F2E90
    
    *sig!* means that the key can be trusted:

        pub   rsa4096/0x17C752B61B2F2E90 2017-05-30 [SC]
              04BB537F5BC2D399BFA72F8F17C752B61B2F2E90
        uid                   [ unknown] Frede Hundewadt <fh@manjaro.org>
        sig!         0x1817DC63CD3B5DF5 2017-09-15  Thanos Apostolou (manjaro maintainer) <thanos@manjaro.org>
        sig!         0x8DB9F8C18DF53602 2017-05-31  Stefano Capitani <stefano@manjaro.org>
        sig!         0xE3B3F44AC45EE0AA 2017-05-31  artoo-manjaro <artoo@manjaro.org>
        sig!         0xDAD3B211663CA268 2017-05-31  Bernhard Landauer <oberon@manjaro.org>
        sig!         0xCAA6A59611C7F07E 2017-05-31  Philip Müller (Called Little) <philm@manjaro.org>
        sig!         0x2C089F09AC97B894 2017-06-03  Ramon Buldó <ramon@manjaro.org>
        sig!3        0x17C752B61B2F2E90 2017-05-30  Frede Hundewadt <fh@manjaro.org>
        sub   rsa2048/0x8396F1D05506E82D 2017-05-30 [E] [expires: 2025-05-28]
        sig!         0x17C752B61B2F2E90 2017-05-30  Frede Hundewadt <fh@manjaro.org>
        sub   rsa2048/0x7605992471F3F073 2017-05-30 [SA] [expires: 2025-05-28]
        sig!         0x17C752B61B2F2E90 2017-05-30  Frede Hundewadt <fh@manjaro.org>
        
        gpg: 9 good signatures
        gpg: 1 signature not checked due to a missing key


<a name='version'></a>

## View supported by current version algorithms list

    $ gpg --version

<a name='more'></a>

## Read more

[GPG Tutorial](https://www.devdungeon.com/content/gpg-tutorial#encrypt_symmetrically)

[GnuPG in Arch Linux wiki](https://wiki.archlinux.org/index.php/GnuPG)

[Creating GPG Keys — Fedora wiki](https://fedoraproject.org/wiki/Creating_GPG_Keys)

[How-to verify GPG key of official .ISO images](https://wiki.manjaro.org/index.php?title=How-to_verify_GPG_key_of_official_.ISO_images)

[Verify the Tails signing key](https://tails.boum.org/install/expert/usb/index.en.html#verify-key)