![](favicon.png)
# toy-http
[![Build Status](https://travis-ci.org/lukas-h/toy-http.svg?branch=master)](https://travis-ci.org/lukas-h/toy-http)  
lightweight embeddable http service,
providing static site hosting.  
Zero dependency alternative to node's `http-server`  
designed for unix-like platforms
For more advanced usage you can set three arguments:  
1. Port (numeric)  
2. Max. Connections at once (numeric)  
3. Source directory (path)  
example: `toy-http 8080 /var/www 30`

## features
- support for GET and HEAD requests  
- stable error and interruption management  
- embeddable as one small C function  
- scalable and easy to modify  
- blocking function for parental folders of the serve folder  
- plainness: less than 400 lines of source code  
- no dependencies to external libraries, just the C standard libraries and  
 the posix API (preinstalled on all good unix-derivates) and socket api (included)  
  
I wrote toy-http to test the http protocol and not to make a project
for serious usage. It is now at the point to be a small alternative to
other servers that offer static hosting.
The server is ideal for hosting the current folder to test websites, aso.

## platforms
Because of the dependencies to the BSD-Socket API and the Posix programming interface,
toy-http is only available for unix platforms like:
- linux  
- FreeBSD, NetBSD, OpenBSD and other BSD derivates  
- GNU Hurd  
- MacOSx  
- Solaris (maybe)  
- and more  
  
Windows is supported with CygWin (or something similar)

## embed it!
You can embed it into your applications, simply add `service.h` and `service.c` to your project  
and use this function: ` int serve(int http_port, int max_connections, char *serve_directory);`.  
`max_connections` is the maximum number of clients that can be connected at once.  
`serve_directory` is the folder with the ressources and files that are hosted.  

hint: for embedding, it could be useful to modificate the signal handlers
and exit functions.

## files
`toy-http.c` <- the main file for the standalone server  
`install` and `Makefile` <- scripts to build the standalone server  
`index.html` <- a html file for testing    
`service.c` and `service.h` <- the library files

## licensing
This project is licensed under the GNU LGPL v3 or later (the library)  
and the standalone server under GNU AGPL v3 or later.
Copyright (C) 2015, 2016 Lukas Himsel
