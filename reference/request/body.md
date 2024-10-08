---
layout: page
title: request.body()
parent: Request object
grand_parent: Reference
nav_order: 4
---

An awaitable object, to get the request body at once. The default maximum upload size is **2MiB**. You can change this with `--client-max-body-size`.

{: .warning }
This will load the entire body into memory. Use [request.stream()](/reference/request/stream.html) whenever possible.

Example:
```python
from httpout import run, request


async def main():
    body = await request.body()
    print(body)


run(main())
```
