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
## Setup
```
git clone https://github.com/tommynsong/simple-webapp
cd simple-webapp
docker build proxy
docker build web
docker compose up -d