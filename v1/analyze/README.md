# /v1/analyze
This endpoint provides a couple of methods for analyzing an IP address.

## Request
```
URL Query:
- ip (required): A public IPv4 address.
                 IPs belonging to a reserved or private range are disallowed.
```

## Endpoints
- [/sync](sync.md)
  - Sync analysis endpoint. The analysis is supposed to complete in the same HTTP request-response cycle.
- [/async](async.md)
  - Async analysis endpoint. The analysis is queued by the server, then a response is immediately returned.
