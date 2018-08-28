# faas-nginx-proxy
Docker container to proxy and cache OpenFaaS functions with `nginx. The container receives request on port 80 and forwards them to the function gateway running on 8080. It also caches function responses for 24 hours as a default. This cache time-to-live (TTL) can be modified by setting an environment variable when running the container.

## Installation
Build the image from source 
```bash
$ git clone https://github.com/satie/dockerfiles.git
$ cd dockerfiles/faas-nginx-proxy
$ docker build -t faas-nginx-proxy .
```

## Usage
Run the following command to run the nginx proxy and cache
```bash
$ docker run -p 80:80 --network=func_functions --name faas_proxy faas-nginx-proxy
```
This will map port `80` on the host to port `80` on the nginx container, and start nginx. The functions are exposed at the `/functions` context on the docker host. For example, to run the IP reputation report function use the following curl command
```bash
$ curl -X POST http://localhost/function/iprreport \
  -H 'Content-Type: application/json' \
  -d '{"ip": "8.8.8.8"}'
```

### Environment variables
The following properties in the nginx configuration can be changed by setting environment variables when running the container
* `CACHE_KEY_ZONE` - cache keys zone; defaults to `faas_cache`
* `CACHE_TTL` - cache item time-to-live; defaults to `24h`
* `MAX_CACHE_SIZE` - size of cache on disk; defaults to `1g`