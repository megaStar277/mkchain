# sslmerge

## Releases

|            **STABLE RELEASE**            |           **TESTING RELEASE**            |
| :--------------------------------------: | :--------------------------------------: |
| [![](https://img.shields.io/badge/Branch-master-green.svg)]() | [![](https://img.shields.io/badge/Branch-testing-orange.svg)]() |
| [![](https://img.shields.io/badge/Version-v1.3.0-lightgrey.svg)]() | [![](https://img.shields.io/badge/Version-v1.3.0-lightgrey.svg)]() |
| [![Build Status](https://travis-ci.org/trimstray/sslmerge.svg?branch=master)](https://travis-ci.org/trimstray/sslmergel) | [![Build Status](https://travis-ci.org/trimstray/sslmerge.svg?branch=testing)](https://travis-ci.org/trimstray/sslmerge) |

## Description

Is an open source tool to help you build a valid SSL certificate chain.

## Parameters

Provides the following options:

```
  Usage:
    sslmerge <option|long-option>

  Examples:
    sslmerge --in Root.crt --in Intermediate.crt --in Server.crt --out nginx_bundle.crt
    sslmerge --in /tmp/certs/ --out /tmp/nginx_bundle.crt

  Options:
        --help        show this message
        --debug       displays information on the screen (debug mode)
    -i, --in          add certificates to merge (multiple files or directory)
    -o, --out         saves the result (chain) to file
```

## Requirements

**<u>sslmerge</u>** uses external utilities to be installed before running:

- [openssl](https://www.openssl.org/)

## Install/uninstall

It's simple - for install:

```
./setup.sh install
```

For remove:

```
./setup.sh uninstall
```

> - symlink to `bin/sslmerge` is placed in `/usr/local/bin`
> - man page is placed in `/usr/local/man/man8`

## Use example

Then an example of starting the tool:

![sslmerge_output](doc/img/sslmerge_output.png)

## Result/output

**Sslmerge** displays a lot of useful information on the output:

- **chain generated correctly**

  Means that the creation of the correct certificate chain has been **completed successfully**. In addition, this means that all required certificates have been found.

- **not found root certificate**

  The chain was **generated correctly** but it does **not contain the root certificate**.

  The use of root certificates is not a good practice. They serve no purpose (clients will always ignore them) and they incur a slight performance (latency) penalty because they increase the size of the SSL handshake.


- **not found intermediate certificate**

  The chain was **not created correctly**. Most often it contains only the server certificate in the output file.

## Logging

After running the script, the `log/` directory is created and in it the following files with logs:

- `<script_name>.<date>.log` - all `_logger()` function calls are saved in it
- `stdout.log` - a standard output and errors from the `_init_cmd()` function are written in it. If you want to redirect the output from command, use the following structure: `your_command >>"$_log_stdout" 2>&1 &`

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Project architecture

    |-- LICENSE.md                 # GNU GENERAL PUBLIC LICENSE, Version 3, 29 June 2007
    |-- README.md                  # this simple documentation
    |-- CONTRIBUTING.md            # principles of project support
    |-- .gitignore                 # ignore untracked files
    |-- .travis.yml                # continuous integration with Travis CI
    |-- setup.sh                   # install sslmerge on the system
    |-- bin
        |-- sslmerge               # main script (init)
    |-- doc                        # includes documentation, images and manuals
        |-- man8
            |-- sslmerge.8         # man page for sslmergel
    |-- lib                        # libraries, external functions
    |-- log                        # contains logs, created after init
    |-- src                        # includes external project files
        |-- helpers                # contains core functions
        |-- import                 # appends the contents of the lib directory
        |-- __init__               # contains the __main__ function
        |-- settings               # contains sslmergel settings
    |-- example                    # examples of certs needed to build a chain

## License

GPLv3 : <http://www.gnu.org/licenses/>

**Free software, Yeah!**
