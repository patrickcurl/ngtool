NgTool
This is modified from: 
https://github.com/RoverWire/virtualhost
===========

Bash Script to allow create or delete apache/nginx virtual hosts on Ubuntu on a quick way.

## Installation ##

1. Download the script
2. Apply permission to execute:

```
$ chmod +x /path/to/virtualhost.sh
```

3. Optional: if you want to use the script globally, then you need to copy the file to your /usr/local/bin directory, is better
if you copy it without the .sh extension:

```bash
$ sudo cp /path/to/virtualhost.sh /usr/local/bin/virtualhost
```

### For Global Shortcut ###

```bash
$ cd /usr/local/bin && sudo wget -O ng https://raw.githubusercontent.com/patrickcurl/ngTool/master/ng && sudo chmod +x /usr/local/bin/ng
```

## Usage ##

Basic command line syntax:

```bash
$ sudo sh /path/to/virtualhost.sh [create | delete] [domain] [optional host_dir]
$ sudo ng [create | delete] [domain] [/full/path/to/project/dir]
```

### Examples ###

to create a new virtual host:

```bash
$ sudo ng create mysite.dev /home/patrick/projects/laravel/myapp/public
```
to delete a virtual host

```bash
$ sudo ng delete mysite.dev
```

to delete a virtual host with custom directory name:

```
$ sudo virtualhost delete anothersite.dev my_dir
```
### Localization

For Apache:

```bash
$ sudo cp /path/to/locale/<language>/virtualhost.mo /usr/share/locale/<language>/LC_MESSAGES/
```

For NGINX:

```bash
$ sudo cp /path/to/locale/<language>/virtualhost-nginx.mo /usr/share/locale/<language>/LC_MESSAGES/
```
