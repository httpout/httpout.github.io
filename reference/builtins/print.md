---
layout: page
title: print()
parent: Built-ins
grand_parent: Reference
nav_order: 1
---

`print()` behaves like a regular [print()](https://docs.python.org/3/library/functions.html#print). It will add `'\n'` to the end.

If you prefer bytes-oriented and want to be more efficient, you can use [response.write()](/reference/response/write.html). This method is async therefore it should be *awaited*.
```python
# hello.py
from httpout import response

# ...

async def main():
    await response.write(b'Hello, ')
    await response.write(b'World!')


run(main())
```

Or wrapped with [run()](/reference/builtins/run.html) or [wait()](/reference/builtins/wait.html) if you want to use it outside the async context:
```python
# hello.py
from httpout import response

# ...

wait(response.write(b'Hello, '))
wait(response.write(b'World!'))
```
