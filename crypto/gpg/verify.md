# GnuPG — Verify a signature

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

## Read more

[How-to verify GPG key of official .ISO images](https://wiki.manjaro.org/index.php?title=How-to_verify_GPG_key_of_official_.ISO_images)

[Verify the Tails signing key](https://tails.boum.org/install/expert/usb/index.en.html#verify-key)