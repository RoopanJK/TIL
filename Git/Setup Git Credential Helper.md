Ref: https://publish.obsidian.md/git-doc/Authentication#HTTPS
(The following instructions are not specific to Obsidian alone but can be used system wide.)

In order to securely store our username and password permanently without having to re-enter it all the time. Git's credential helper can be used.
1. Install `libsecret` to store the password in a secure place.
		```
		sudo apt install libsecret-1-0 libsecret-1-dev make gcc
		```
2. Build the dev package
		```
		sudo make --directory=/usr/share/doc/git/contrib/credential/libsecret 
		```
3. Set the credential helper to libsecret. This can either be done locally to globally using the `--global` flag.
		```
		git config --global credential.helper \ /usr/share/doc/git/contrib/credentail/libsecret/git-credential-libsecret
		```
4. After setting up the credential helper, one action to your git repository must be make for the credential helper to save the credentials.
5. Use [Fine grained tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#fine-grained-personal-access-tokens) for more control over your keys and repositories.