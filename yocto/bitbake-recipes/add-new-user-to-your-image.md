# Add New User to you Image

- inherit `extrausers` class into your image recipe. This allows additional user and group configuration to be applied at image level.
- Generate the hash of your password to be set using the below command.
	```
	printf "%q" $(mkpasswd -m sha256crypt *password* [SALT])
	```
- Add optional SALT if required.
- Supply the hashed password and user name to be created to `EXTRA_USER_PARAMS` variable
	```
	EXTRA_USERS_PARAMS = "\
    useradd -p '${PASSWD}' *new-user*; \
    "
	```
- Further modification can be done using the usermod command set in the `EXTRA_USER_PARAMS` variable if required.