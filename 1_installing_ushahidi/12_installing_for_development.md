## 1.2 Installing for development

### 1.2.1 Installing the API

#### 1.2.1.1 Getting the API code

First, you will need a copy of the source code, which lives in our Github repository:

```
git clone https://github.com/ushahidi/platform.git
```

**Note**: if you're getting set up for development, you might want to [fork the repository](https://github.com/ushahidi/docs.ushahidi.com/blob/gh-pages/install/developer-guide/adding-code.html) first.

Once you have the code, the next step is to prepare a web server.

#### 1.2.1.2 Prerequisites

* [Vagrant](http://www.vagrantup.com/)\*
* [VirtualBox](https://www.virtualbox.org/wiki/VirtualBox)\*
* [Composer](https://getcomposer.org/)
* PHP &gt;= 5.6

\*_Windows users\_may be required to \_Enable VT-X \(Intel Virtualization Technology\) in the computer's bios settings, disable Hyper-V on program and features page in the \_control_ panel, and install the VirtualBox Extension Pack \(installation instructions [_here_](https://www.youtube.com/watch?v=mwKmxxRbvws)_\)_

#### 1.2.1.3 Installing

First up we need to install the PHP dependencies

```
cd platform
composer install
```

If you get an error about "The requested PHP extension ... is missing from your system" you might need to run\_composer install --ignore-platform-reqs\_instead. You generally won't need all the PHP extensions on your host machine as they're installed in the vagrant box instead.

Then you can bring up the vagrant server and provision it:

```
vagrant up && vagrant provision
```

Our vagrant box is built on [Laravel's Homestead](https://laravel.com/docs/5.4/homestead#per-project-installation), a pre-packaged Vagrant box that provides you with a pre-built development environment. Homestead includes the Nginx web server, PHP 7.1, MySQL, Postgres, Redis, Memcached, Node, and all of the other goodies you might need.

_If you see errors about "Vagrant was unable to mount VirtualBox shared folders...", try upgrading VirtualBox or edit Homestead.yaml and change the folders to NFS as shown below, then re-run "vagrant" up._

```
      -
          map: "./"
          to: /vagrant
          type: "nfs"
      -
          map: "./"
          to: /home/vagrant/Code/platform-api
          type: "nfs"
```

At this point you should have a running web server but your deployment isn't set up yet. We still need to configure the database and run migrations.

```
cp .env.example .env
composer migrate
```

Go to [192.168.33.110](http://192.168.33.110/) to check the API is up and running. You should see some JSON with an API version, endpoints and user info.

### 1.2.2 Installing the client

#### 1.2.2.1 Getting the client code

First, you will need a copy of the source code, which lives in our Github repository:

```
git clone https://github.com/ushahidi/platform-client.git
```

The latest install instructions for the client are always in the README. If you have any trouble check those instructions first.

#### 1.2.2.2 Client dependencies

First you'll need nodejs or io.js installed, npm takes care of the rest of our dependencies.

* nodejs &gt;= v4.0

#### 1.2.2.3 Install, build and run a local dev server

1. Clone the repo

   ```
   git clone https://github.com/ushahidi/platform-client.git
   ```

   **Note**: if you're getting set up for development, you might want to [fork the repository](https://github.com/ushahidi/docs.ushahidi.com/blob/gh-pages/install/developer-guide/adding-code.html) first.

2. Navigate to project root

   ```
   cd platform-client
   ```

3. Install Build Requirements
   ```
   npm install -g gulp
   ```
4. Install Packages
   ```
   npm install
   ```
5. Set up build options. Create a`.env`file, you'll need to point`BACKEND_URL` at an instance of the [platform api](https://github.com/ushahidi/platform) \(If you  followed the vagrant instructions above that'll be:[ http://192.168.33.110](http://192.168.33.110/)\)

   ```
   BACKEND_URL=http://192.168.33.110
   ```

6. Run gulp

   ```
   gulp
   ```

7. You should now have a local development server running on [http://localhost:3000/](http://localhost:3000/)

### 1.2.3 Logging in the first time

The default install creates a user **admin** with password **admin**. Once logged in this user can create further user accounts or give others admin permissions too.
