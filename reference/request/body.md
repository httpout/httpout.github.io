---
layout: page
title: request.body()
parent: Request object
grand_parent: Reference
---

An awaitable object, to get the request body at once.

{: .warning }
This will load the entire body into memory. Use [request.stream()](/reference/request/stream.md) whenever possible.

```python
from httpout import run, request


async def main():
    body = await request.body()
    print(body)


run(main())
```
