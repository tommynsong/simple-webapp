# simple-webapp
This is an example of how confidential files can be secured behind authentication, encryption-in-transit and proxy.
This example contain two containers running nginx, a proxy and a web.
All inbound requests are being routed/proxy via the proxy container as ports are not being exposed externally on the web container.
Both nginx servers are configured with SSL/TLS termination, as well as Basic Authentication.
## Authentication
The basic authentication includes the following:
```
admin / jg9Ajqc9yPNeLK3E
```
## Confidential documents
Any requests that match `/secreturi/` will be proxy to the web container.

## Pre-requisites
- Docker
## Setup and deploy
```
git clone https://github.com/tommynsong/simple-webapp
cd simple-webapp
docker build proxy
docker build web
docker compose up -d

## Usage
Once deployed, you can access the web app at `http://localhost` this will then redirect to `https://localhost`.
You will be then prompted with Basic Authentication, where you can either use the included sample credential in `htpasswd` or generate a new one of your own.
Any request that the URI prefix matches `/secreturi/` will then be pass to the `web` container where the `proxy` container serve as the external endpoint as well as catch all.