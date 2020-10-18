# GnuPG — List available keys

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

