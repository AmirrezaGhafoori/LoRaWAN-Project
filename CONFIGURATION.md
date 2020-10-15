Firstly we have to configure our Raspberry pi SBC to become a gateway and register it on TTN platform as our network server. 

1- Install raspbian and git on the raspberry pi 
2- config the correct time and locale of your region --> this can be done by commands bellow : 
	1- sudo dpkg-reconfigure locales
	2- sudo dpkg-reconfigure tzdata

3- Create new user for TTN and add it to sudoer:
	1- sudo adduser ttn
	2- sudo adduser ttn sudo 
	3- sudo visudo --> add the following line to the end of this file:
		ttn ALL=(ALL) NOPASSWD: ALL
		
		this will eliminate the password requirement for this user
		*** doing this step is optional ***
4- Login and logout as ttn and remove the default pi user:
	sudo userdel -rf pi 

5- Configure the wifi credentials:
	1- sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
	2- add your network information to this file as following template:
		network ={
			ssid="YOUR WIFI SSID"
			psk="YOUR WIFI PASS"
		}

6- Clone the following package from github:
	  1- git clone -b spi https://github.com/ttn-zh/ic880a-gateway.git ~/ic8	     80a-gateway
	  2- cd ~/ic880a-gateway
	  3- sudo ./install.sh spi

7- After this step you have to register your gateway on TTN (the instruction is available on internet) 


