---
layout: page
title: request.files()
parent: Request object
grand_parent: Reference
---

An *async generator*, to stream the request body with `multipart/form-data` type.

```python
from httpout import run, request


async def main():
    async for info, data in request.files():
        print(info, data[:15])


run(main())
```
