## 1.4 Connecting to Ushahidi Mobile App {#1-6-connecting-to-ushahidi-mobile-app}

### 1.4.1 Configure your deployment to support the mobile app {#1-6-1-configure-your-deployment-to-support-the-mobile-app}

First, it is necessary to edit the file config.json

`{`

`client_id: "ushahidiui",`

`client_secret: "35e7f0bca957836d05ca0492211b0ac707671261",`

`backend_url: "",`

`google_analytics_id: "",`

`intercom_app_id: "", mapbox_api_key: "",`

`raven_url: ""`

`}`

The following are the required settings to allow for mobile app support:

* **client\_id:** this is the oauth client id that allows the mobile app to identify itself to your deployment’s API instance. If you have not explicitly changed it then the default value is ‘ushahidiui’
* **client\_secret:** this is the oauth client secret, the second property that the mobile client uses to identify itself to the API instance. If you have not explicitly changed it then the default value is ‘35e7f0bca957836d05ca0492211b0ac707671261’
* **backend\_url:** this should be set to the uri of the location of your API instance. For example, if your client is hosted at _‘name.domain.com’_ and your API is hosted at _‘name.api.domain.com’_, then the value for this field should be _‘name.api.domain.com’_

Optional properties:

* **google\_analytics\_id:** if you have a Google Analytics account and you wish for the Mobile App to log information to it then you should specify your google analytics id here.
* **intercom\_app\_id:** if you have an Intercom account and you wish to provide intercom support for your users then you can specify your Intercom app id here.
* **mapbox\_api\_key:** if you wish to use your own map box key, it can be set here
* **raven\_url:** if you are using Sentry and wish to have the mobile app send any issues to your Sentry account then you can set the appropriate raven url here.

### 1.4.2 CORS headers {#1-6-2-test-your-deployment-to-with-the-mobile-app}

It's necessary to configure your web server to serve the config.json file along with a series of HTTP headers. Here are the headers:

`Access-Control-Allow-Origin: *  
Access-Control-Allow-Methods: GET, POST, OPTIONS  
Access-Control-Allow-Headers: DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Content-Range,Range  
Access-Control-Expose-Headers: DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Content-Range,Range`

The exact way to accomplish this depends on the specific kind of web server that you are using.

### 1.4.3 Test your deployment to with the mobile app {#1-6-2-test-your-deployment-to-with-the-mobile-app}

* Download the Ushahidi Mobile app for [Android](https://play.google.com/store/apps/details?id=com.ushahidi.mobile&hl=en) or [iOS](https://itunes.apple.com/us/app/ushahidi-mobile/id1205994516?ls=1&mt=8)
* Follow the App steps to setup access to your deployment



