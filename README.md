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

Composer
======
You can add a composer command to the host based on the composer docker container:
`sudo vim /usr/local/bin/composer`
 
```
#!/bin/sh
export PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin
echo "Current working directory: '"$(pwd)"'"
docker run --rm -v $(pwd):/app -v ~/.ssh:/root/.ssh composer/composer $@
```
`sudo chmod +x /usr/local/bin/composer`

`composer --version`

Documented here: https://hub.docker.com/r/composer/composer/

Bower, grunt, etc. etc
======
You can add composer commands for bower, grunt, node, npm, etc, to the host based on the composer docker container:
``` 
wget -nv -O ~/bin/bower https://raw.githubusercontent.com/mkenney/docker-npm/alpine/bin/bower && chmod 0755 ~/bin/bower
wget -nv -O ~/bin/grunt https://raw.githubusercontent.com/mkenney/docker-npm/alpine/bin/grunt && chmod 0755 ~/bin/grunt
wget -nv -O ~/bin/gulp https://raw.githubusercontent.com/mkenney/docker-npm/alpine/bin/gulp && chmod 0755 ~/bin/gulp
wget -nv -O ~/bin/node https://raw.githubusercontent.com/mkenney/docker-npm/alpine/bin/node && chmod 0755 ~/bin/node
wget -nv -O ~/bin/npm https://raw.githubusercontent.com/mkenney/docker-npm/alpine/bin/npm && chmod 0755 ~/bin/npm
```
Documented here: https://hub.docker.com/r/mkenney/npm/