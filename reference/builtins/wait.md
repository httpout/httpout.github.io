---
layout: page
title: wait()
parent: Built-ins
grand_parent: Reference
nav_order: 4
---

Just like [run()](/reference/builtins/run.html), this function is used to run a coroutine, but **waits** for the result.

Example:
```python
import asyncio

from httpout import run, wait

wait(asyncio.sleep(1))

# essentially the same as:
# run(asyncio.sleep(1)).result()

print('Done!')
```
