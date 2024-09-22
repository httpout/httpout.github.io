---
layout: page
title: response.append_header()
parent: Response object
grand_parent: Reference
---

To append a custom header to the [response.headers](/reference/response/headers.html).

Example:
```python
from httpout import response

response.append_header('X-Powered-By', 'foo')
```
