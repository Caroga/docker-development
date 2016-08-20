Using this stack means just having a easy development environment.
Nothing fancy or special, just a combination of the official containers with some custom configuration.

How to
======
* Launch the stack by using: `docker-compose up -d`
* Make your project checkouts in the `www` folder. 
  * Nginx will look for a `web` folder inside your project, e.g.: `www/default/web`.
* Nginx will accept requests on `<foldername>.local.dev` where `<foldername>` is the name of your www folder.
  * E.g.: `www/default/web/index.php` => `http://default.local.dev/index.php`
* Either add a host entry pointing towards your project (e.g.: `172.17.0.1	default.local.dev`) or add the dnsmasq server at `172.0.0.1` as a dns resolver.
  * The dnsmasq server uses wildcard dns resolving meaning that every checkout automatically will be accessible from your host computer.
* If you wish to add custom dns entries inside dnsmasq you can do so by browsing here: `http://localhost:8082`

Bower, grunt, etc. etc
=======
https://hub.docker.com/r/mkenney/npm/