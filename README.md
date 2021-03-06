# Integrating SmartThings App with Xooa
This document will provide step-by-step tutorial to integrate a smartApp with Xooa.
The objective is to make entries for each event of a device into the hyperledger blockchain and retrieve it.

The repository in use for this example is <https://github.com/Xooa/smartThings-xooa>.

## Xooa Setup
1. Go to Xooa dashboard located at <https://xooa.com/blockchain/apps>
2. Login to the platform. If you dont have an account, you can click on **Sign Up** to create a new account. Once logged in, you will be taken to the main Xooa dashboard.
3. From the main dashboard, click on **Deploy New** on top left corner to start the deployment process.
4. The first step is to connect your new Xooa login to your Github account. In the main dashboard you should see the **Connect to Git** option. Click it and in the new browser window that opens up, allow Xooa to access your github account. Select the Github account you hold in which you have smartThings-xooa repository.
5. Enter **App Name** and **Description** for the app. These fields are for you to identify a particular app from list so make sure your values are relevant to the app you are deploying. Click **Next**.
6. Select **Private** and search for **smartThings-xooa**. A list of repositories matching the search criteria are shown below. In our case, **smartThings-xooa** will show up. Click **Select** and then, click **Next**.
7. The next step is deployment details. Select **master** as the branch and **smartThings-xooa** as the chaincode from the dropdown available. Click **Deploy**.
8. Sit back and relax while Xooa sets up the backend. Once *Xooa* is finished with the process you will see Success for all the process listed on screen.
9. You will be redirected to app dashboard once the deployment is complete.
10. Take note of **App ID** from the dashboard under `Basic Information` tab. It will be required later to connect the **smartApp**.
11. From the app dashboard, navigate to **Identities** tab.
12. For the identity available, click **Show API token** and copy the token value. We will be using this for authorizing the API requests. This will be your `API Token` needed to authorize **smartApp**.

___

## SmartApp Setup (Server)
1. Create a developer account or login with your existing account at <https://graph.api.smartthings.com>.
2. Go to **My SmartApps** tab from top menu, then `New SmartApp`.
3. Go to **From code** option. Now, let's get code to paste in this section.
4. Click on `blockchain-event-logger.groovy` file present in **smartThings-xooa** repository.
5. Click on **Raw**.
6. Copy all the code.
7. Paste it in the **From Code** section in your develepor portal of smartThings.
5. Click on **create**.
6. Click on **save**.
7. Click on **Publish -> For me**.

Alternative to steps 3-7, to setup via Github integration,
1. Click on **Enable GitHub Integration**.
2. Click on **Authorize application**.
3. Click on **Next** button on the bottom left.
4. Click on Authorize SmartThingsCommunity.
5. Follow the instructions to fork the SmartThingsCommunity/SmartThingsPublic repository, and then click the Next button.
6. Go to **My SmartApps**.
7. Click on **Settings**.
8. Click on **Add new repository**.
9. Add the Github Repo to your IDE with the following settings:
	* Owner: arishtjain
	* Name: smartThings-xooa
	* Branch: master
10. Click on **Save**.
11. Click on **Update from Repo**.
12. Click on **smartThings-xooa (master)**.
13. Select **blockchain-event-logger.groovy** from **New(only in GitHub)** column.
14. Check **Publish**.
15. Click on **Execute Update**.

### SmartApp Configuration
1. Click on the smartApp you just deployed.
1. Click on **App Settings**.
2. Click on **Settings** option.
3. Enter app Id provided in dashboard of Xooa under `Basic Information` tab.
4. Enter the API Token provided in Xooa dashboard under `Identities` tab.
5. Click on **Update**.

The below document is currently for android devices (need to verify for iOS).
There are 2 apps available for smartThings in google play store . We recommend the classic app over new app due to frequent glitches in new app being faced currently.
## SmartApp Setup (Smartphone)
1. Make sure you have smartThings app installed on your phone with at least 1 location and 1 device defined.
2. Also make sure that you use same login ID to log into the app as used in developer account login.
3. Open your SmartThings app on your smartphone.

### SmartThings classic app (Preferred)
1. Tap on **automation** in the lower bar.
2. Tap on the SmartApps tab on top.
3. Tap on **Add a SmartApp**.
4. Scroll down to end and tap on **My Apps**.
5. You should find `Blockchain Event Logger` here. Tap it and proceed to setup.
6. Select which devices' data you want to log into the Xooa Blockchain.

### SmartThings new app
1. Tap on `automations` in lower bar.
2. Tap on `Add`.
3. If prompted, select The location you want to add the app to.
4. You should find `Blockchain Event Logger` at the very end of the page. It may take few seconds to show up. Tap it and continue to setup.
5. Select which devices' data you want to log into the Xooa Blockchain.
___

## Log some events
1. Take some actions with the smartThings devices you associated with the smartApp.
2. If they are simulated devices, then go to your smartThings app and tap your simulated devices to make some events.


## Accessing the past events
1. Go to <http://54.251.163.66/smartthings/>.
2. Enter your `App Id` and `API Token` provided in Xooa dashboard.
3. Click on **submit** and access all your previous events logged in the blockchain along with **timestamp**.

## Accessing the past events in SmartThings App

### SmartApp Setup (SmartThings IDE)
1. Login with your Samsung  SmartThings account to the SmartThings IDE at <https://graph.api.smartthings.com>.
2. Navigate to **My SmartApps** 
3. Now you will publish the app.  Steps depends if wish to use github integration or not.

**Not using github integration:**

* From top menu, select `New SmartApp`.
* Naviagte to **From code** tab. 
* Locate `blockchain-viewer.groovy` in **smartThings-xooa** github repo.
* Click or tap **Raw** 
* Select all and Copy the code
* Paste it in the **From Code** section in smartThings console, click or tap **create**, **save**, **Publish -> For me**.

**Using Github integration** (if you haven't already set it up here there is FAQ in the community https://community.smartthings.com/t/faq-github-integration-how-to-add-and-update-from-repositories/39046)
* Sill under Smartapps tab, Select  **Settings**.
* Select  **Add new repository**.
* Add the Github Repo to your IDE with the following settings:
	* Owner: arishtjain
	* Name: smartThings-xooa
	* Branch: master
* Click on **Save**.
* Click on **Update from Repo**.
* Click on **smartThings-xooa (master)**.
* Select **blockchain-viewer.groovy** from **New(only in GitHub)** column.
* Check the **Publish** checkbox
* Click on **Execute Update**.

### Accessing blockchain-viewer smartApp
#### SmartThings classic app (Preferred)
1. Tap on **automation** in the lower bar.
2. Tap on the SmartApps tab on top.
3. Tap on **Add a SmartApp**.
4. Scroll down to end and tap on **My Apps**.
5. You should find `Blockchain Viewer` here. Tap it.
6. Enter app Id provided in dashboard of Xooa under `Basic Information` tab.
7. Enter the API Token provided in Xooa dashboard under `Identities` tab.
8. Click **Next** to proceed to view devices logged with the blockchain.
9. Click on any device to view all the past logged events of that particular device.

#### SmartThings new app
1. Tap on `automations` in lower bar.
2. Tap on `Add`.
3. If prompted, select The location you want to add the app to.
4. You should find `Blockchain Viewer` at the very end of the page. It may take few seconds to show up. Tap it.
5. Enter app Id provided in dashboard of Xooa under `Basic Information` tab.
6. Enter the API Token provided in Xooa dashboard under `Identities` tab.
7. Click **Next** to proceed to view devices logged with the blockchain.
8. Click on any device to view all the past logged events of that particular device.