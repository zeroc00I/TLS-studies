# TLS-studies
Work in progress

Drafts from Practical TLS
HTTPS -> HTML transferred with HTTP protected by SSL
But can also protect other data transfer
SSL VPN

Secure sockets layer (Netscap 1994)
Transport Layer security (maintenance handed to IETF in 1999 and renamed protocol to TLS)

# How the secure is made
Confidentiality / Encryption
Integrity / Hashing
Authentication / PKI

Anti-replay: Request transfering 100. A MitM trying to repeat the request.
Provided with built-in sequence numbers
Built in to integrity + authentication mechanism

Non repudiation:
Sender cannot later deny sending a message

Key players:
* Client
Optionally authenticated (rare)

* Server
Always authenticated / Always provide the certificate

* Certificate Authority
Provides de Trust Anchor
Five organizations secure 98% of the internet
IdenTrust -> Lets encrypt (51.9) | Digicert -> Geotrust (19.4) | Sectigo -> Comodo (17.5) | Godaddy (6.9) | Globalsign (2.9)

# Tls/SSL version
- SSL 1.0 (1994 - Netscape)
Never publicly released. Full of flaws.
- SSL 2.0 (1995 - Netscape)
Still full of flaws
- SSL 3.0 (1996 - Netscape. Predominant version of SSL through ~ 2014)
Introduced concept of certificate chains
Added compression capability -> Vulnerabilities was found
Options support for adicionar key exchange
RFC published 6101
Poodle attack released october 2014 (SSL 3.0)

SSL 3.0 foundation of TLS version we use today:
All TLS version are minor incrementor of SSL 3.0

- TLS 1.0 (1990) - RFC 2246
Few minor changes: HMAC support
Major vulnerability: BEAST (Attack on CBC ciphers)
Mitigated in modern browsers

- TLS 1.1 (2006) - RFC 4346
Formally deprecated "EXPORT grade" ciphers
Protection against CBC attack (i.g, BEAST)

TLS v1.0 and TLS v1.1 deprecated March 2021
Fails most compliance (PCI, NIST)

TLS v1.2 (2008) - RFC 5246
- Improved security of key generation
- Introduced suport for AEAD Ciphers (Authenticated Encryption With Associated Data)

TLS v1.3 (2018) - RFC 8446
- Shorter Handshake (2 messaves vs 5+)
- 0-RTT Resumption
- Forward Secrecy required
- AEAD Ciphers required
- Favors security and simplicity over backwars compability
- Insecure algorithms removed


# Criptography

# Hashing used to provide integrity, it must satisfy four requirements:
- Infeasible to produce a given digest
- Impossible to extract original message
- Slight changes produce drastic differences
- Resulting digest is fixed width (length)

Collision are a bad thing that occurs when two messages result in identical digests
Cannot be avoided. Its a byproduct of "fixed width digests"
Can only be made more rare

Examples: https://web.archive.org/web/20131020122204/http://www2.mat.dtu.dk/people/S.Thomsen/wangmd5/samples.html

Common Hashing Algorithms:
- Md5 -> 128 bits
- Sha/Sha1 -> 160 bits
- Sha2 Family

Interceptor can modify the message and re-calculate Hash.
Receiver compares their Digest against modified Digest
Simply hashing the message isnt enought
Both parties establish a mutual Secret Key
Message Authentication Code (MAC) = Combining Message + Secret Key when calculating Digest
Example: HMAC (Hash Based Message Authentication Code)

Encryption:
Simple encryption: Transforms plaintext into cipher text
- Doesnt scale
- Hard to do securely
- Cannot simple use a Standard Algorithm

Key Based encryption:
- Combines indestru vetted algorithm with a Secret Key
- Algorithm is created by experts
- Secret Keys can be randomly generated

Two type of Key Based Encryption
Symetric -> Encrypt / Decrypt using same keys
Asymmetric -> Encrypt / Decrypt using different keys
(Two different keys that are mathematically related)
One key will be made Public
Other key will be kept Private

Symetric: 
- Des
- RC4
- 3DES
- AES

Asymmetric:
- DSA
- RSA
- ECDSA
- ECDH
- Diffie-Hellman






























