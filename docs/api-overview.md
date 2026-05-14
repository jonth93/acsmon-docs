# API Overview

## API Reference

REST API overview, authentication, and rate limiting

The ACS Monitor API provides full programmatic access to all resources. All endpoints are prefixed with `/api/v1` and return JSON responses.

Prefer not to call the API by hand? Official client libraries for PHP, Laravel, Node.js, Python and bash are open-source on GitHub — see [Developer Libraries](#developer-libraries).

### Base URL

/api/v1

### Authentication

The API uses **Bearer token** authentication. Obtain a token via the login endpoint, then include it in all subsequent requests.

# 1. Login to get a token

POST /api/v1/auth/login

Content-Type: application/json

{"email": "admin@example.com", "password": "your-password"}

# Response:

{"token": "1|abc123...", "user": {"id": 1, "name": "Admin", ...}}

# 2. Use the token in subsequent requests

Authorization: Bearer 1|abc123...

You can also generate API tokens from the web UI under **Profile > API Tokens**. These long-lived tokens don't require the login flow.

### Rate Limiting

| Scope | Limit | Notes |
| --- | --- | --- |
| auth/login | 6 requests / minute | Prevents brute force attacks |
| General API | 60 requests / minute | Standard throttle for all authenticated endpoints |
| Network Tools | 10 concurrent / user | Additional stricter throttle on tool endpoints |

Rate limit headers (`X-RateLimit-Limit`, `X-RateLimit-Remaining`) are included in every response.

### Error Responses

// 401 Unauthorized

{"message": "Unauthenticated."}

// 403 Forbidden

{"message": "This action is unauthorized."}

// 422 Validation Error

{"message": "The name field is required.", "errors": {"name": ["The name field is required."]}}

// 429 Rate Limited

{"message": "Too Many Attempts."}

### Pagination

List endpoints return paginated results. Use `?page=2&per_page=25` query parameters. Responses include `current_page`, `last_page`, `per_page`, `total`, and navigation links.
