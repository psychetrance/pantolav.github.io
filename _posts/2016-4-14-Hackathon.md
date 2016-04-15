---
layout: post
title: Voter Notification Web App
permalink: /hackathon/
---

#### Keeping voters informed
While the Philippines is often referred to as the "Social Networking Capital of the World”, not all Filipino voters may have internet access, keeping them out of the loop. However, Filipinos are also known for their frequent use of mobile phones. This app takes advantage of this fact. 
The following are the intended purposes  to targets of the web application:

 - **Campaign managers** can use it to spread news about various events they have planned to voters who live near the event area.
This can also function as an advisory as these kinds of events often mean some roads may be blocked 
 - Inform **voters** about various events that take place a few months before the election (Debates, speeches, motorcades, etc.)

Deploying this app requires (two?) services from Bluemix, Twilio and Postgresql.

#### Downloading the application for deployment
 1. Create a new folder named `v-notif`. 
 2. Download [myapp.war] and save or move it to the `v-notif` folder.

#### Create a Twilio account
1. Go to [Twilio's website](https://www.twilio.com) and click the `Sign Up` button on the upper right

2.  Fill the registration up, and choose the following options in the drop down list

	||||
	|---|---|---|
	| **What are you building?** | SMS Alerts|
	| **Choose your language** | Java |
	| **Which product do you plan to use first?** | Programmable SMS |
	
	<br>
4. Click `Get Started`

5. Before you can proceed to using Twilio's services, Twilio has to verify one phone number from you, choose `Philippines` (area code +63) and in the textbox, the rest of your phone number (ex. 9xxxxxxxxx)

6. You will be redirected to a page with a textbox. Once you receive the verification code in your phone, enter it in the text box and proceed.

8. On the current page, click `Get your first Twilio Number` and click `Choose this number`. Take note of your new number and click `Done`.

9.  In order for the Twilio service in Bluemix to work, it requires your Twilio account's `Auth Token` and `Account SID` both which can be found [here](https://www.twilio.com/user/account) by clicking `Show API Credentials`. Take note of both of these credentials, you will be using this when binding Twilio to your Bluemix app.

#### Setting Twilio up
Before you are able to send text messages through the app, there are some things you need to set up since Free users have some limitations.

1. To be able to send to Philippine numbers, you have to enable it [here](https://www.twilio.com/user/account/settings/international/sms).

2. If you intend to send messages to phone numbers besides the one you registered when you created your account, you can verify them by going [here](https://www.twilio.com/user/account/phone-numbers/verified) and clicking `Verify a Number`.

> **Note:** Paid accounts do not have to verify numbers, but for the demonstration of this application, we will be using a free account which will need to do so.


#### Deploying the application

> This part will be assuming that the user already has a Bluemix account and already has the necessary terminal commands installed.

1. Open a terminal window (Command Prompt for Windows machines) and change the directory to the `v-notif` folder.
2. Log into your Bluemix account through the `cf login` command:
````
cf login -a https://api.ng.bluemix.net -s dev
````
3. Upload `myapp.war` to your Bluemix account with the command:
````
cf push <app name> -m 512M -p myapp.war 
````
**Example**
````
cf push hackathon-gitgit-aw -m 512M -p myapp.war
````
4. Go to the Bluemix website and log into your account.
5. Upon logging in, navigate to your account’s dashboard by clicking `DASHBOARD` on the upper right if logging in did not already redirect you to it.

	> Since you have already uploaded the application to Bluemix, its widget should be present on your dashboard

6.  Click the application widget to view its overview.
7. Click `ADD A SERVICE OR API`, this will redirect you to the service catalog.

#### Adding Services: Twilio
1. In the Catalog page look for the `Twilio` service and click it.
2. Rename the Service name to `Twilio - <your_name>` .
3. Enter your Twilio account's `Auth Token` and `Account SID` in their respective fields
4. Click `Create`

#### Adding Services: Postgresql

 1. Click on your application widget and click on `ADD A SERVICE OR API` again
 2. Scroll down to the bottom of the Catalog page and click on the `Bluemix Labs Catalog` link
 3. Search for the `postgresql` service and click.
 4.  (Optional) Change the service name according to your liking
 5.  Click `Create` 
