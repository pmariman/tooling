## Rationale

* The default user in a Docker container is root.
* All files created in a shared volume will have the root ownership.
* This image has a *dev* user, optionally with the same UID and GID as the creating user.
* This allows to read and write files from shared volumes with the same owner and group as the host system.


## Usage

* Create Docker development image:

```
$ docker build --build-arg USER_UID=$(id -u) --build-arg USER_GID=$(id -g) -t devel .
```

* Enter Docker development container:

```
$ docker run --rm -ti devel /bin/bash
```
