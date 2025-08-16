# SSH Key

- SSH (Secure Shell) is a cryptographic network protocol for operation network services securely over an unsecured network.
- SSH are primarily used for **authentication** purposes, to **connect to remote serves** without using password.
- Components of SSH key
	- Private Key (kept a secret)
	- Public Key (shared among a remote server)
- SSH is **native part** of the Unix-based system, but may not be widely supported on non-Unix platforms such as Windows.
### Generation and Management:

- **SSH Key Generation:**

	```
	ssh-keygen -t rsa -b 4096
	```

- SSH keys **don't have** advanced management features.

#### Security:

- SSH keys are recommended to be generated with a key size of **4096** bits.
- SSH keys can be created without a **passphrase** which leave them vulnerable.

#### Lifetime & Revocation:

- SSH keys don't have any lifetime or revocation functionality.