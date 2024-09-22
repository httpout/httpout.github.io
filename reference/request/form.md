---
layout: page
title: request.form()
parent: Request object
grand_parent: Reference
nav_order: 5
---

An awaitable object, to get the request body with `application/x-www-form-urlencoded` type.

Example:
```python
from httpout import run, request


async def main():
    form_data = await request.form()
    print(form_data)


run(main())
```
