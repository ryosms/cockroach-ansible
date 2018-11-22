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

## Using Docker

This repository include `Dockerfile` and `docker-compose.yml`.
Using command below, you can use the commands `cockroach` and `ansible-playbook`.

```bash
$ docker-compose up -d --build
$ docker-compose exec cockroach
```
