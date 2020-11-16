# docker-appengine-node

Docker image for the [Google App Engine Node.js Environment](https://cloud.google.com/appengine/docs/nodejs/).

## Installation
```
$ docker pull fxwx23/appengine-node
```

## Tags
|Tag       | `latest`, `10` | `8`        |
|:---------|:---------------|:-----------|
|Node.js   |v10.21.0       |v8.17.0     |
|Base      |ubuntu:19.10    |ubuntu:19.10|
|Components|bq              |bq          |
|          |gsutil          |gsutil      |

※ Not supported so far below.
 - Other components like `cloud-datastore-emulator` , `pubsub-emulator` . 
 - `cloudbuild` support. 

## Usage
To use this image, pull from [Docker Hub](https://hub.docker.com/r/fxwx23/appengine-node). See [Installation](#installation) section.

Check the `gcloud` , `node` and `npm` commands:

```console
$ docker run --rm -it fxwx23/appengine-node:latest gcloud version
Google Cloud SDK 318.0.0
bq 2.0.62
core 2020.11.06
gsutil 4.54

$ docker run --rm -it fxwx23/appengine-node:latest node -v
v10.21.0

$ docker run --rm -it fxwx23/appengine-node:latest npm -v
6.4.1
```

#### Circle CI 2.0

Add `.circleci/config.yml` to your repository.  

```yaml
version: 2
jobs:
  build:
    working_directory: /YOUR/REPO/PATH
    docker:
      - image: fxwx23/appengine-node
    steps:
      - checkout
      - run:
          command: # write your command.
```

## License

Copyright 2019 Fumitaka Watanabe ([@fxwx23](https://github.com/fxwx23))

Licensed under the MIT License.