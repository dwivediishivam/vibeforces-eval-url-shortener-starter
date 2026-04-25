# Idempotent URL Shortener — Spec

Build a Python (FastAPI) service:
1. POST /shorten {url, idempotency_key?} -> {short_code} (same key => same code)
2. GET /{short_code} -> 302 redirect, or 404
3. GET /metrics -> Prometheus text format with http_requests_total{path,status}
4. Storage: Redis (host `redis`, port 6379, no auth)
5. Short codes: 7 chars, base62, deterministic for (url, idempotency_key)
6. pytest covering: idempotency, 404 path, metrics shape

Acceptance test path: `tests/acceptance/`
