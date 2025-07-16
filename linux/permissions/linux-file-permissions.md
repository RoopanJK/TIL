# Linux File Permissions:

- The permission of the files can be listed using the `ls-l` command. This command results with the following output.

```
-rwxrwxr-x 1 user-owner group-owner   302 Jun 27 11:11 file.txt
```

- The first element of the expression represents the file type.

| Character |      Meaning      |
| :-------: | :---------------: |
|    `-`    |   Regular file    |
|    `d`    |     Directory     |
|    `l`    |   Symbolic link   |
|    `c`    | Character device  |
|    `b`    |   Block device    |
|    `s`    |      Socket       |
|    `p`    | Named pipe (FIFO) |

- The Linux file permissions are usually represented in the expression of three different sets of permissions:

| Position | Characters |           Meaning           |
| :------: | :--------: | :-------------------------: |
|    1     |    `d`     | File type (`d` = directory) |
|   2–4    |   `rwx`    |  User (owner) permissions   |
|   5–7    |   `r-x`    |      Group permissions      |
|   8–10   |   `r-x`    | Others (world) permissions  |
- These permissions are also represented in `octal` representation for a more compact way of expressing file permission.
- These permissions have a value:
	- r = 4
	- w = 2
	- x = 1
- Adding them up will result in the permission required.
 - Example: `rwxr-xr-x` → `755`.

|  Role  | Symbolic Permissions | Value Calculation | Octal Value |
| :----: | :------------------: | :---------------: | :---------: |
|  User  |        `rwx`         |     4 + 2 + 1     |      7      |
| Group  |        `r-x`         |     4 + 0 + 1     |      5      |
| Others |        `r-x`         |     4 + 0 + 1     |      5      |
|        |                      |                   |   **755**   |
- A leading 0 such as `0755` also represents the same. But the leading 0 is used to indicate many programming languages that it is a octal number.