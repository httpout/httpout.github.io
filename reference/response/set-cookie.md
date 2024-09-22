---
layout: page
title: response.set_cookie()
parent: Response object
grand_parent: Reference
---

To set a `Set-Cookie` header to the [response.headers](/reference/response/headers.html).

Signature:
```python
response.set_cookie(name, value='', expires=0, path='/', domain=None,
                    secure=False, httponly=False, samesite=None)
```

Example:
```python
from httpout import response

response.set_cookie('foo', 'bar')
```
