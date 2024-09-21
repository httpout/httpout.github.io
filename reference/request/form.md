---
layout: page
title: request.form()
parent: Request object
grand_parent: Reference
---

An awaitable object, to get the request body with `application/x-www-form-urlencoded` type.

```python
from httpout import run, request


async def main():
    form_data = await request.form()
    print(form_data)


run(main())
```
