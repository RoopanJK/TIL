# GPG Key

- GPG (GNU Privacy Guard) is a public key cryptography implementation that allows us to **encrypt** and **sign** data and communication.
- Widely used for **email encryption** and **Digital Signing**
- Allows to create **digital signatures** that verify the author and integrity of the message/file.
- GPG keys can also be used for authentication using **GPG Agent**, but is less common compared to [SSH Keys](./ssh-key.md)
- GPG has compatibility with email clients and encryption software as it is based on widely adopted **OpenPGP** standard.
- It is well supported on various platforms such as Windows, MacOS, Linux.
### Generation and Management:

- **GPG Key Generation:**

	```
	gpg --full-generate-key
	```

- More comprehensive management which allows to **manage**, **revoke**, **expire** multiple keys.
- Designate sub-keys for specific functions.

#### Security:

- GPG keys are generated using **RSA** with key size of **2048** bits.
- GPG keys are always encrypted with a **passphrase**

#### Lifetime & Revocation:

- Keys can have a expiration data and can be revoked anytime