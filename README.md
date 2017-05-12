## The official Bolt Docker Image

This is also the image that powers the container Bolt demo sites on https://try.bolt.cm 
and https://market.bolt.cm.

It uses Apache, PHP-FPM and SQLite in a single service.

It should be used in production with a separate http proxy container, we'd recommend
jwilder/nginx-proxy which will allow you to define a virtual host for each container.

### Releases

This repo mirrors the release branches of the main Bolt repo, starting with `release/3.2`
As new versions are released we will tag a corresponding version for the image. You can
always leave the tag empty or define `latest` which will have the same effect of installing
the latest stable version.


### Quick Start

All you need to do to get started is pull the image and then launch a container.

```bash
docker pull rossriley/docker-bolt
```

If you want to specify a specific tag then append that as below

```bash
docker pull rossriley/docker-bolt:3.2
```

Once the pull has completed then you can launch a container using the `docker run` command,
there are a few additional environment variables that you can pass, the one shown below installs
the default Bolt theme.

```bash
docker run -p 80 --name my_bolt_site -e APP_USER='my_bolt_site' -e APP_PASS='my_bolt_site_pw' -e APP_DB='my_bolt_site' -e BOLT_EXT='bolt/theme-2016 dev-master' -e BOLT_TITLE='My Bolt Site' -e BOLT_THEME='bolt/theme-2016' -d -t rossriley/docker-bolt
```