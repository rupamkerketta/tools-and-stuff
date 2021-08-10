# GPG encryption

> What is GPG ?

:point_right: `GPG` stands for the `GNU Privacy Guard`. It's a free and open source implementation
of another encryption standard called `PGP` - which stands for `Pretty Good Privacy`.

> PGP was written in 1991 by [Phil Zimmermann](https://en.wikipedia.org/wiki/Phil_Zimmermann)

GnuPrivacy Guard (GPG) allows you to securely encrypt files so that only the intended
recepient can decrypt them.

GPG relies on the idea of two encryption keys per person. Each person has a _private_
key and a _public_ key. The _public_ key can decrypt something that was encrypted using the
_private_ key.

To send a file securely, you encrypt it with your _private_ key _and_ the recipient's _public_
key. To decrypt the file, they need their private key _and_ your public key.

---

> Where are they used ?

:point_right: GPG encryption is often used by:
* financial institutions
* banks
* healthcare
* tech firms
* and other highly regulated industries

The main goal is to protect _sensitive_ data.

---

> How can it be used to verify a _digital signature_ ?

:point_right: First, understanding what really is a _digital signature_.

In most cases, a `digital signature` in it's simplest form is a _HASH_ (SHA1, MD5, etc.) of the
data (file, git-commit, message, etc.) that is encrypted with the signer's _private_ key.
The signer should be the one and only in posession of the _private_ key, this is where the
trust comes from. Everyone else should have access to the signer's _public_ key.

Next, to verify a _digital signature_, the recipient:
1. Calculates the _HASH_ of the same data (file, git-commit, message, etc.)
2. Decrypts the digital signature using the sender's _public_ key, then
3. Compares the two _HASH_ values.

If the _HASH_ values match, the signature is considered to be valid :heavy_check_mark:.
<br />
Else, if they dont match :x:, the follwing can be the most probable reasons:
<br />
* A different key was used to sign it.
* The data was altered (intentionally or untentionally).

---

#### Contents:

1. [Generating GPG key pair](#1.-generating-gpg-key-pair)
2. Editing the expiry date of the date of the key
3. What does revoking a GPG key mean ?
4. Creating revoke certificates
5. Backing-Up the keys
6. Signed git-commits

   * How to set the time duration for cached password ?
   * How git-commit signatures work - using GPG keys ?

---

#### 1. Generating GPG key pair

The `--full-generate-key` option let's the use generate the _GPG key pair_ in an interactive
session, within the terminal window.

```bash
user@host:~ $ gpg --full-generate-key
```

1. You'll be asked to pick an encryption type from a menu. Unless you have a good
reason not to, type 1 and press `Enter`
```bash
Please select what kind of key you want:
    (1) RSA and RSA (default)
    (2) DSA and Elgamal
    (3) DSA (sign only)
    (4) RSA (sign only)
   (14) Existing key from card
Your selection? 1
```

2. Generally, I use `4096` as the bit size. :point_down:
```bash
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 4096
```

3. You can choose the expiry date for the public key. **_The private key is not affected by
this configuration._** The user can still use the _private_ key for encryption, but of
the _public_ key is no longer valid, then the intended recipient won't be able to decrypt
the data(file, git-commit, message, etc.) using the senders _public_ key.

```bash
Requested keysize is 4096 bits
Please Specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for> (0) 0
```

```bash
Key does not expire at all
Is this correct? (y/N) y
```

```bash
GnuPG needs to construct a user ID to identify your key.

Real name: <FirstName><Space><LastName>
Email address: user@mail.com
Comment:
```

```bash
You selected this USER-ID:
    "Username <username@mail.com>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
```

```bash
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key <KEY_ID> marked as ultimately trusted
gpg: revocation certificate stored as '/home/user/.gnupg/openpgp-revocs.d/<ID>.rev'
public and secret key created and signed.

pub   rsa4096 2021-07-31 [SC]
      <SOME_ID>
uid                      John Doe <user@mail.com>
sub   rsa4096 2021-07-31 [E]
```
