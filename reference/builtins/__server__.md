---
layout: page
title: __server__
parent: Built-ins
grand_parent: Reference
---

A tribute to PHP's [$_SERVER](https://www.php.net/manual/en/reserved.variables.server.php). If you're a pythonista, you should probably use `request.environ` instead.
```python
from httpout import __server__, request


print(
    __server__.REQUEST_METHOD,
    request.environ['REQUEST_METHOD']
)
```

Note that this doesn't necessarily provide the exhaustive environment to keep it minimal.

Only the following list is guaranteed:
```python
__server__.REQUEST_METHOD
__server__.SCRIPT_NAME
__server__.PATH_INFO
__server__.QUERY_STRING
__server__.REMOTE_ADDR
__server__.HTTP_HOST
__server__.REQUEST_URI
__server__.REQUEST_SCHEME
__server__.DOCUMENT_ROOT
```

