## gRPC Gateway POC

### What?
A trivial example of how to run gRPC gateway as a sidecar for an HTTP
protocol bridge.

### Why?
Because there are times you want to expose one protocol and use another
one internally.

### How?
[grpc-gateway](https://github.com/grpc-ecosystem/grpc-gateway)

### Try it
In a shell run:
```
git clone https://github.com/lowellmower/gateway-poc
cd gateway-poc && go run main.go
```
From another shell session run:
```
curl -X POST -k http://localhost:8090/v1/example/echo -d '{"name": " hello"}' | jq .
```
You should see:
```
{
  "message": " hello world"
}
```
Type safety:
```
curl -X POST -k http://localhost:8090/v1/example/echo -d '{"name": 1}' | jq .
{
  "code": 3,
  "message": "proto: (line 1:10): invalid value for string type: 1",
  "details": []
}
```

