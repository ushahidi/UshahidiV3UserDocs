## 1.2 Installing for development {#1-2-installing-with-vagrant-a-nodejs-dev-server}

### 1.2.1 Installing the API {#1-2-1-installing-the-api}

#### Getting the API Code {#getting-the-api-code}

First, you will need a copy of the source code, which lives in our Github repository:

_git clone_[_https://github.com/ushahidi/platform.git_](https://github.com/ushahidi/platform.git)

_**Note: if you're getting set up for development, you might want to**_** **[_**fork the repository**_](https://github.com/ushahidi/docs.ushahidi.com/blob/gh-pages/install/developer-guide/adding-code.html)** **_**first. Once you have the code, the next step is to prepare a web server.**_

#### Prerequisites {#prerequisites}

* Vagrant
* Ruby

If you already use Vagrant, check the settings in the [Vagrantfile](http://docs.vagrantup.com/v2/vagrantfile/index.html) and make sure the IP address won't conflict with your existing VMs.

#### Preparing the Server {#preparing-the-server}

Before we run vagrant we need to get some puppet modules. We do this with librarian puppet:

_gem install puppet librarian-puppetlibrarian-puppet install_

You'll need to [get a github token](https://github.com/settings/tokens/new) then replace XXXX below with that token

Then you can bring up the vagrant server and provision it:

_export github\_token = "XXXX"vagrant up && vagrant provision_

This should set up a server, and install all the dependencies too.

Go to [192.168.33.110](http://192.168.33.110/) to check the API is up and running. You should see some JSON with an API version, endpoints and user info.

_The vagrant set up uses a 64 bit VM so you may need to enable 64 bit virtualization on your host machine._

### 1.2.2 Installing the client {#1-2-2-installing-the-client}

#### Getting the client code {#getting-the-client-code}

First, you will need a copy of the source code, which lives in our Github repository:

_git clone_[_https://github.com/ushahidi/platform-client.git_](https://github.com/ushahidi/platform-client.git)

README. If you have any trouble check those instructions first.

#### Client Dependencies {#client-dependencies}

First you'll need nodejs or io.js installed, npm takes care of the rest of our dependencies.

* nodejs v0.10 or v0.12 or io.js v1.2

#### Install, Build and run a local dev server {#install-build-and-run-a-local-dev-server}

* Clone the repo

_git clone_[_https://github.com/ushahidi/platform-client.git_](https://github.com/ushahidi/platform-client.git)

_**Note: if you're getting set up for development, you might want to**_** **[_**fork the repository**_](https://github.com/ushahidi/docs.ushahidi.com/blob/gh-pages/install/developer-guide/adding-code.html)** **_**first.**_

* Navigate to project root

_cd platform-client_

* Install Build Requirements

_npm install -g gulp_

* Install Packages

_npm install_

_**This will install both NPM and Bower dependencies! No separate**_** bower install **_**command is required.**_

* Set up build options. Create a .env file, you'll need to point BACKEND\_URL at an instance of the [platform api](https://github.com/ushahidi/platform) \(If you followed the vagrant instructions above that'll be: [http://192.168.33.110](http://192.168.33.110/)\)

_NODE\_SERVER=true_

_BACKEND\_URL=_[_http://192.168.33.110_](http://192.168.33.110/)

* Run gulp

_gulp_

* You should now have a local development server running on [http://localhost:8080](http://localhost:8080)

### 1.2.3 Logging in the first time {#1-2-3-logging-in-the-first-time}

The default install creates a user admin with password admin. Once logged in this user can create further user accounts or give others admin permissions too.

