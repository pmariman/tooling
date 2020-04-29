## Rationale

* The default user in a Docker container is root.
* All files created in a shared volume will have the root ownership.
* This image has a *dev* user, optionally with the same UID and GID as the creating user.
* This allows to read and write files from shared volumes with the same owner and group as the host system.


## Usage

* Create Docker nginx-http-share image:

```
$ docker build -t nginx-http-share .
```

* Start Docker nginx-http-share container:

```
$ docker run --rm -d -p 8090:80 \
           -v </full/path/to/share/>:/usr/share/nginx/data nginx-http-share
```
