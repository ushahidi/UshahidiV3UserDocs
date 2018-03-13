## 3.4 Data Sources {#3-4-data-sources}

There are many ways to enter posts into your Ushahidi deployment other than from the deployment itself. This section shows you how to configure all the possible data source types.

**_NB: If you’re a user on ushahidi.com, the number of data source types available to you may be limited, based on the Ushahidi plan you are subscribed to. You may review these from_ **[**_our plans page_**](https://www.ushahidi.com/plans)**_. For open source/self hosted deployments, all data source types are available to you_**

To access the data sources configuration page,

*   On the left hand menu bar, click on **_Settings_**

*   Then, click on **_Data Sources_**.

![Data_Source_Settings.png](../assets/datasource_settings.png)

*   You should get a full list of data sources as shown below

### 3.4.1 Email {#3-4-1-email}

This section allows you to set up the platform to receive emails from user. Before getting started, make sure that you have an email account set up on Gmail, Yahoo or any other service provider. Make sure that you have IMAP/POP enabled (For more information on these two protocols, [visit this website](http://www.pop2imap.com/). Instructions on how to enable the IMAP/POP settings in your email can be found here

*   [Gmail](https://support.google.com/mail/troubleshooter/1668960?hl=en)
*   [Yahoo](https://help.yahoo.com/kb/SLN3697.html)

To get started with email set up,

*   Click on **_the drop down icon on the right as shown_**
*   Input the following email account settings:-
    *   **_Incoming server type_**: You have two options to select from, **_POP_** and **_IMAP_**. We recommend using IMAP if possible because it’s the best way to make sure you can see all your mail at any time on all of your devices
    *   **_Incoming server_**: Enter the address of the server where your email services are hosted. E.g _mail.yourwebsite.com_, _imap.gmail.com_ or _pop.gmail.com_
    *   **_Incoming server port_**: Enter the port that your email account uses for incoming emails. This is also provided by your service provider and depends on the use of [SSL(Secure Sockets Layer)](https://www.digicert.com/ssl.htm)/[Transport Layer Security(TLS)](https://en.wikipedia.org/wiki/Transport_Layer_Security) or not. As a standard rule;
        *   IMAP uses port 143 , but SSL/TLS encrypted IMAP uses port 993 .
        *   POP uses port 110 , but SSL/TLS encrypted POP uses port 995
    *   **_Incoming server security_**: You have 3 options to choose from to enhance secure connection to your email mailbox, depending on which is supported by your email service provider.
        *   None
        *   TLS - [Read more on Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security)
        *   SSL - [Read more on Secure Sockets Layer](https://www.digicert.com/ssl.htm)
    *   **_Incoming user name_**: Enter the email address you want to use to receive emails e.g **_sample@youremail.com_**. We recommend setting up a separate email address for this purpose, preferably one that has lot of available space to avoid the account getting full in a short time, especially if the platform will be receiving a lot of submission via email.
    *   **_Incoming password_**: Enter the password of the email account inserted above.
    *   **_Outgoing server type_**: Select one of the three options presented to you:-
        *   SMTP: Simple Mail Transfer Protocol (SMTP) is recommended for use with the ushahidi platform.
        *   Sendmail
        *   Native
    *   **_Outgoing server_**: Enter the address of the server from which emails are sent out. This is also provided by the email service provider
    *   **_Outgoing server port_**: Enter the port your email service provider uses for outgoing emails. The default port tends to be 25, but SMTP with SSL support uses port 465 or 587
    *   **_Outgoing server security_**: Select one of the three options provided to you
        *   None
        *   SSL
        *   TLS, which is recommended by the service provider for outgoing server security.
    *   **_Outgoing user name_**: Enter the email address you want to use to send emails. E.g **_sample@youremail.com_**
    *   **_Outgoing password_**: Enter the password of the email account inserted above.
    *   **_Email sender name_**: This is what appears in the “from” field in outgoing emails.
*   Click on **_Save_ **and this data source’s settings will be saved. Unstructured posts from email will now be pulled into the platform.
*   To enable/disable the email data source, simply click on the green toggle.

*   If you’d like to edit your email configuration, simply click on the drop down icon on the right while on the data sources list page****and make your changes.

### 3.4.2 FrontlineSMS {PENDING} {#3-4-2-frontlinesms-pending}

### 3.4.3 Nexmo {#3-4-3-nexmo}

Nexmo is a cloud-based SMS API that lets you send and receive a high volume of messages to mobile phones in any country at wholesale rates.

**_NB: You need a nexmo account to be able to configure this as a data source. To sign up, go to_ **[**_https://dashboard.nexmo.com/sign-up_**](https://dashboard.nexmo.com/sign-up)

To get started with Nexmo set up,

*   Log into your Nexmo Dashboard [https://dashboard.nexmo.com](https://dashboard.nexmo.com)
*   If you haven’t already, you’ll need buy a number that you will use to receive SMS messages from.
    *   Click on Numbers on the top menu bar on your nexmo dashboard

*   *   Click on Buy Numbers

*   *   Set the desired criteria of the phone number you’re looking to use

*   *   *   Select the country in which the SMS Number will likely be operating in
        *   Select the features of this phone number(SMS only, Voice only or SMS &amp; Voice)
        *   Select the type of phone number it will be (Mobile, Landline, Toll free)
    *   Click on** _Search_**. A list of available numbers based on the criteria set above will appear.
    *   Click **_Buy_** on the number you’d like to use.
*   Once you have a phone number, note it down as you’ll need it to configure your data source later on.
*   You’ll need to grab your API credentials from your nexmo settings page.

*   Pick your _API KEY_ and _API SECRET_ from the **_API Settings_** section.

*   Go back to your Data source settings page on your deployment
*   Click on **_the drop down icon on the right to get to your Nexmo configuration page_**

****

*   Enter the following details, which you got earlier from your Nexmo Dashboard
    *   **_From_**: Enter the phone number you will use to receive SMS messages from your nexmo account
    *   **_Secret_**: Enter a secret value for security purposes.
    *   **_API KEY_**: Enter the API key retrieved from your nexmo settings page.
    *   **_API SECRET_**: Enter the API secret retrieved from your nexmo settings page.
*   Click on **_Save_ **and this data source’s settings will be saved. Unstructured posts from SMS will now be pulled into the platform from Nexmo.

*   To enable/disable the nexmo data source, simply click on the green toggle.

![Toggle_Nexmo.png](../assets/togglenexmo.png)

*   If you’d like to edit your nexmo configuration, simply click on the drop down icon on the right while on the data sources list page****and make your changes.

### 3.4.4 SMSSync {#3-4-4-smssync}

SMSsync is a simple, yet powerful SMS to HTTP sync utility that turns any Android phone into a local SMS gateway by sending incoming messages (SMS) to a configured URL (web service).

To get started with SMSSync set up,

*   Click on **_the drop down icon on the right as shown_**

**_![SMSSync.png](../assets/smssync.png)_**

*   Follow the instructions given to you below.
    *   Download the application from the Android Market by scanning the QR Code presented to you on the settings page or simply search for it in the android market.

_Please note that SMSsync works on any SMS-enabled device running Android 2.1 and above._

*   *   Retrieve the **_Sync URL_**, which you’ll need to configure SMSSync with under **_Step 2: ANDROID APP SETTINGS_**
    *   You can also set an SMSSync secret key for security purposes
    *   Click on **_Save_**
*   Open up the SMSSync Application on your android device. You’ll note that you can manage multiple Sync URLs on the app.
*   To add a new Sync URL
    *   Tap on the Sync URL from the navigation drawer.
    *   Tap on the Add icon icon on the actionbar. An input dialog should open.
    *   Enter a title for the Sync URL.
    *   Enter a secret key(If you set one above). Make sure you enter the exact key here.
    *   The secret key should be presented as string of any characters without spaces.
    *   Enter a comma separated value for the keyword(s). These keywords will be used by SMSsync to filter incoming SMS and pending messages to the Sync URL you are adding. As of v2.0.2\. You can now add Regular Expression code for filtering. This means, it can either be CSV or RegExp. It cannot be both.
    *   Enter the URL for your web service. Don&#039;t forget to start with the HTTP or HTTPS protocol. e.g. [https://example.com/api-v1/add-record/](https://example.com/api-v1/add-record/)
    *   Tap OK to save the new entry.

_Note: Version 2.5 or higher supports_[ _basic auth_](http://en.wikipedia.org/wiki/Basic_access_authentication) _credentials in the URL, e.g. https://username:pass@example.com/api-v1/add-record/._

*   You will now need to start the SMSSync Service to start forwarding messages to the platform. To start the SMSSync service
    *   Make sure that you have added and enabled(checked) the Sync URL you added above.
    *   On the SYNC URL screen, tap on the Start SMSsync service to start the service. You only do this if the service is disabled.
*   You should be all set to work with SMSSync and Ushahidi now. Unstructured posts via SMS will now be pulled into the platform.
*   To enable/disable the SMSSync data source, simply click on the green toggle.

*   If you’d like to edit your SMSSync configuration, simply click on the drop down icon on the right while on the data sources list page****and make your changes.

For more details on how to manage messages within SMSSync, see [configuration instructions on the SMSSync Website](http://smssync.ushahidi.com/configure/)

### 

###  {#-0}

### 3.4.5 Twilio {#3-4-5-twilio}

Twilio allows you to programmatically make and receive phone calls and send and receive text messages using its web service APIs.

**_NB: You need a Twilio account to be able to configure this as a data source. To sign up, go to_ **[**_https://www.twilio.com/try-twilio_**](https://www.twilio.com/try-twilio)

To get started with Twilio set up,

*   Log into your twilio account.
*   You’ll need to buy a number to use. Click on **_PHONE NUMBERS._**

****

*   Click on **_Buy a number_**

****

*   Select the desired criteria for your phone number
    *   Country
    *   Location/Number
    *   Capabilities (Voice, SMS, MMS)
*   Click on** _Search_**. A list of available numbers based on the criteria set above will appear.
*   Click **_Buy_** on the number you’d like to use.

*   Once you have a phone number, note it down as you’ll need it to configure your data source later on.
*   You’ll need to grab your API credentials from your Twilio Account settings page.

*   Pick your _ACCOUNT SID_ and _AUTH TOKEN_ from the **_API Credentials_** section.

*   Go back to your Data source settings page on your deployment
*   Click on **_the drop down icon on the right as shown_**

**_![Twilio.png](../assets/twilio.png)_**

*   Enter the following details, which you got earlier from your Twilio Account
    *   **_From_**: Enter the phone number you will use to receive SMS messages from your twilio account
    *   **_ACCOUNT SID_**: Enter the unique ID of your twilio account
    *   **_AUTH TOKEN_**: Enter the Auth Token retrieved from your twilio settings page.
    *   **_SMS Auto Response_**: This will likely be the message sent back to users who send you SMS Messages.
*   Click on **_Save_ **and this data source’s settings will be saved. Unstructured posts from SMS will now be pulled into the platform from Twilio.

*   To enable/disable the Twilio data source, simply click on the green toggle.

*   If you’d like to edit your Twilio configuration, simply click on the drop down icon on the right while on the data sources list page****and make your changes.

### 3.4.6 Twitter {#3-4-6-twitter}

This section allows you to configure twitter as a data source, and subsequently pull unstructured posts from specific twitter hashtags.

For you to be able to pull tweets based on hashtags, you will need to set up your ushahidi deployment as an application on twitter. To get started,

*   Click on **_the drop down icon on the right as shown_**
*   Click on Create a new twitter application. This will redirect you to [https://apps.twitter.com](https://apps.twitter.com)
*   Sign into [https://apps.twitter.com](https://dev.twitter.com) using your twitter username and password
*   Click on “Create New App”

**_![Twitter.png](../assets/twitter.png)_**

![Screen_Shot_2016-04-14_at_12_40_12_PM.png](../assets/screenshot_2016_-04-14at_12_40_12.png)

*   Fill in the application details
    *   Name – this can be your deployment/site name e.g Uchaguzi
    *   Description – this is your deployment/site description – what your deployment does
    *   Website – this is your deployment url/link i.e http://yourdeployment
    *   Callback url – Leave this blank.
    *   Agree to the terms and conditions then click on **_Create your twitter_ **application

*   Once your application has been successfully created, you should now be able to access your access keys and tokens. To do so, click on **_Keys and Access Tokens_** or **_Manage Keys and Access_**
*   You’ll get redirected to a page where you can grab details needed to configure your Ushahidi deployment i.e **_CONSUMER KEY_**, **_CONSUMER SECRET_**, **_ACCESS TOKEN_**, **_ACCESS TOKEN SECRET_**.
*   You’ll have to generate an **_ACCESS TOKEN_** and **_ACCESS TOKEN SECRET_** by clicking on **_Generate my access token and token secret._ **This may take a couple of minutes, and your page will refresh with all the details you require.
*   Go back to your twitter configuration page on your deployment and fill in all the details from your twitter app management page.
*   Add the hashtags you want to pull tweets from in the “Twitter Search Terms” section. You can choose more than one hashtag, separated by a comma. It is recommended that short and clear hashtags be chosen.
*   Click on **_Save_ **and this data source’s settings will be saved. Unstructured posts from twitter will now get pulled into the platform.

*   To enable/disable the twitter data source, simply click on the green toggle.
*   If you’d like to edit your twitter configuration, simply click on the drop down icon on the right while on the data sources list page****and make your changes.

![Edit_Twitter.png](../assets/edittwitter.png)