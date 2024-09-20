---
layout: page
nav_order: 7
title: Virtual imports
---

The following syntax is an example of a virtual import:
```python
from httpout import request
```

As its name implies, it doesn't actually import from a file,
it just magically retrieves the current `request` object.

Since httpout uses [file-based routing](routing.html), this is the only viable way I can think of
to interact with objects like `request`, `response`, etc., by leveraging the import syntax.

I am not aware if there are other tools/frameworks that do something like this, so I just call it *virtual import*.

The objects that can be imported are mostly from the built-in:
```python
from httpout import (
    request,
    response,
    print,
    run,
    wait,
    __server__,
    __globals__
)
```

While `__main__` can be imported in this way:
```python
import __main__
```

Well, to use [print](/reference/print.html), there is no need to do so, unless on other built-ins like `run` or `wait`.

It is useful to avoid linter errors:
```
F821 undefined name 'run'
F821 undefined name '__globals__'
```