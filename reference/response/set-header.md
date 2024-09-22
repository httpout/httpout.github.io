---
layout: page
title: response.set_header()
parent: Response object
grand_parent: Reference
---

To set a custom header to the [response.headers](/reference/response/headers.html).
This will overwrite the existing header (if any).

Example:
```python
from httpout import response

response.set_header('X-Powered-By', 'bar')
```
