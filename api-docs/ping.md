---
type: endpoint
title: Ping
published: true
---

openapi: 3.0.3
info:
  title: Ping
  version: 1.0.0
servers:
  - url: https://api.example.com
paths:
  /ping:
    get:
      summary: Ping
      description: Health check endpoint.
      responses:
        "200":
          description: OK
