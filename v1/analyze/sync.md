# /v1/analyze/sync
This endpoint is responsible for IP analysis in a blocking (sync) fashion.

The `percent` value shows the possibility of the IP being an anonymizer, out of 100. Automated action can be taken for values over `98` and it is better to flag the orders for manual review when the value is over `95`. It is your call to adapt the results to your own system.

## Example Request
```
> GET /v1/analyze/sync?ip=1.2.3.4 HTTP/2
> Host: kit.ooo.foundation
> User-Agent: curl/7.58.0
> Accept: */*
```

## Example Response
```
< HTTP/2 200 
< cache-control: no-cache, private
< content-type: application/json
< x-fingerprint: 69dbd9e5e06249f64712bdcfa14b7957da60b467
< x-ratelimit-limit: 50
< x-ratelimit-remaining: 49
< x-task-id: 94c328f7-acc3-4300-8a3d-d61865b03e73
< x-vcap-request-id: b1a0fde0-36f7-457f-6e81-532e4e959465
< content-length: 41
< date: Wed, 01 May 2019 13:05:28 GMT
< server: LiteSpeed
< alt-svc: quic=":443"; ma=2592000; v="35,39,43,44"
< 
{"status":true,"detail":"OK","percent":0}⏎
```
