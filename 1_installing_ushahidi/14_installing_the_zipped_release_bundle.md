## 1.4 Installing the zipped release bundle {#1-4-installing-the-zipped-release-bundle}

The zipped release bundle are pre-built compressed files for you, which don&#039;t require further building or downloading. These files bundles are available from the platform-release repository in Github. The files are named ushahidi-platform-release-vX.Y.Z.tar.gz .

The installation procedure will vary depending on your setup, but the requirements in all cases are

*   A web server supporting PHP
    *   This can be apache2, nginx or a hosting provider
*   PHP invokable from command line
*   The following PHP modules installed:
    *   curl, json, mcrypt, mysqli, pdo, pdo_mysql, imap and gd
*   A MySQL database server

These instructions assume that you know how to create a database in your MySQL server and obtain user credentials with access to such database.

The instructions and example commands are written specifically for Debian Linux or a derivative of it (Ubuntu, Mint, etc). You may have to adjust some things if you are installing on a different flavour of Linux, or a different OS.

### 1.4.1 Apache 2 with mod_php {#1-4-1-apache-2-with-mod-php}

*   Ensure _mod_rewrite_ is installed and enabled in your apache server.
*   Copy into your document root the contents of the _html/_ folder after unzipping the ushahidi-platform-release-vX.Y.Z.tar.gz bundle file.
*   The **dist/** folder contains the suggested configurations for the virtual host (_apache-vhost.conf_). The configs are quite default, you just need to ensure that there is an AllowOverride directive set to _All_ for your document root (where the app has been unzipped).
*   Create a _platform/.env_ file with your database credentials, such as:

_DB_HOST=&lt;address of your MySQL server&gt;_

_DB_NAME=&lt;name of the database in your server&gt;_

_DB_USER=&lt;user to connect to the database&gt;_

_DB_PASS=&lt;password to connect to the database&gt;_

_DB_TYPE=MySQLi_

*   Run the database migrations, execute this command from the _platform_ folder:

_./bin/phinx migrate -c application/phinx.php_

*   Ensure that the folders _logs_, _cache_ and _media/uploads_ under _platform/application_ are all owned by the user that the web server is running as.
    *   i.e. in Debian derived Linux distributions, this user is **_www-data_**, belonging to group **_www-data_**, so you would run:

**_chown -R www-data:www-data platform/application/{logs,cache,media/uploads}_**

*   Set up the cron jobs for tasks like receiving reports and sending e-mail messages.
    *   You&#039;ll need to know again which user your web server is running as. We&#039;ll assume the Debian standard _www-data_ here.
    *   Run the command crontab -u www-data -e and ensure the following lines are present in the crontab:

MAILTO=&lt;your email address for system alerts&gt;

*/5 * * * * cd &lt;your document root&gt;/platform &amp;&amp; ./bin/ushahidi dataprovider outgoing &gt;&gt; /dev/null

*/5 * * * * cd &lt;your document root&gt;/platform &amp;&amp; ./bin/ushahidi dataprovider incoming &gt;&gt; /dev/null

*/5 * * * * cd &lt;your document root&gt;/platform &amp;&amp; ./bin/ushahidi savedsearch &gt;&gt; /dev/null

*/5 * * * * cd &lt;your document root&gt;/platform &amp;&amp; ./bin/ushahidi notification queue &gt;&gt; /dev/null

*   Restart your apache web server and access your virtual host. You should see your website and be able to login with the credentials user name _admin_ and password _admin_
*   **Make sure to change the credentials. Specially if the website is exposed to be accessed by anyone other than you.**

### 1.4.2 Nginx with php-fpm {#1-4-2-nginx-with-php-fpm}

The procedure is pretty similar to the one detailed for apache above, with the following exceptions.

*   Step 1: _mod_rewrite_ is specific for Apache, in nginx the module is named _ngx_http_rewrite_module_. It&#039;s usually included and enabled.
*   Step 2: Instead of configuring Apache, you would need to configure nginx. For configuring nginx see the example _nginx-site.conf_ in the dist folder. You would usually drop this file in a place where it&#039;s included from the main configuration file. It assumes php-fpm is listening in port 9000 of localhost.
*   The default php-fpm configuration should work. Most importantly, you need to ensure the _listen_ directive matches the _fastcgi_pass directive_ in the nginx host configuration file.
*   Once you are done, restart both your nginx and php-fpm services.

### 1.4.3 Shared hosting (Cpanel, Dreamhost, Bluehost, etc) {#1-4-3-shared-hosting-cpanel-dreamhost-bluehost-etc}

In general, the instructions for apache can be taken as a guideline. Each shared hosting provider comes with their own set of particularities, so we can only provide general directions here. In all cases, you&#039;ll need to ensure that:

*   Decompress the release file and place the contents of the _html_ folder in the webroot of your shared hosting domain or subdomain.
*   Create a database for your website and write the access details in the _.env_ file (as per step 4 of Apache 2 instructions)
*   You have command line access (SSH) in order to run the _phinx_ database migration utility in step 5 of Apache 2 instrucions.
*   A URL rewriting mechanism has to be in place so that
    *   Requests to _/platform/api/v3/*_ are to be forwarded to the _index.php_ script inside/platform/httpdocs.
    *   When invoking that script, the _api/v3/*_ part of the url should be passed to the script into the a _$_SERVER_ or environment variable.
    *   If your host uses Apache and supports _.htaccess_ files, most of this should be taken care of for you.