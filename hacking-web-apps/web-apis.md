---
description: Tricks and resources for hacking web APIs
---

# Web APIs

## Enumeration / Discovery

You can use a fuzzer to enumerate API endpoints, but before doing that, it is worth to check if the API you are testing have a spec document.

```
/openapi.json
/swagger/docs/v1
/graphql
```

### Visualize OpenAPI

You can use things like [https://editor.swagger.io/](https://editor.swagger.io/) to visualize OpenAPI spec.
