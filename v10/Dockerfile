FROM ubuntu:20.04
LABEL maintainer "https://github.com/fxwx23"

# GAE/Node.js build & testing environment for Circle CI 2.0
ENV GCLOUD_SDK_VERSION 331.0.0
ENV NODEJS_VERSION 10.24.0

RUN apt update && \ 
  apt install -y software-properties-common && \
  add-apt-repository universe && \ 
  apt update && \
  ln -sf /usr/share/zoneinfo/UTC /etc/localtime && \
  apt install -y --no-install-recommends \
  tzdata xvfb vim \
  curl ca-certificates \
  build-essential git unzip \
  ssh \
  python2 \
  gettext-base \
  openjdk-11-jre-headless && \
  apt clean && \
  rm -rf /var/lib/apt/lists/*

RUN curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip.py && \
  python2 get-pip.py

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