---
layout: page
title: response.write()
parent: Response object
grand_parent: Reference
---

An alternative to [print()](/reference/builtins/print.html) for writing the response body. It only accepts a *bytes-like* object.

Example:
```python
from httpout import run, response

async def main():
    await response.write(b'Hello, ')
    await response.write(b'World!')


run(main())
```
