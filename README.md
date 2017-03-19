sslmerge
===============

[![bash_logotype](doc/bash_logotype.png)](https://www.gnu.org/software/bash/)

__**sslmerge**__ is a GPLv3 tool to help create the correct chain of SSL certificates delivered.

  - simple to use
  - does not send the certificates to the outside (running locally)

### Version

Latest stable: **v1.1d**  
[![Build Status](https://travis-ci.org/zurawsky/sslmerge.svg?branch=master)](https://travis-ci.org/zurawsky/sslmerge)  
Devel branch: **next-release**  
[![Build Status](https://travis-ci.org/zurawsky/sslmerge.svg?branch=next-release)](https://travis-ci.org/zurawsky/sslmerge)  

### Usage

Examples of ways to use:

```
  Usage:
    sslmerge [option|long-option]

  Examples:
    sslmerge --help
    sslmerge --version
    sslmerge --in Root.crt --in Intermediate1.crt --in Server.crt --out nginx_bundle.crt
    sslmerge --in /tmp/certs/ --out /tmp/nginx_bundle.crt

  Options:
    -h, --help                  show this message
    -v, --version               show script version
    -d, --debug                 display information on the screen (debug mode)
    -i, --in                    add certificates to merge (multiple files or directory)
    -o, --out                   saves the result (chain) to file
```

### Requirements

  - openssl package

### Todos

  - add better error handling mechanism
  - in the case of detecting different certificate .crt it must be converted to this format
  - adding a mechanism for informing the format of the certificate

### Problems

See on the *Issues* page.

### Project architecture

    |-- sslmerge               	# main file (init)
    |-- CHANGELOG.md            # notable changes for each version of a project
    |-- LICENSE.md              # GNU GENERAL PUBLIC LICENSE, Version 3, 29 June 2007
    |-- README.md               # this simple documentation
    |-- _config.yml             # jekyll’s configuration file
    |-- .gitignore              # ignore untracked files e.g. log/ directory
    |-- .travis.yml             # travis-ci configuration for project
    |-- src                     # includes external project files
        |-- _import_            # functions, variables and all other attached files to the script
    |-- doc                     # includes documentation, images and manuals
        |-- bash_logotype.png   # bash logo (added to README.md)

### License

GPLv3 : <http://www.gnu.org/licenses/>

**Free software, Yeah!**
