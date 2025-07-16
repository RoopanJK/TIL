# Add a [Network Manager](https://networkmanager.dev/docs/api/latest/) Config for Autoconnect to WLAN

- Create a new recipe named `config-networkmanager_1.0-0.bb`.
- Create a new directory named files in the recipe folder which will contain the `.nmconnection` configuration file.
- The below step is OPTIONAL as the `.nmconnection` files can only be accessed by root user.
	- Create a hashed psk for your network you would like to connect.
		- Install wpasupplicant
		```
		sudo apt install wpasupplicant
		```
		- Create a encrypted psk using `wpa_passphrase`
		```
		wpa_passphrase SSID password
		```
		- This will generate a hashed psk that we will use in the `.nmconnection` configuration file.
- Now to create a new configuration file use the nmcli command. (Manually creating these files are also possible, but not advised as any type errors will lead to undefined behaviours)
- 
	```
	sudo nmcli connection add con-name *connection-name* type wifi ssid *SSID* wifi-sec.key-mgmt wpa-psk wifi-sec.psk *encrypted-psk-here*
	```
- This will create a new `.mmconnection` file in `/etc/networkmanager/system-connections`
- You can test if this works by using 
	```
	sudo nmcli con up *connection-name* 
	```
- Now we can either copy the file or create our own file and place it in the files directory of the recipe folder. 
- (Note: Lookout for the permissions while moving this file and placing it in your image. As improper permissions will result in NetworkManager ignoring the file.)
---
- Recipe file is as below
```
SUMMARY = "Network manager configuration to autoconnect to WLAN"

DESCRIPTION = "Place the required configuration file for network manager to autoconnect to saved networks"

LICENSE = "MIT"

SRC_URI = " \
file://*connection-name*.nmconnection
"

S = "${WORKDIR}"

RDEPENDS:${PN} = "networkmanager wpa-supplicant"
  
do_install(){

install -d ${D}/${sysconfdir}/NetworkManager/system-connections

install -m 600 ${S}/*connection-name*.nmconnection ${D}/${sysconfdir}/NetworkManager/system-connections

}
```