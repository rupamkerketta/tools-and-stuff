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

To send a file securely, you encrypt it with your _private_ key and the recipient's _public_
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
Else, if they don't match :x:, the following can be the most probable reasons:
<br />
* A different key was used to sign it.
* The data was altered (intentionally or untentionally).

---

#### Resources and links

* [Subkeys](https://wiki.debian.org/Subkeys)
* [Why does gnupg create 4 separate keys and what does sub and ssb mean?](https://crypto.stackexchange.com/questions/63100/why-does-gnupg-create-4-separate-keys-and-what-does-sub-and-ssb-mean)
* [How To Use GPG to Encrypt and Sign Messages](https://www.digitalocean.com/community/tutorials/how-to-use-gpg-to-encrypt-and-sign-messages)

---

#### Contents:

##### 1. Generating GPG key pair
   * [Creating and Managing a GPG key pair (by Nick Janetakis)](https://www.youtube.com/watch?v=1vVIpIvboSg&t=2s)

       ```
       Topics covered

        - Generating a secure gpg key pair with an expiration date
        - Updating the expiry date of the key
        - Changing the gpg passphrase and keeping it safe
        - Creating a revoke certificate to revoke the key pair on demand
        - Backing up and restoring your key pair and associated files
        - Exporting your gpg public key so you can share it with others
        - Configuring your gpg agent to cache your passphrase for a week
        ```
##### 2. What does revoking a GPG key mean ?
##### 3. Signed git-commits

 * Signing and Verifying Git Commits on the Command Line and Github
 * How git-commit signatures work - using GPG keys ?

##### 4. Using gpg to encrypt files
##### 5. Primary keys and Sub keys
##### 6. Public key servers

---
