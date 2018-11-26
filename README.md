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

### check client certificate

check subject CN is `root`

```bash
$ openssl x509 -text -noout -in roles/cockroach/files/client.root.crt
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            1a:2b:3c:4d:5e:6f:th:is:is:ex:am:pl:e1:0f:fd:aa
    Signature Algorithm: sha256WithRSAEncryption
        Issuer: O=Cockroach, CN=Cockroach CA
        Validity
            Not Before: Nov 21 07:14:02 2018 GMT
            Not After : Nov 29 07:14:02 2028 GMT
        Subject: O=Cockroach, CN=root
        Subject Public Key Info:
(snip)
```

## Using Docker

This repository include `Dockerfile` and `docker-compose.yml`.
Using command below, you can use the commands `cockroach` and `ansible-playbook`.

```bash
$ docker-compose up -d --build
$ docker-compose exec cockroach
```
