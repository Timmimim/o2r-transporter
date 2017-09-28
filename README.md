# o2r-transporter

![Travis CI](https://api.travis-ci.org/o2r-project/o2r-transporter.svg)

Delivery of files from compendia, partial or complete, individual or as an archive - transporter delivers everything.

This microservice implements file download and archive download features of the [o2r web API](http://o2r.info/o2r-web-api).
It integrates the now deprecated microservices [`o2r-transportar`](https://github.com/o2r-project/o2r-transportar/) and [`o2r-contentbutler`](https://github.com/o2r-project/o2r-contentbutler)

## o2r web API routes

- `/api/v1/compendium/:id/data`
- `/api/v1/job/:id/data`
- `/api/v1/compendium/:id.zip`
- `/api/v1/compendium/:id.tar.gz.`

## Requirements

- Node.js
- ImageMagic tool `convert` (for image previews)

## Usage

### Configuration

- `TRANSPORTER_PORT`
  Define on which Port muncher should listen. Defaults to `8081`.
- `TRANSPORTER_MONGODB` __Required__
  Location for the mongo db. Defaults to `mongodb://localhost/`. You will very likely need to change this.
- `TRANSPORTER_MONGODB_DATABASE`
  Which database inside the mongo db should be used. Defaults to `muncher`.
- `TRANSPORTER_BASEPATH`
  The local path where compendia are stored. Defaults to `/tmp/o2r/`.
- `SESSION_SECRET`
  String used to sign the session ID cookie, must match other microservices.

### Run

Run locally with

```bash
npm install
DEBUG=transporter,transporter:* npm start
```

Run in a container with

```bash
docker run -it --rm -p 8081:8081 o2rproject/o2r-transporter
```

## Develop

### Test

```bash
npm install -g mocha

# TODO start required Docker containers?

npm test
```

### Automated tests

See `.travis.yml`.

## Docker container

The `Dockerfile` is used to build an image on [Docker Hub](https://hub.docker.com/r/o2rproject/o2r-transporter/).

## License

o2r transporter is licensed under Apache License, Version 2.0, see file LICENSE.

Copyright (C) 2016 - o2r project.