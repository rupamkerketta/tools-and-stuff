# GPG encryption

> What is GPG ?

:point_right: `GPG` stands for the `GNU Privacy Guard`. It's a free and open source implementation
of another encryption standard called `PGP` - which stands for `Pretty Good Privacy`.

> PGP was written in 1991 by Phil Zimmerman

GnuPrivacy Guard (GPG) allows you to securely encrypt files so that only the intended
recepient can decrypt them.

GPG relies on the idea of two encryption keys per person. Each person has a _private_
key and a _public_ key. The public key can decrypt something that was encrypted using the
private key.

To send a file securely, you encrypt it with your private key _and_ the recipient's public
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

In most cases, a digital signature in it's simplest form is a _HASH_ (SHA1, MD5, etc.) of the
data (file, git-commit, message, etc.) that is encrypted with the signer's _private key_.
The signer should be the one and only in posession of the _private key_, this is where the
trust comes from. Everyone else should have access to the signer's _public key_.

Next, to verify a _digital signature_, the recipient:
1. Calculates the _HASH_ of the same data (fiel, git-commit, message, etc.)
2. Decrypts the digital signature using the sender's _PUBLIC KEY_, then
3. Compares the two hash values.

If the _HASH_ values match, the signature is considered to be valid :white_check_mark:.
<br />
Else, if they dont match :x:, the follwing can be the most probable reasons:
<br />
* A different key was used to sign it.
* The data was altered (intentionally or untentionally).

