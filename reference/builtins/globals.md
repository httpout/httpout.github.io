---
layout: page
title: __globals__
parent: Built-ins
grand_parent: Reference
nav_order: 7
---

`__globals__` is a process-level context,
meaning it is initialized when the server starts and can be accessed from anywhere. You can share objects underneath like `__globals__.myvar`.

`__globals__` is not thread-safe, but it can be safely modified within the async context.

```python
# hello.py
from httpout import __globals__, run

# unsafe
# __globals__.counter += 1


async def main():
    # safe
    __globals__.counter += 1


run(main())
```

## The \_\_globals\_\_.py file
`__globals__` is of type [types.ModuleType](https://docs.python.org/3/library/types.html#types.ModuleType) and can actually point to the module file, a [\_\_globals\_\_.py](https://github.com/nggit/httpout/blob/main/examples/__globals__.py) file in the document root (if it exists).

If it doesn't exist, you'll end up doing something tricky like this:

```python
# hello.py
# ...

if hasattr(__globals__, 'counter'):
    __globals__.counter += 1
else:
    # initialize
    __globals__.counter = 0

```

It's much cleaner if the initialization is done with `__globals__.py`:

```python
# __globals__.py

# initialize
counter = 0

```

## Advanced use of \_\_globals\_\_.py
Since `__globals__.py` is initiated when the server starts,
this allows us to do some other things such as [applying middleware](https://github.com/nggit/httpout/blob/main/examples/__globals__.py).
