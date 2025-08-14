    # Today I Learned...

A collection of concepts and things that I learn day to day across various technologies.

***27*** TILs and counting...

## Categories

* [Git](#Git)
* [Linux](#Linux)
* [Groups](#Groups)
* [Permissions](#Permissions)
* [Users](#Users)
* [Obsidian](#Obsidian)
* [Package Managers](#Package-Managers)
* [Python](#Python)
* [QEMU](#QEMU)
* [Yocto](#Yocto)

## TILs

### Git

- [Adding Submodules to Repository](git/adding-submodules-to-repository.md)
- [Setup Git Credential Helper](git/setup-git-credential-helper.md)
- [Remove Submodule from Repository](git/remove-submodule-from-repository.md)
- [Undo Commits - Git Reset](git/undo-commits-git-reset.md)

### Linux

- [Configuring Sudoers](linux/configuring-sudoers.md)
- [Text Insertion into File via HereDoc Input Stream](linux/text-insertion-into-file-via-heredoc-input-stream.md)

### Groups
- [Add a New Group](linux/groups/add-a-new-group.md)
- [Add a New Group with Specific Group ID](linux/groups/add-a-new-group-specific-group-id.md)
- [Change the Group ID](linux/groups/change-the-group-id.md)
- [Delete a Group](linux/groups/delete-a-group.md)
- [Rename a Group](linux/groups/rename-a-group.md)
- [Method to List All Groups](linux/groups/method-to-list-all-groups.md)
- [Add a User to a Group](linux/groups/add-a-user-to-a-group.md)

### Permissions
- [Linux File Permissions](linux/permissions/linux-file-permissions.md)

### Users
- [Add a New User](linux/users/add-a-new-user.md)

### Obsidian

- [Automatic Vault Sync Across Devices via Github](obsidian/automatic-vault-sync-across-devices-via-github.md)

### Package-Managers

#### APT

- [Adding PPA to APT](package-managers/apt/adding-ppa-to-apt.md)
- [PPA - Personal Package Archive](package-managers/apt/ppa-personal-package-archive.md)

### Python

- [Creating a Virtual Environment](python/creating-a-virtual-environment.md)

### QEMU

- [Virtual Machine Configuration](qemu/runqemu-virtual-machine-configuration.md)

### Yocto

#### BitBake

- [Adding a SystemD service into a Image Using a Recipe](yocto/bitbake-recipes/adding-a-systemd-service-into-a-image-using-a-recipe.md)
- [Creating a Recipe for PIP Packages](yocto/bitbake-recipes/creating-a-recipe-for-pip-packages.md)
- [Patching Source of a Recipe Using Devtool](yocto/bitbake-recipes/patching-source-of-a-recipe-using-devtool.md)
- [Modifying Root Password of your Image](yocto/bitbake-recipes/modifying-root-password-of-your-image.md)
- [Add New User to your Image](yocto/bitbake-recipes/add-new-user-to-your-image.md)
- [Adding a Network Manager Configuration for Autoconnect to WLAN](yocto/bitbake-recipes/adding-a-networkmanager-config-for-autoconnect-to-wlan.md)
- [Add Bash Configuration to Image](yocto/bitbake-recipes/add-bashrc-config-to-image.md)
## Usage

The `.vimrc` file for this project contains a function `CountTILs` that can
be invoked with `<leader>ct` (Default leader key is set to `\`). This will do a substitution count of the
current number of TILs and display the result in the command tray.

## About

I swiped this idea from [meganesu/til](https://github.com/meganesu/TIL).

## Other TIL Collections

* [jbranchaud/til](https://github.com/jbranchaud/til).
* [jwworth/til](https://github.com/jwworth/til).


## License

This repository is licensed under the MIT license. See `LICENSE` for
details.