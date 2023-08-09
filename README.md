FireFlyIII-Stack

Minimal Firefly III + Data Importer & Cronjobs docker-compose file

#First time startup

Edit the .env file inside the root directory.
You only need to fill in these variables on first boot.

1. APP_KEY #32 long random string
2. STATIC_CRON_TOKEN #32 long random string
3. AUTO_IMPORT_SECRET #16 long random string

Once you have confirmed Firefly III is working proceed to next step.

1. Add every bank account to firefly III you plan on using with nordigen and set starting balance FROM the date you plan on pulling data off.
3. Create Your Access Token for your Data Importer by opening FireFly III -> "Options/Profile/OAuth/Personal Access Tokens" Create new Access token and add the string to your .env file FIREFLY_III_ACCESS_TOKEN
5. Create account on Nordigen and go to "Projects/User Secrets" and click Create New. Add these to .env file. ID to NORDIGEN_ID and key to NORDIGEN_KEY

Restart your docker-compose with these new changes.

1. Open up your data importer in browser http://server_ip_here:20002 it should show you the callback url
2. Add the Callback url to your Firefly III "Options/Profile/OAuth/OAuth Clients" and uncheck Confidential checkbox
3. Go back to data importer and follow the instructions. I would suggeds importing everything
4. Once you have your first successful import Start over and then import data from last 7 days. Before you exit the page click Download configuration file. Place this configuration file under $DATA/data_importer/ directory.
5. You're all set. You need to renew the import every 3 months or so. Click Import from nordigen and upload the config file you used earlier. This way you don't need to write everything every time you need to renew your access.

You can edit the firefly-cron file if you want to import data and run the automatic cronjob in different time. My bank usually updates the balance around 6am so it's set to import at 6am.
