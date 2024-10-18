---
layout: page
title: run()
parent: Built-ins
grand_parent: Reference
nav_order: 2
---

`run()` is the key part that makes the [hybrid async-sync](/hybrid.html) possible in httpout.
This function is used to run a [coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutines) and then return a [concurrent.futures.Future](https://docs.python.org/3/library/concurrent.futures.html#concurrent.futures.Future) object.

Unlike [asyncio.run](https://docs.python.org/3/library/asyncio-runner.html#asyncio.run), this function (along with [wait](/reference/builtins/wait.html)) does not create a new event loop but uses the existing one.

Example:
```python
import httpout

async def main():
    pass

httpout.run(main())
```
