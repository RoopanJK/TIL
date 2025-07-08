# Configuring Sudoers

- The default `/etc/sudoers` file might get overwritten during system upgrades, but custom files in `sudoers.d` directory.
- The Linux processes the configuration files that are present in `/etc/sudoers.d` in numeric and alphabetical order. To avoid conflicts add number to filenames by controlling the processing order.
- The basic syntax for sudoers is
```
	*username* ALL=(ALL:ALL) ALL
```
	- *username* host=(root-ownership:group-ownership) commands
- Create a new file inside the `/etc/sudoers.d` directory. (use numbers in filenames to avoid conflicts)
```
	sudo visudo -f /etc/sudoers.d/*file-name*
```
- Add the required configuration w.r.t to the basic syntax mentioned above.