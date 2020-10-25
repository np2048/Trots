
# How to transfer keys to another machine

If you need to share the same keys on multiple devices the safest way to transfer the keys is to use [SSH](../../linux/ssh.md) without an intermediate file:

    $ gpg --export-secret-keys -a | ssh OTHER_MACHINE gpg --import

where:

- **-a** or --armor — Create ASCII armored output
- **OTHER_MACHINE** — IP address or hostname of remote SSH server that will receive the keys

## Read more

[How to share one pgp-key on multiple machines?](https://askubuntu.com/questions/32438/how-to-share-one-pgp-key-on-multiple-machines)