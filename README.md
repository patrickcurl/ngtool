Support Me by going to my Etsy store : http://myjarofhope.etsy.com
===========
Bash Script to allow create or delete nginx virtual hosts on linux in a quick way.

## Installation ##

```shell
$ mkdir ~/bin && cd ~/bin 
$ git clone  https://github.com/patrickcurl/ngtool
$ cd ngtool && chmod +x ng
$ sudo ln -s /home/username/bin/ngtool/ng /usr/local/bin/ng
```

Alternately you can add the ngtool directory to your $PATH, it just needs to be in a folder that's in the $PATH. 

I also recommend adding an alias to ~/.bash_rc or ~/.bash_aliases : alias ng="sudo ng"

The script requires being run as sudo, or else you can't modify nginx files - this way it'll do so by default, and you 
still need to enter a password.

## Caveat Emptor on .dev domains and HSTS ## 

'.dev' domains are blocked from browsers now because  of HSTS (blame google), I highly recommend only using '.test'. 

On my system what I've done is enabled a global dns wildcard using dnsmasq, this makes it so all .test domains are local and need no editing. 

I'm on ARCH linux so YMMV, but to do this I added a file named test.tld in /etc/NetworkManager/dnsmasq.d with the following contents:

```
local=/test/
address=/test/127.0.0.1
listen-address=127.0.0.1
```

Then run: 
```shell
$ sudo systemctl restart NetworkManager
$ ping anything.test
```

You'll need to wait for the Network Manager to start back up in a few seconds before running the ping, but any domain should now resolve locally without editing hosts file.

Now you can edit the useHosts config in the NG tool to false as you won't need to edit hosts.
 

## Config ##
```bash
### CONFIG SETTINGS
# Put owner/group that nginx must run under for your system.
# The default on ubuntu would be user: www-data group: www-data.
# This is my personal settings for Arch linux.

#owner for chowing -- this is the owner nginx uses.
owner=patrick 

#group for chowing -- this is the group nginx uses.
group=users 

#sites-enabled path
sitesEnabled='/etc/nginx/sites-enabled/' 

#sites-available path
sitesAvailable='/etc/nginx/sites-available/' 

#make true if you do not have a global .test wildcard setup via dnsmasq or other.
useHosts=false 

#whether to use, setup and regenerate self-signed wildcard ssl. 
useSSL=true 

# SSL Settings only matter if useSSL is true.
sslConfig='/etc/nginx/ssl/ssl_servers.cfg'
sslKey='/etc/nginx/ssl/nginx.key'
sslCert='/etc/nginx/ssl/nginx.crt'

# Change this to match what your system uses.
#arch
restart='systemctl restart nginx'

#ubuntu
# restart=service nginx restart

### END CONFIG SETTINGS
```

## Usage ##

Basic command line syntax:

```bash
$ ng [create | delete | enable | disable] [domain] [/full/path/to/project/dir]
```

### Examples ###

To create a new virtual host:

```bash
$ ng create mysite.test /home/patrick/projects/laravel/mysite/public
```
To delete a virtual host

```bash
$ ng delete mysite.dev
```

To enable ALL virtual hosts: 

```bash
$ ng enable
```

To enable a single virtual host:

```bash
$ ng enable vhost.test
```
To disable all hosts: 

```bash
$ ng disable all
```

To disable a single host: 

```bash
$ ng disable vhost.test
```

## License ##
MIT : Basically do whatever just provide copyright notice w/ all derivatives. 
