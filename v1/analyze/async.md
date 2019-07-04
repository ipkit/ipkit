# /v1/analyze/async
This endpoint is responsible for IP analysis in a non-blocking (async) fashion.

## Request
```
URL Query:
- callback (required): An HTTP URL to be called with analysis results after a background worker processes the inquiry.

                       This callback will be sent a payload of content type `application/json` with the same `X-Task-Id`
                       header returned by the call to this endpoint to help the caller identify the analysis results.
                       
                       The request method is POST.
                       
                       Originating IP of the worker is indeterministic. You should NEVER depend on the IP for authenticating
                       incoming requests.
```

## Example Request
```http
GET /v1/analyze/async?ip=176.53.43.8&callback=http://webhook.site/a7404220-9948-405e-97c2-a7caa1a9a4b6 HTTP/2
Host: kit.ooo.foundation
User-Agent: curl/7.58.0
Accept: */*
```

## Example Response
```http
HTTP/2 202 
cache-control: no-cache, private
content-type: application/json
x-fingerprint: 4a54fb680b45e4c5eb0ace598d021292a8e92eab
x-memory-peak-usage: 6635616
x-ratelimit-limit: 50
x-ratelimit-remaining: 49
x-task-id: 220704fb-5edb-4d35-b09a-69892aae516f
x-vcap-request-id: 00e42e33-9abc-4a9a-51d2-d573b711f477
content-length: 176
date: Sun, 05 May 2019 06:21:10 GMT
server: LiteSpeed
alt-svc: quic=":443"; ma=2592000; v="35,39,43,44"

{"status":true,"detail":"Inquiry accepted! The X-Task-Id header in the response will be sent as-is with analysis results to given callback. It may be used for identification."}
```

## Example Request (Callback)
This is the request sent by IP Kit's worker after the IP is analyzed to the `callback` above.
`X-Task-Id` headers both match in endpoint's response and the request of worker as seen.

![](https://i.snag.gy/VALOoz.jpg)
