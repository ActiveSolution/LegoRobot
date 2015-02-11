H�r �r koden som k�rs p� Raspberry PI

Koden �r avsedd att ligga i '/home/pi/lego_robot' och startas av anv�ndaren 'pi' med kodens katalog som aktuell katalog. Typ:
cd /home/pi/lego_robot
su pi
node ./start_lego_robot

Koden kan autostartas genom att l�gga till f�ljande i /etc/rc.local
	(cd /home/pi/lego_robot;sudo -u pi ./start_lego_robot) &

Scriptet 'start_lego_robot' v�ntar p� att f� en wlan-koppling, loggar lite statusinformation och startar d�refter tv� node-skript.
'receiveLegoMsg.js' tar emot kommandon fr�n en SignalR-hub och styr robotens motorer d�refter.
'heartbeat.js' skickar varje minut statusinformation till Azure

Scriptet beh�ver ha exekveringsr�ttigheter satta (sudo chmod 755 start_lego_robot).
Loggning sker till filen 'lego_robot.log'.

F�r att fungera beh�ver node vara installerat p� Raspberry PI:n.
	wget http://node-arm.herokuapp.com/node_latest_armhf.deb
	sudo dpkg -i node_latest_armhf.deb
samt n�gra node-moduler
	npm install config
	npm install azure
	npm install ffi
	npm install signalr-client

D�rut�ver beh�vs kod f�r BrickPI. Den skaffas via Dexter industries.
