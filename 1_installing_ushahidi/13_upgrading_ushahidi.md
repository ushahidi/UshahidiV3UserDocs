## 1.3 Upgrading Ushahidi {#1-5-upgrading-ushahidi}

### 1.3.1 Updating your deployment to the latest version {#1-5-1-updating-the-client}

1. Make a backup copy of the current folder where you have installed the Ushahidi Platform.

2. Make a backup copy of your database.  
   1. The exact procedure to do this depends on your environment.

3. Download the latest .tar.gz file from our [github releases page](https://github.com/ushahidi/platform-release/releases). Please note that pre-releases are not considered stable and you may find issues with them.

4. Uncompress the downloaded file on the same location where the Ushahidi Platform is currently installed.
5. If you had made any changes to .htaccess files, application config files or similar after installation, restore those from your backup copy.
6. Re-run some of the installation steps \(refer to the [installation guide](/1_installing_ushahidi/README.md) for more detailed instructions\). In particular, re-run these two steps
7. 1. Running database migrations
   2. Ensuring that log, cache and media/uploads under platform/application are owned by the proper user

### 1.3.2 Updating the client \(for developers\) {#1-5-2-updating-the-api}

From your local repository fetch the latest code and run \`npm install\` to update your modules:

```
git pull
```

```
npm install
```

```
gulp build
```

The updated version should load when you reload your browser.

### 1.3.3 Updating the API {#1-5-2-updating-the-api}

From your local repository fetch the latest code and run `bin/update` or `bin/update --production` if you are running on a production environment:

`git pull`

`bin/update`

OR

`bin/update --production`
