FROM python:3.6
LABEL maintainer="ryosms<ryo.sms@gmail.com>"

WORKDIR /cockroach-ansible

RUN pip install ansible

ARG COCKROACH_VERSION="v2.1.1"

RUN wget -qO- https://binaries.cockroachdb.com/cockroach-${COCKROACH_VERSION}.linux-amd64.tgz | tar  xvz \
        && cp -i cockroach-${COCKROACH_VERSION}.linux-amd64/cockroach /usr/local/bin \
        && rm -rf cockroach-${COCKROACH_VERSION}.linux-amd64
