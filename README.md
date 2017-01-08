[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=Y2JHAQRU77CCE)

===========
Bash Script to allow create or delete nginx virtual hosts on linux in a quick way.

## Installation ##

1. Download the script
2. Apply permission to execute:

```
$ chmod +x /path/to/ng
```

### For Global Shortcut ###

```bash
$ cd /usr/local/bin && sudo wget -O ng https://raw.githubusercontent.com/patrickcurl/ngTool/master/ng && sudo chmod +x /usr/local/bin/ng
```

## Config ##
Open and edit the file as sudoer, change the owner, group, and restart variables as needed.

## Usage ##

Basic command line syntax:

```bash
$ sudo ng [create | delete] [domain] [/full/path/to/project/dir]
```

### Examples ###

to create a new virtual host:

```bash
$ sudo ng create mysite.dev /home/patrick/projects/laravel/mysite/public
```
to delete a virtual host

```bash
$ sudo ng delete mysite.dev
```

## License ##
MIT : Basically do whatever just provide copyright notice w/ all derivatives. 