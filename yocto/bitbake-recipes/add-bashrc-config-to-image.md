# Add Bash - .bashrc shell configuration

- In order to add a .bashrc file to you user's root directory. Use the below recipe.
- Create the required `.bashrc` file inside your `files` directory of you recipe.

- **.bashrc**
```
# Append to path

export PATH=/usr/sbin:$PATH

# Add additional required commands.
```
- We would also required a `.profile` that sources the `.bashrc`, as this file will be sourced when bash is invoked as a Interactive shell. Check `INVOCATION` section in bash [man page](https://www.man7.org/linux/man-pages/man1/bash.1.html#top_of_page).

- **.profile**
```
# Source Bash

if [ -f ~/.bashrc ]; then

. ~/.bashrc

fi
```

- **Recipe**
```
SUMMARY = "Bash configuration"

DESCRIPTION = "Installs the required configuration file .bashrc for bash shell"

  

LICENSE = "CLOSED"

  

SRC_URI = " \

file://.bashrc \

file://.profile \

"

  

S = "${WORKDIR}"

  

RDEPENDS:${PN} = "bash"

  

do_install(){

install -d ${D}/home/*username*

install -m 644 ${S}/.bashrc ${D}/home/*username*

install -m 644 ${S}/.profile ${D}/home/*username*

}

  

FILES:${PN} += "/home/*username*"
```

- Set the file permissions appropriately.