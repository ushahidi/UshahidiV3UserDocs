## Technical Specifications {#technical-specifications}

**Better development stack**

Ushahidi 3.x is built on a modern PHP stack: dependencies are managed with composer, we’re using Kohana 3 but phasing that out, and we’ve isolated the core logic of the platform standalone Entity and Usecase classes.

The user interface of Ushahidi 3.x is now a separate app (the client) built purely in JS, HTML + CSS using AngularJS and a collection of other libraries. Again this uses a modern stack, with a build pipeline using gulp and browserify.

**What’s new (and improved)?**

*   Dependencies are properly managed and easier to update or replace needed.
*   We’re using our own API to build the app, it gets first class support.
*   You can work on just the UI without delving into the API code
*   Modern libraries mean they’re still being supported, we don’t have the burden of supporting legacy libraries ourselves.

**Code is easier to customize**

*   It’s more structured making it easier to find what you want
*   It doesn’t repeat itself so a change can be made in one place, not need to be copied everywhere else
*   UI is isolated to the client, allowing work on just the UI without having to delve into the API code

**The stack**

*   Back-end: [Linux](http://en.wikipedia.org/wiki/Linux), [PHP](https://php.net/), [Apache](http://httpd.apache.org/)/[Nginx](http://wiki.nginx.org/Main), [MySQL](http://www.mysql.com/) or PostgreSQL
*   Front-end: [AngularJS](https://angularjs.org/), [Javascript](http://en.wikipedia.org/wiki/JavaScript), [Html](http://en.wikipedia.org/wiki/HTML), [CSS](http://en.wikipedia.org/wiki/Cascading_Style_Sheets). Built with [NodeJS](http://nodejs.org/) and [Browserify](http://browserify.org/). Using [Leaflet](http://leafletjs.com/) for mapping, and a collection of other frontend libraries