# Apache APISIX Standalone Sample

## Basic Usage

```sh
docker run --rm \
  --restart=always \
  -p 9080:9080 \
  -e APISIX_STAND_ALONE=true \
  -v $(pwd)/apisix.yaml:/usr/local/apisix/conf/apisix.yaml \
  -v $(pwd)/config.yaml:/usr/local/apisix/conf/config.yaml \
  --name apisix-dp \
  apache/apisix:3.11.0-debian
```

## Build and Run the Image

```sh
$ docker build -t standalone-apisix:latest .
$ docker run --name apisix-standalone -p9080:9080 -p9443:9443 standalone-apisix:latest
```

## Test

```sh
➜  standalone-apisix git:(main) ✗ curl http://localhost:9080/uuid -v
* Host localhost:9080 was resolved.
* IPv6: ::1
* IPv4: 127.0.0.1
*   Trying [::1]:9080...
* Connected to localhost (::1) port 9080
> GET /uuid HTTP/1.1
> Host: localhost:9080
> User-Agent: curl/8.7.1
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 200 OK
< Content-Type: application/json
< Content-Length: 53
< Connection: keep-alive
< Date: Tue, 11 Mar 2025 03:38:12 GMT
< Access-Control-Allow-Origin: *
< Access-Control-Allow-Credentials: true
< Server: APISIX/3.11.0
<
{
  "uuid": "48f0631f-a180-4ace-a4e6-5ee0a5d8fd35"
}
* Connection #0 to host localhost left intact
```