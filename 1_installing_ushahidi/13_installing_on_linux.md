## 1.3 Installing on Linux {#1-3-installing-on-linux}

### 1.3.1 Installing the API {#1-3-1-installing-the-api}

#### Getting the API code {#getting-the-api-code}

First, you will need a copy of the source code, which lives in our Github repository:

_git clone_[](https://github.com/ushahidi/platform.git)[_https://github.com/ushahidi/platform.git_](https://github.com/ushahidi/platform.git)Once you have the code, the next step is to prepare a web server.

#### System Requirements {#system-requirements}

To install the platform on your computer/server, the target system must meet the following requirements:

*   [PHP](http://php.net/) version 5.4.0 or greater
    *   The following php extensions enabled: curl, gd, imap, json, mcrypt, mysqlnd (optional)
*   Composer
*   [MySQL](http://mysql.com/) database version 5.5 or greater (PostgreSQL support planned)
*   [Apache](http://apache.org/) 2.2+ or nginx

**NB: These instructions are written specifically for Debian Linux or a derivative of it (_Ubuntu_, _Mint_, etc). You may have to adjust some things if you are using a different flavour of linux.**

#### 

#### Set up the database {#set-up-the-database}

To create a database

*   First login to MySQL as root.

_mysql -u root -p_

Using the _`-p`_ is only required when your MySQL configuration requires it.

You may need to use the _`-h`_ option to specify _`localhost`_ or _`127.0.0.1`_ if you are unable to connect.

*   Next, create a new user and database for Ushahidi. The username and database can be anything; we will use `ushahidi`for both in this example:

_CREATE DATABASE ushahidi_db; GRANT ALL ON ushahidi_db.* to ushahidi_user@localhost IDENTIFIED BY &#039;ushahidi-db-password&#039;;_

_quit;_

*   Now create a _.env_ config file in the base of repository. Make sure that the database, username, and password match the database you just created.

_DB_HOST=localhostDB_NAME=ushahidi_dbDB_TYPE=MySQLiDB_USER=ushahidi_userDB_PASS=ushahidi-db-password_

#### Set up URL Rewrites {#set-up-url-rewrites}

Rename `httpdocs/template.htaccess` to `httpdocs/.htaccess` (for Apache) to enable rewriting of all non-existent files to `index.php`.

If you are unable to enable rewriting, then you&#039;ll need to customize the init settings.

*   Copy the `application/config/init.php` file into `application/config/environments/development/` (create this directory if it doesn&#039;t exist).
*   Edit init.php and set `index_file` to `&quot;index.php&quot;` to include index.php in your URLs

**_AN IMPORTANT NOTE ON URLS, DOCROOTS AND BASE_URL_**

Typically, the Ushahidi platform backend is run **under a separate virtual host / domain name. It&#039;s important to understand that this is a different domain name, from the one you will use to access the website with your browser.** We will refer to this URL as &quot;backend URL&quot; throughout this document.

You would configure the domain name for this URL with the `_ServerName_` directive (for Apache), or the `_server_name_` (for nginx). Be sure to make `_platform/httpdocs_/` the `_DocumentRoot_` (for Apache) or `_root_` (for nginx) setting in your virtual host.

If you are running Ushahidi via http://localhost/ then the `_base_url_` will be http://localhost/platform/httpdocs/

#### Enable writing to the logs, cache, and upload directories {#enable-writing-to-the-logs-cache-and-upload-directories}

The webserver will need write access to logs, cache and upload directories. To do this run:

_% chmod 0777 application/logs application/cache application/media/uploads_

OR

_% chown www-data 0777 application/logs application/cache application/media/uploads_

It&#039;s generally better to use `chown` to set the owner of the directories to the user the web server runs as, rather than making them globally writable.

### 1.3.2 Installing dependencies {#1-3-2-installing-dependencies}

We use [Composer](https://getcomposer.org/) to manage server side dependencies. Once you have installed composer, you can run the update script with:

_bin/update_

**_Whenever the repository is updated using_ git pull_, run the update script to ensure that your installation stays updated!_**

If you are updating a production deployment, you will want to avoid installing developer dependencies (testing tools, etc) by using the &quot;deploy&quot; option:

_bin/update --production_

### 1.3.3 Testing: Did it work? {#1-3-3-testing-did-it-work}

In order to test your platform backend, you can do a quick test with your browser.

Assuming that your backend url is &quot;http://myapi.example.com&quot;, you would open the following address with your browser: &quot;http://myapi.example.com/api/v3/config&quot; . As a result you should see a JSON document starting similarly to this:

{ &quot;count&quot;: 3, &quot;results&quot;: [ { &quot;id&quot;: &quot;features&quot;, &quot;url&quot;: &quot;http://myapi.example.com/api/v3/config/features&quot;, &quot;views&quot;: { &quot;map&quot;: true, &quot;list&quot;: true, &quot;chart&quot;: true, &quot;Data&quot;: true, &quot;activity&quot;: true, &quot;plan&quot;: false }…

You would of course change &quot;myapi.example.com&quot; with the specific backend URL domain you chose during configuration.

### 1.3.4 Extra: Customizing configuration {#1-3-4-extra-customizing-configuration}

Base config files are in **_application/config/_**.

You can add per-environment config overrides in `application/config/environments/`. The environment is switched based on the `KOHANA_ENV` environment variable.

### 1.3.5 Installing the client {#1-3-5-installing-the-client}

#### Getting the client code {#getting-the-client-code}

First, you will need a copy of the source code, which lives in our Github repository:

_% git clone_[ _https://github.com/ushahidi/platform-client.git_](https://github.com/ushahidi/platform-client.git)

#### Client dependencies {#client-dependencies}

First you&#039;ll need nodejs or io.js installed, npm takes care of the rest of our dependencies.

*   nodejs v6
    *   We recommend using NodeJS builds from [NodeSource](https://github.com/nodesource/distributions) or using NVM
*   Build tools for building native addons from npm:
    *   Debian users install the `build-essential` package
    *   Fedora users install `gcc-c++` and `make`
*   nginx or apache2

#### Building the client {#building-the-client}

*   Clone the repo

_git clone_[](https://github.com/ushahidi/platform-client.git)[_https://github.com/ushahidi/platform-client.git_](https://github.com/ushahidi/platform-client.git)

**_Note: if you&#039;re getting set up for development, you might want to_ **[**_fork the repository_**](https://github.com/ushahidi/docs.ushahidi.com/blob/gh-pages/install/developer-guide/adding-code.html)** _first._**

*   Navigate to project root

_cd platform-client_

*   Install Build Requirements

_npm install -g gulp_

*   Install Packages

_npm install_

**_This will install both NPM and Bower dependencies! No separate `bower install` command is required._**

*   Set up build options. Create a `.env` file, you&#039;ll need to point BACKEND_URL at an instance of the platform api

_BACKEND_URL=_[_http://myapi.server/_](http://myapi.server/)

*   Run gulp

_gulp build_

You should now have a client build in server/www.

### 1.3.6 Configure nginx or apache {#1-3-6-configure-nginx-or-apache}

*   Nginx:
    *   Copy the virtual host config from server/nginx-site.conf into your nginx conf dir (/etc/nginx or /etc/nginx/sites-enabled)
    *   Edit the config:
        *   Set server_name to whatever domain you plan to use
        *   Replace root /var/www with the path to server/www ie. platform-client/server/www
    *   Include the config in your nginx.conf (usually located in /etc/nginx.conf) by adding the following include /etc/nginx/ushahidi-site.conf
    *   Restart nginx
    *   Load the new vhost in a browser
*   Apache2:
    *   Copy server/rewrite.htaccess to server/www/.htaccess
    *   Create a new apache vhost and point the docroot at server/www
    *   Restart apache
    *   Load the new vhost in a browser

### 1.3.7 Logging in the first time {#1-3-7-logging-in-the-first-time}

The default install creates a user admin with password admin. Once logged in this user can create further user accounts or give others admin permissions too.