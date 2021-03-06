Apache+PHP build pack
========================

This is a build pack bundling PHP and Apache for Heroku apps. It has been modified to support Wordpress and other high-memory PHP applications.


Usage
-----

To use this buildpack as-is, see https://devcenter.heroku.com/articles/buildpacks and especially read the note about specifying a specific revision. If you don't specify a revision, then any updates to this repo will automatically propogate to your application the next time you push an application code update. (Note that adding this buildpack to a live application with heroku config:add will only affect the live application once you push an application code update and therefore rebuild the application slug. If you don't have any code updates to make, you can make an empty commit in git using git commit --allow-empty and push that.)


Configuration
-------------

The config files are bundled with the buildpack itself:

* conf/httpd.conf
* conf/php.ini


Pre-compiling binaries
----------------------

See https://devcenter.heroku.com/articles/buildpack-binaries for info on how to install and use vulcan.

    vulcan build -v -s ./build -p /tmp/build -c "./vulcan.sh"
    cp /tmp/build.tgz src/build.tgz


Hacking
-------

To change this buildpack, fork it on Github. Push up changes to your fork, then create a test app with --buildpack <your-github-url> and push to it.  If you make changes to the build script, you will need to precompile your binaries as above, upload them somewhere, and then change the "compile" script to download your tarball instead of ours.


Meta
----

* Original buildpack by Pedro Belo. https://github.com/heroku/heroku-buildpack-php
* Modified buildpack using vulcan by winglian@github. https://github.com/winglian/heroku-buildpack-php
* Further modified for Wordpress by Andrew Gorcester and Foundry Interactive. https://github.com/foundryinteractive/heroku-buildpack-php-foundry
