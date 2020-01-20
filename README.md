# ecobee-manager
Barebones script app to track ecobee sensor temperatures, and control tp-link switches (ex. to turn heaters on)

It will log the temperatures and the actions it does to sensors:

1/18/2020, 11:10:03 AM
	EcoHouse: Overall temp: 22.0℃, 29%
		 - Downstairs: 22.0℃[*]
		 - Basement Room: 24.6℃[*]
		 - Sunroom: 10.7℃
	[deviceAction] SunroomHeater turning ON (temp=10.7)

You need to create a .env file with the logins to your ecobee web login, and if controlling sensors, also to your TP-Link Cloud account, and finally to send emails you need to give a login to a gmail account.

.env FILE:
API_KEY=(api key from ecobee developer portal)
SMTP_LOGIN=(ex. gmail login)
SMTP_PASS=(ex. gmail pass)
SETTINGS_FILE=/user.dat
LOG_FILE=/info.log
TPLINK_USER=(tplink cloud account)
TPLINK_PASS=

Finally, you should set a cron-tab to run the script on a regular interval:
/etc/crontab
*/10 *  * * *   ecobee  cd /home/ecobee && node ecobee.js
