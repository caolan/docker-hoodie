# Hoodie Dockerfile

**Warning: not recommended for production use yet**

This docker file bundles together Node.js, CouchDB and Hoodie to make it
easy to try out Hoodie without having to install dependencies manually. For
production use and increased flexibility, you'll probably want to put
together a docker file which uses an external CouchDB and data-only
containers.

## Build

Install docker from [docker.io](http://docker.io), then:

```
cd docker-hoodie
docker build -t hoodiehq/hoodie .
```

Then, create a data directory to store your couchdb data etc.

```
mkdir ./data
chmod 777 ./data
```

## Run

```
docker run -p 6001:6001 -p 6002:6002 \
    -v `pwd`/data:/home/hoodie/project/data hoodiehq/hoodie
```

You may want to replace `pwd` with the full path to the data directory you
created if it's not in the current directory.

You should now have a TODO app example running at http://127.0.0.1:6001 and
the Hoodie admin interface available at http://127.0.0.1:6002

**The admin password is "changeme"**. Since there isn't an option to do
that in the Hoodie admin interface atm, you should go to
http://127.0.0.1:6002/\_api/\_utils and click the 'Change password' link in
the bottom right corner.
