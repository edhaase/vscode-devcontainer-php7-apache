Application Profiling
===

Profiling for this project is provided via xdebug and webgrind.

## Setup

Most of the setup is already done!

* Run `composer install` to install dependencies including webgrind.
* (Optional) Install the chrome extension [xdebug-helper](https://chrome.google.com/webstore/detail/xdebug-helper/eadndfjplgieldjbigjakmdgkmoaaaoc) to make using xdebug easier.

## Usage

To profile the application, either call any url with `XDEBUG_PROFILE` or enable profiling in the xdebug-helper chrome extension. Then visit [127.0.0.1:80/webgrind]()

## Notes

The `/webgrind` alias is provided in  `.devcontainer/000-default.conf` should you need to change it.

xdebug_profiler configuration is defined in `.devcontainer/Dockerfile`


