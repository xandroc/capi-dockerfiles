FROM ruby:3.2-buster

ENV bosh_cli_version 7.5.0
ENV bbl_version 9.0.13

RUN apt-get update && \
    apt-get -y install \
    build-essential \
    wget \
    xz-utils \
    lsof \
    jq \
    vim \
    netcat-openbsd \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN \
  wget https://s3.amazonaws.com/bosh-cli-artifacts/bosh-cli-${bosh_cli_version}-linux-amd64 --output-document="/usr/bin/bosh" && \
  chmod +x /usr/bin/bosh

# Install bbl
RUN \
  wget https://github.com/cloudfoundry/bosh-bootloader/releases/download/v${bbl_version}/bbl-v${bbl_version}_linux_amd64 -P /tmp && \
  mv /tmp/bbl-* /usr/local/bin/bbl && \
  cd /usr/local/bin && \
  chmod +x bbl
