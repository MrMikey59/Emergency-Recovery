
## Private Communication

Use 
- [Signal](https://www.signal.org/) ([setup
instructions](https://medium.com/@mshelton/signal-for-beginners-c6b44f76a1f0)
- [Wire](https://wire.com/en/) is [fine too](https://www.securemessagingapps.com/); 
- WhatsApp is okay; [don't use Telegram](https://twitter.com/bascule/status/897187286554628096)).

E-mail is particularly problematic, even if PGP signed. It's not generally forward-secure, and the key-distribution problem is pretty severe. [keybase.io](https://keybase.io/) helps, and is useful for a number of other reasons. Also, PGP keys are generally handled on desktop computers, which is one of the least secure computing environments.

## File Security

File security is hard, and operates on many level. What is it you're
trying to secure against?

[![$5 wrench](https://imgs.xkcd.com/comics/security.png)](https://xkcd.com/538/)

 - Offline attacks (someone steals your laptop while it's off): turn on
   full disk encryption. ([cryptsetup +
   LUKS](https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_a_non-root_file_system)
   on Linux,
   [BitLocker](https://fossbytes.com/enable-full-disk-encryption-windows-10/)
   on Windows, [FileVault](https://support.apple.com/en-us/HT204837) on
   macOS. Note that this won't help if the attacker _also_ has you and
   really wants your secrets.
 - Online attacks (someone has your laptop and it's on): use file
   encryption. There are two primary mechanisms for doing so
    - Encrypted filesystems: stacked filesystem encryption software encrypts files individually rather than having encrypted block devices. You can "mount" these filesystems by providing the decryption key, and then browse the files inside it freely. When you unmount it, those files are all unavailable.  Modern solutions include [gocryptfs](https://github.com/rfjakob/gocryptfs) and [eCryptFS](http://ecryptfs.org/). More detailed comparisons can be found [here](https://nuetzlich.net/gocryptfs/comparison/) and [here](https://wiki.archlinux.org/index.php/disk_encryption#Comparison_table)
    - Encrypted files: encrypt individual files with symmetric
      encryption (see `gpg -c`) and a secret key. Or, like `pass`, also
      encrypt the key with your public key so only you can read it back
      later with your private key. Exact encryption settings matter a
      lot!
 - [Plausible
   deniability](https://en.wikipedia.org/wiki/Plausible_deniability)
   (what seems to be the problem officer?): usually lower performance,
   and easier to lose data. Hard to actually prove that it provides
   [deniable
   encryption](https://en.wikipedia.org/wiki/Deniable_encryption)! See
   the [discussion
   here](https://security.stackexchange.com/questions/135846/is-plausible-deniability-actually-feasible-for-encrypted-volumes-disks),
   and then consider whether you may want to try
   [VeraCrypt](https://www.veracrypt.fr/en/Home.html) (the maintained
   fork of good ol' TrueCrypt).
 - Encrypted backups: use [Tarsnap](https://www.tarsnap.com/) or [Borgbase](https://www.borgbase.com/)
    - Think about whether an attacker can delete your backups if they
      get a hold of your laptop!

## Internet Security & Privacy

The internet is a _very_ scary place. Open WiFi networks
[are](https://www.troyhunt.com/the-beginners-guide-to-breaking-website/)
[scary](https://www.troyhunt.com/talking-with-scott-hanselman-on/). Make
sure you delete them afterwards, otherwise your phone will happily
announce and re-connect to something with the same name later!

If you're ever on a network you don't trust, a VPN _may_ be worthwhile,
but keep in mind that you're trusting the VPN provider _a lot_. Do you
really trust them more than your ISP? If you truly want a VPN, use a
provider you're sure you trust, and you should probably pay for it. Or
set up [WireGuard](https://www.wireguard.com/) for yourself -- it's
[excellent](https://web.archive.org/web/20210526211307/https://latacora.micro.blog/there-will-be/)!

There are also secure configuration settings for a lot of internet-enabled
applications at [cipherlist.eu](https://cipherlist.eu/). If you're particularly
privacy-oriented, [privacytools.io](https://privacytools.io) is also a good
resource.

Some of you may wonder about [Tor](https://www.torproject.org/). Keep in
mind that Tor is _not_ particularly resistant to powerful global
attackers, and is weak against traffic analysis attacks. It may be
useful for hiding traffic on a small scale, but won't really buy you all
that much in terms of privacy. You're better off using more secure
services in the first place (Signal, TLS + certificate pinning, etc.).

## Web Security

So, you want to go on the Web too?
Jeez, you're really pushing your luck here.

Install [HTTPS Everywhere](https://www.eff.org/https-everywhere).
SSL/TLS is
[critical](https://www.troyhunt.com/ssl-is-not-about-encryption/), and
it's _not_ just about encryption, but also about being able to verify
that you're talking to the right service in the first place! If you run
your own web server, [test it](https://ssldecoder.eu/) and [test it
again](https://www.ssllabs.com/ssltest/index.html). TLS configuration
[can get hairy](https://wiki.mozilla.org/Security/Server_Side_TLS).
HTTPS Everywhere will do its very best to never navigate you to HTTP
sites when there's an alternative. That doesn't save you, but it helps.
If you're truly paranoid, blacklist any SSL/TLS CAs that you don't
absolutely need.

Install [uBlock Origin](https://github.com/gorhill/uBlock). It is a
[wide-spectrum
blocker](https://github.com/gorhill/uBlock/wiki/Blocking-mode) that
doesn't just stop ads, but all sorts of third-party communication a page
may try to do. And inline scripts and such. If you're willing to spend
some time on configuration to make things work, go to [medium
mode](https://github.com/gorhill/uBlock/wiki/Blocking-mode:-medium-mode)
or even [hard
mode](https://github.com/gorhill/uBlock/wiki/Blocking-mode:-hard-mode).
Those _will_ make some sites not work until you've fiddled with the
settings enough, but will also significantly improve your online
security.

If you're using Firefox, enable [Multi-Account
Containers](https://support.mozilla.org/en-US/kb/containers). Create
separate containers for social networks, banking, shopping, etc. Firefox
will keep the cookies and other state for each of the containers totally
separate, so sites you visit in one container can't snoop on sensitive
data from the others. In Google Chrome, you can use [Chrome
Profiles](https://support.google.com/chrome/answer/2364824) to achieve
similar results.

## Entropy

[Entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory)) is a
measure of randomness. This is useful, for example, when determining the
strength of a password.

![XKCD 936: Password Strength](https://imgs.xkcd.com/comics/password_strength.png)

As the above [XKCD comic](https://xkcd.com/936/) illustrates, a password like
"correcthorsebatterystaple" is more secure than one like "Tr0ub4dor&3". But how
do you quantify something like this?

Entropy is measured in _bits_, and when selecting uniformly at random from a
set of possible outcomes, the entropy is equal to `log_2(# of possibilities)`.
A fair coin flip gives 1 bit of entropy. A dice roll (of a 6-sided die) has
\~2.58 bits of entropy.

You should consider that the attacker knows the _model_ of the password, but
not the randomness (e.g. from [dice
rolls](https://en.wikipedia.org/wiki/Diceware)) used to select a particular
password.

How many bits of entropy is enough? It depends on your threat model. For online
guessing, as the XKCD comic points out, \~40 bits of entropy is pretty good. To
be resistant to offline guessing, a stronger password would be necessary (e.g.
80 bits, or more).

## Hash functions

A [cryptographic hash
function](https://en.wikipedia.org/wiki/Cryptographic_hash_function) maps data
of arbitrary size to a fixed size, and has some special properties. A rough
specification of a hash function is as follows:

```
hash(value: array<byte>) -> vector<byte, N>  (for some fixed N)
```

An example of a hash function is [SHA1](https://en.wikipedia.org/wiki/SHA-1),
which is used in Git. It maps arbitrary-sized inputs to 160-bit outputs (which
can be represented as 40 hexadecimal characters). We can try out the SHA1 hash
on an input using the `sha1sum` command:

```console
$ printf 'hello' | sha1sum
aaf4c61ddcc5e8a2dabede0f3b482cd9aea9434d
$ printf 'hello' | sha1sum
aaf4c61ddcc5e8a2dabede0f3b482cd9aea9434d
$ printf 'Hello' | sha1sum 
f7ff9e8b7bb2e09b70935a5d785e0cc5d9d0abf0
```

At a high level, a hash function can be thought of as a hard-to-invert
random-looking (but deterministic) function (and this is the [ideal model of a
hash function](https://en.wikipedia.org/wiki/Random_oracle)). A hash function
has the following properties:

- Deterministic: the same input always generates the same output.
- Non-invertible: it is hard to find an input `m` such that `hash(m) = h` for
some desired output `h`.
- Target collision resistant: given an input `m_1`, it's hard to find a
different input `m_2` such that `hash(m_1) = hash(m_2)`.
- Collision resistant: it's hard to find two inputs `m_1` and `m_2` such that
`hash(m_1) = hash(m_2)` (note that this is a strictly stronger property than
target collision resistance).

Note: while it may work for certain purposes, SHA-1 is [no
longer](https://shattered.io/) considered a strong cryptographic hash function.
You might find this table of [lifetimes of cryptographic hash
functions](https://valerieaurora.org/hash.html) interesting. However, note that
recommending specific hash functions is beyond the scope of this lecture. If you
are doing work where this matters, you need formal training in
security/cryptography.

### Applications

- Git, for content-addressed storage. The idea of a [hash
function](https://en.wikipedia.org/wiki/Hash_function) is a more general
concept (there are non-cryptographic hash functions). Why does Git use a
cryptographic hash function?
- A short summary of the contents of a file. Software can often be downloaded
from (potentially less trustworthy) mirrors, e.g. Linux ISOs, and it would be
nice to not have to trust them. The official sites usually post hashes
alongside the download links (that point to third-party mirrors), so that the
hash can be checked after downloading a file.
- [Commitment schemes](https://en.wikipedia.org/wiki/Commitment_scheme).
Suppose you want to commit to a particular value, but reveal the value itself
later. For example, I want to do a fair coin toss "in my head", without a
trusted shared coin that two parties can see. I could choose a value `r =
random()`, and then share `h = sha256(r)`. Then, you could call heads or tails
(we'll agree that even `r` means heads, and odd `r` means tails). After you
call, I can reveal my value `r`, and you can confirm that I haven't cheated by
checking `sha256(r)` matches the hash I shared earlier.

## Key derivation functions

A related concept to cryptographic hashes, [key derivation
functions](https://en.wikipedia.org/wiki/Key_derivation_function) (KDFs) are
used for a number of applications, including producing fixed-length output for
use as keys in other cryptographic algorithms. Usually, KDFs are deliberately
slow, in order to slow down offline brute-force attacks.

### Applications

- Producing keys from passphrases for use in other cryptographic algorithms
(e.g. symmetric cryptography, see below).
- Storing login credentials. Storing plaintext passwords is bad; the right
approach is to generate and store a random
[salt](https://en.wikipedia.org/wiki/Salt_(cryptography)) `salt = random()` for
each user, store `KDF(password + salt)`, and verify login attempts by
re-computing the KDF given the entered password and the stored salt.

## Symmetric cryptography

Hiding message contents is probably the first concept you think about when you
think about cryptography. Symmetric cryptography accomplishes this with the
following set of functionality:

```
keygen() -> key  (this function is randomized)

encrypt(plaintext: array<byte>, key) -> array<byte>  (the ciphertext)
decrypt(ciphertext: array<byte>, key) -> array<byte>  (the plaintext)
```

The encrypt function has the property that given the output (ciphertext), it's
hard to determine the input (plaintext) without the key. The decrypt function
has the obvious correctness property, that `decrypt(encrypt(m, k), k) = m`.

An example of a symmetric cryptosystem in wide use today is
[AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard).

### Applications

- Encrypting files for storage in an untrusted cloud service. This can be
combined with KDFs, so you can encrypt a file with a passphrase. Generate `key
= KDF(passphrase)`, and then store `encrypt(file, key)`.

## Asymmetric cryptography

The term "asymmetric" refers to there being two keys, with two different roles.
A private key, as its name implies, is meant to be kept private, while the
public key can be publicly shared and it won't affect security (unlike sharing
the key in a symmetric cryptosystem). Asymmetric cryptosystems provide the
following set of functionality, to encrypt/decrypt and to sign/verify:

```
keygen() -> (public key, private key)  (this function is randomized)

encrypt(plaintext: array<byte>, public key) -> array<byte>  (the ciphertext)
decrypt(ciphertext: array<byte>, private key) -> array<byte>  (the plaintext)

sign(message: array<byte>, private key) -> array<byte>  (the signature)
verify(message: array<byte>, signature: array<byte>, public key) -> bool  (whether or not the signature is valid)
```

The encrypt/decrypt functions have properties similar to their analogs from
symmetric cryptosystems. A message can be encrypted using the _public_ key.
Given the output (ciphertext), it's hard to determine the input (plaintext)
without the _private_ key. The decrypt function has the obvious correctness
property, that `decrypt(encrypt(m, public key), private key) = m`.

Symmetric and asymmetric encryption can be compared to physical locks. A
symmetric cryptosystem is like a door lock: anyone with the key can lock and
unlock it. Asymmetric encryption is like a padlock with a key. You could give
the unlocked lock to someone (the public key), they could put a message in a
box and then put the lock on, and after that, only you could open the lock
because you kept the key (the private key).

The sign/verify functions have the same properties that you would hope physical
signatures would have, in that it's hard to forge a signature. No matter the
message, without the _private_ key, it's hard to produce a signature such that
`verify(message, signature, public key)` returns true. And of course, the
verify function has the obvious correctness property that `verify(message,
sign(message, private key), public key) = true`.

### Applications

- [PGP email encryption](https://en.wikipedia.org/wiki/Pretty_Good_Privacy).
People can have their public keys posted online (e.g. in a PGP keyserver, or on
[Keybase](https://keybase.io/)). Anyone can send them encrypted email.
- Private messaging. Apps like [Signal](https://signal.org/) and
[Keybase](https://keybase.io/) use asymmetric keys to establish private
communication channels.
- Signing software. Git can have GPG-signed commits and tags. With a posted
public key, anyone can verify the authenticity of downloaded software.

### Key distribution

Asymmetric-key cryptography is wonderful, but it has a big challenge of
distributing public keys / mapping public keys to real-world identities. There
are many solutions to this problem. Signal has one simple solution: trust on
first use, and support out-of-band public key exchange (you verify your
friends' "safety numbers" in person). PGP has a different solution, which is
[web of trust](https://en.wikipedia.org/wiki/Web_of_trust). Keybase has yet
another solution of [social
proof](https://keybase.io/blog/chat-apps-softer-than-tofu) (along with other
neat ideas). Each model has its merits; we (the instructors) like Keybase's
model.

## Case studies

### Password managers

This is an essential tool that everyone should try to use (e.g.
[KeePassXC](https://keepassxc.org/), [pass](https://www.passwordstore.org/),
and [1Password](https://1password.com)). Password managers make it convenient to use unique,
randomly generated high-entropy passwords for all your logins, and they save
all your passwords in one place, encrypted with a symmetric cipher with a key
produced from a passphrase using a KDF.

Using a password manager lets you avoid password reuse (so you're less impacted
when websites get compromised), use high-entropy passwords (so you're less likely to
get compromised), and only need to remember a single high-entropy password.

## #Two-factor authentication

[Two-factor
authentication](https://en.wikipedia.org/wiki/Multi-factor_authentication)
(2FA) requires you to use a passphrase ("something you know") along with a 2FA
authenticator (like a [YubiKey](https://www.yubico.com/), "something you have")
in order to protect against stolen passwords and
[phishing](https://en.wikipedia.org/wiki/Phishing) attacks.

### Full disk encryption

Keeping your laptop's entire disk encrypted is an easy way to protect your data
in the case that your laptop is stolen. You can use [cryptsetup +
LUKS](https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_a_non-root_file_system)
on Linux,
[BitLocker](https://fossbytes.com/enable-full-disk-encryption-windows-10/) on
Windows, or [FileVault](https://support.apple.com/en-us/HT204837) on macOS.
This encrypts the entire disk with a symmetric cipher, with a key protected by
a passphrase.

###Private messaging

Use [Signal](https://signal.org/) or [Keybase](https://keybase.io/). End-to-end
security is bootstrapped from asymmetric-key encryption. Obtaining your
contacts' public keys is the critical step here. If you want good security, you
need to authenticate public keys out-of-band (with Signal or Keybase), or trust
social proofs (with Keybase).

### SSH

We've covered the use of SSH and SSH keys in an [earlier
lecture](/2020/command-line/#remote-machines). Let's look at the cryptography
aspects of this.

When you run `ssh-keygen`, it generates an asymmetric keypair, `public_key,
private_key`. This is generated randomly, using entropy provided by the
operating system (collected from hardware events, etc.). The public key is
stored as-is (it's public, so keeping it a secret is not important), but at
rest, the private key should be encrypted on disk. The `ssh-keygen` program
prompts the user for a passphrase, and this is fed through a key derivation
function to produce a key, which is then used to encrypt the private key with a
symmetric cipher.

In use, once the server knows the client's public key (stored in the
`.ssh/authorized_keys` file), a connecting client can prove its identity using
asymmetric signatures. This is done through
[challenge-response](https://en.wikipedia.org/wiki/Challenge%E2%80%93response_authentication).
At a high level, the server picks a random number and sends it to the client.
The client then signs this message and sends the signature back to the server,
which checks the signature against the public key on record. This effectively
proves that the client is in possession of the private key corresponding to the
public key that's in the server's `.ssh/authorized_keys` file, so the server
can allow the client to log in.

{% comment %}
extra topics, if there's time

security concepts, tips
- biometrics
- HTTPS
{% endcomment %}

## Resources

- [Last year's notes](/2019/security/): from when this lecture was more focused on security and privacy as a computer user
- [Cryptographic Right Answers](https://latacora.micro.blog/2018/04/03/cryptographic-right-answers.html): answers "what crypto should I use for X?" for many common X.

