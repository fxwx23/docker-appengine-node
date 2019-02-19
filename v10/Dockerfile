FROM ubuntu:18.04
LABEL maintainer "https://github.com/fxwx23"

# GAE/Node.js build & testing environment for Circle CI 2.0
ENV GCLOUD_SDK_VERSION 231.0.0
ENV NODEJS_VERSION 10.15.1

RUN apt-get update && \
  ln -sf /usr/share/zoneinfo/UTC /etc/localtime && \
  apt-get install -y --no-install-recommends \
  tzdata xvfb vim \
  curl ca-certificates \
  build-essential git unzip \
  ssh \
  python \
  gettext-base \
  openjdk-11-jre-headless python-pip && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*

# setup Google Cloud SDK
ENV PATH=/google-cloud-sdk/bin:/google-cloud-sdk/:$PATH
RUN curl -o google-cloud-sdk.tar.gz https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-${GCLOUD_SDK_VERSION}-linux-x86_64.tar.gz && \
  tar -zxf google-cloud-sdk.tar.gz && \
  rm google-cloud-sdk.tar.gz && \
  ./google-cloud-sdk/install.sh --quiet

# setup node.js environment
ENV PATH=/root/.nodebrew/current/bin:$PATH
RUN curl -L git.io/nodebrew | perl - setup && \
  nodebrew install-binary ${NODEJS_VERSION} && \
  nodebrew use ${NODEJS_VERSION}