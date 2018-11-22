# Cockroach Ansible

Install Cockroach DB using ansible


## Network Configuration

1. Front Server
    - HAProxy
    - [PostgREST](http://postgrest.org/en/v5.1/index.html)
1. Database Server
    - [Cockroach DB](https://www.cockroachlabs.com/)
1. Database Server
    * Same as above

## Prepare

You must create security certificates, before running ansible-playbook.

1. install cockroach locally
    * If you don't want to install cockroach, you can use docker. See detail below.
1. create certificates with running command below
    * run `cockroach cert create-ca` command.
    * run `cockroach cert create-client` command.

```bash
$ mkdir -p roles/cockroach/files
$ cockroach cert create-ca \
    --certs-dir=roles/cockroach/files \
    --ca-key=roles/cockroach/files/ca.key

$ cockroach cert create-client \
    root \
    --certs-dir=roles/cockroach/files \
    --ca-key=roles/cockroach/files/ca.key
```


## Using Docker

This repository include `Dockerfile` and `docker-compose.yml`.
Using command below, you can use the commands `cockroach` and `ansible-playbook`.

```bash
$ docker-compose up -d --build
$ docker-compose exec cockroach
```
