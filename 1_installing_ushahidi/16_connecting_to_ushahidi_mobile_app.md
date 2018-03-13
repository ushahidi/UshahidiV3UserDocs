## 1.6 Connecting to Ushahidi Mobile App {#1-6-connecting-to-ushahidi-mobile-app}

### 1.6.1 Configure your deployment to support the mobile app {#1-6-1-configure-your-deployment-to-support-the-mobile-app}

First, it is necessary to edit the file config.json

{

client_id: &quot;ushahidiui&quot;,

client_secret: &quot;35e7f0bca957836d05ca0492211b0ac707671261&quot;,

backend_url: &quot;&quot;,

google_analytics_id: &quot;&quot;,

intercom_app_id: &quot;&quot;, mapbox_api_key: &quot;&quot;,

raven_url: &quot;&quot;

}

The following are the required settings to allow for mobile app support:

*   **client_id:** this is the oauth client id that allows the mobile app to identify itself to your deployment’s API instance. If you have not explicitly changed it then the default value is ‘ushahidiui’
*   **client_secret:** this is the oauth client secret, the second property that the mobile client uses to identify itself to the API instance. If you have not explicitly changed it then the default value is ‘35e7f0bca957836d05ca0492211b0ac707671261’
*   **backend_url:** this should be set to the uri of the location of your API instance. For example, if your client is hosted at _‘name.domain.com’_ and your API is hosted at _‘name.api.domain.com’_, then the value for this field should be _‘name.api.domain.com’_

Optional properties:

*   **google_analytics_id:** if you have a Google Analytics account and you wish for the Mobile App to log information to it then you should specify your google analytics id here.
*   **intercom_app_id:** if you have an Intercom account and you wish to provide intercom support for your users then you can specify your Intercom app id here.
*   **mapbox_api_key:** if you wish to use your own map box key, it can be set here
*   **raven_url:** if you are using Sentry and wish to have the mobile app send any issues to your Sentry account then you can set the appropriate raven url here.

### 1.6.2 Test your deployment to with the mobile app {#1-6-2-test-your-deployment-to-with-the-mobile-app}

*   Download the Ushahidi Mobile app for [Android](https://play.google.com/store/apps/details?id=com.ushahidi.mobile&hl=en) or [iOS](https://itunes.apple.com/us/app/ushahidi-mobile/id1205994516?ls=1&mt=8)
*   Follow the App steps to setup access to your deployment