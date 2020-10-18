# GnuPG — Change expiration date of a key

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