# Modifying Root Password of you Image

- inherit `extrausers` class into your image recipe. This allows additional user and group configuration to be applied at image level.
- Generate the hash of your password to be set using the below command.
	```
	printf "%q" $(mkpasswd -m sha256crypt *password* [SALT])
	```
- Add optional SALT if required.
- Set the new password for existing root user using `EXTRA_USER_PARAMS` variable
	```
	EXTRA_USERS_PARAMS = "\
    usermod -p '${PASSWD}' root; \
    "
	```
