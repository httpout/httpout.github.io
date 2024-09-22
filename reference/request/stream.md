---
layout: page
title: request.stream()
parent: Request object
grand_parent: Reference
nav_order: 7
---

An *async generator*, to stream the request body.

Example:
```python
from httpout import run, request


async def main():
    async for data in request.stream():
        print(len(data))


run(main())
```
