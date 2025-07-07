# User Groups

- Groups are used to simplify user management with similar roles which allow administrators to apply permissions to a group of users.
- They are also used to facilitate controlled access to files, directories. Permission can be assigned at group level.
- Security policies can also be enforced at group level.

### Methods to List All Groups in Linux

- `cat /etc/group`
	- This file contains details about existing groups. 
	- group-name:group-password(x indicating that it's password is stored in /etc/shadow):group-ID:list-of-user-associated-to-that-group.
- `getent group`
	- getent stands for `get entries`, which is a linux commands to view contents of information files such as /etc/group, /etc/passwd and /etc/shadow.