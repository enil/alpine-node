# Alpine Node Docker image

[![enil/alpine-node](http://dockeri.co/image/enil/alpine-node)](https://hub.docker.com/r/enil/alpine-node/)

A Docker image running [node.js] with [tini][] on [Alpine Linux][].
The repo contains Dockerfiles for images for node.js `v6.2` including an `onbuild` variant.

## Usage

### `enil/alpine-node:6.2`

The `enil/alpine-node:6.2` image can be run by specifying a volume and a command running the application with `node`:

```sh
docker run -v .:/usr/src/app -w /usr/src/app -p 8080:8080 enil/alpine-node:6.2 npm start
```

### `enil/alpine-node:6.2-onbuild`

The `enil/alpine-node:6.2-onbuild` can be used as a base image for a Dockerfile:

```Dockerfile
FROM enil/alpine-node:6.2-onbuild

CMD ["npm", "start"]
```

By extending the base image the contents of the context directory is copied to `/usr/src/app` in the container and `npm
install` is run installing the dependencies specified in `package.json`.

## Customization

The images can be customized by passing [build arguments] to `docker` to `docker build`.
The following arguments can be used:

* `TINI_VERSION`
the APK version of [`tini`](https://pkgs.alpinelinux.org/package/v3.4/community/x86_64/tini) to install

* `NODEJS_VERSION`
 the APK version of [`nodejs`](https://pkgs.alpinelinux.org/package/edge/main/x86_64/nodejs) to install

* `APP_DIR`
 the directory to install the application to (`onbuild` only)

[node.js]:         https://nodejs.org/en/
[tini]:            https://github.com/krallin/tini
[Alpine Linux]:    https://www.alpinelinux.org/
[build arguments]: https://docs.docker.com/engine/reference/builder/#/arg

