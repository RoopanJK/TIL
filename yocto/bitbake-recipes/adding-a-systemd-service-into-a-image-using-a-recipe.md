
# Adding a SystemD Service into a Image Using a Recipe

- Create a new recipe named `startup-script_1.0-0.bb`.
- Create a new directory named `files` in the recipe folder which will contain the shell script and systemD service file.
- Copy your sh file into the files directory.
- Create a new sytemd service file with your required configuration.
- Example systemd service file below.

```
[Unit]
Description=startup service

[Service]
ExecStart=/bin/bash /usr/bin/startup.sh

[Install]
WantedBy=multi-user.target
```

---

- Recipe file is as below.

```
SUMMARY = "A Example of a recipe that installs a systemd service"

DESCRIPTION = "Runs startup.sh script using a systemd service"

  

LICENSE = "CLOSED"

  

SRC_URI = " \

file://startup.sh \

file://startup.service \

"

  
# Inherit SystemD bbclass to 
inherit systemd

  
# Set source directory
S = "${WORKDIR}"

  
# Require Bash
RDEPENDS:${PN} = "bash"

  
# Add service files to the systemd variable
SYSTEMD_SERVICE:${PN} = "startup.service"
# Set to enable to auto-enable the service
SYSTEMD_AUTO_ENABLE:{PN} = "enable"

  

do_install(){
# Create a `/usr/bin` directory in target if not present already. 
install -d ${D}${bindir}
# Install the file in the `bindir` with the below permission.
install -m 0755 ${S}/startup.sh ${D}${bindir}

  
# Create the systemd directory for service files in target. if not present 
# already.
install -d ${D}/${sysconfdir}/systemd/system
# Install the service file the directory with the below permission.
install -m 0644 ${S}/startup.service ${D}/${sysconfdir}/systemd/system

}
```

- After installing the recipe use journalctl to check the status of your service.
```
journalctl -u service-name.service
```