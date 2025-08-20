# Creating Asymmetric Keys

- Use openssl to create asymmetric keys with the appropriate algorithm as required.

### Generate private key

```
	openssl genpkey -algorithm RSA -out private.key -pkeyopt rsa_keygen_bits:3072
```

- `algorithm` - the public key algorithm
- `out`- output file
- `pkeyopt`- public key options

### Generate public key for the private key

```
	openssl rsa -in private.key -out public.key -pubout
```

- `in` - input file
- `out`- output file
- `pubout`- output a public key

### Encrypt the private key using a passphrase (Optional)

- In order the keep the private key secure from unauthorised access, it can be additionally encrypted with a passphrase.

```
	openssl rsa -in private.key -out private_encrypted.key -aes256
```

- `in` - input file
- `out`- output file
- `aes256` - encrypt PEM output with cbc aes

- Enter the passphrase when prompted, re-enter it to verify it.

### Decrypt the encrypted private key

```
	openssl rsa -in private_encrypted.key -out private_decrypted.key
```

- Enter the correct passphrase to decrypt the private key.