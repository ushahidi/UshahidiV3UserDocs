## 1.1 Installing on Heroku {#1-1-installing-on-heroku}

Deploying on [Heroku](https://www.heroku.com/) is good way to test out the platform quickly. Its also a viable option for running a production deployment (though this could be expensive depending on your traffic needs).

*   First deploy the API with the [latest release](https://heroku.com/deploy?template=https://github.com/ushahidi/platform/tree/release) or the [latest development code](https://heroku.com/deploy?template=https://github.com/ushahidi/platform/tree/master). If you haven&#039;t used heroku before, you&#039;ll be asked to sign up. Pick an App name for your deployment (or let heroku pick one for you), then hit Deploy for free. You will need to wait while it deploys.

Confirm your deployment went ok by clicking &quot;View&quot;. You should see a block of JSON something like:

Take note of the URL of the created app (ie: [https://afternoon-castle-5024.herokuapp.com/)](https://afternoon-castle-5024.herokuapp.com/)

*   Deploy the client with the [latest release](https://heroku.com/deploy?template=https://github.com/ushahidi/platform-client/tree/release) or the [latest development code](https://heroku.com/deploy?template=https://github.com/ushahidi/platform-client/tree/master). Make sure you use the same version as you did for the API. Again, Pick an _App name_ for your deployment. Set _Backend URL_ to the URL of the API app you just created (ie: [https://afternoon-castle-5024.herokuapp.com/](https://afternoon-castle-5024.herokuapp.com/))

***_Important: make sure you don&#039;t include the trailing slash_

Leave other config as-is, and hit **_Deploy for free_**. You may need to wait (the client takes much longer to deploy). When it&#039;s finished, click **_View_** and check out your new deployment.

*   Log in to your new deployment. By default there is a single user, username: admin &amp; password: admin
*   Configure scheduled jobs.

In order to make use of features such as twitter, email data sources and notifications you would need to add and configure the [Heroku Scheduler](https://elements.heroku.com/addons/scheduler) add-on to your Heroku application.

Once it&#039;s added, you will need to configure 4 jobs in it, running with your desired frequency (10 minutes at most):

*   *   **_bin/ushahidi dataprovider incoming_**
    *   **_bin/ushahidi dataprovider outgoing_**
    *   **_bin/ushahidi savedsearch_**
    *   **_bin/ushahidi notification queue_**

You will be able to see the output of these jobs in the heroku logs window for your app.