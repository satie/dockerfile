# graylog
This is an updated version of the Docker compose file described in the [official graylog repo](https://hub.docker.com/r/graylog/graylog/). The `docker-compose.yml` file is upgraded to version `3`. Also, the graylog service exposes port `5044` for the `Filebeat` collector.

### Pre-requisites
* Create the `PASSWORD_SECRET` and `PASSWORD_SHA256` environment variables using any of the [methods supported by docker compose](https://docs.docker.com/compose/environment-variables/). For example, create environment in your shell using the following commands -

```bash
$ export PASSWORD_SECRET=ABCDEFGH12345678
```

```bash
$ echo -n graylog | sha256sum
4bbdd5a829dba09d7a7ff4c1367be7d36a017b4267d728d31bd264f63debeaa6  -
$ export PASSWORD_SHA256=4bbdd5a829dba09d7a7ff4c1367be7d36a017b4267d728d31bd264f63debeaa6
```

## Installation
Clone the [`dockerfiles`](https://github.com/satie/dockerfiles.git) repository

```bash
$ git clone https://github.com/satie/dockerfiles.git
```

To create a stack from the compose file, run the following command - 

```bash
$ docker stack deploy --compose-file docker-compose.yml graylog
Creating network graylog_default
Creating service graylog_elasticsearch
Creating service graylog_graylog
Creating service graylog_mongo
```

Browse to `http://localhost:9000` and login using the password created in the [prequisites](#prequisites) step.

### References
* [Official guide](https://hub.docker.com/r/graylog/graylog/) to run Graylog 2.4 with Elasticsearch 5.6.9 and Mongodb 3.