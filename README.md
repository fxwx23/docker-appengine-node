# docker-appengine-node

Docker image for the [Google App Engine Node.js Environment](https://cloud.google.com/appengine/docs/nodejs/).

## Installation
```
$ docker pull fxwx23/appengine-node
```

## Tags
|Tag       |`latest`, `14`  |`12`         | `10`        | `8` (deprecated)         |
|:---------|:---------------|:------------|:------------|:-------------------------|
|Node.js   |v14.16.0        |v12.21.0     |v10.24.0     |v8.17.0                   |
|Base      |ubuntu:20.04    |ubuntu:20.04 |ubuntu:20.04 |ubuntu:20.04              |
|Components|bq              |bq           |bq           |bq                        |
|          |gsutil          |gsutil       |gsutil       |gsutil                    |

※ Not supported so far below.
 - Other components like `cloud-datastore-emulator` , `pubsub-emulator` . 
 - `cloudbuild` support. 

## Usage
To use this image, pull from [Docker Hub](https://hub.docker.com/r/fxwx23/appengine-node). See [Installation](#installation) section.

Check the `gcloud` , `node` and `npm` commands:

```console
$ docker run --rm -it fxwx23/appengine-node:latest gcloud version
Google Cloud SDK 331.0.0
bq 2.0.65
core 2021.03.05
gsutil 4.59

$ docker run --rm -it fxwx23/appengine-node:latest node -v
v14.16.1

$ docker run --rm -it fxwx23/appengine-node:latest npm -v
6.14.11
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