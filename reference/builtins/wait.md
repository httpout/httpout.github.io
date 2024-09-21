---
layout: page
title: wait()
parent: Built-ins
grand_parent: Reference
---

Just like `run()`, this function is used to run a coroutine, but **waits** for the result.
```python
import asyncio

from httpout import run, wait

wait(asyncio.sleep(1))

# essentially the same as:
# run(asyncio.sleep(1)).result()

print('Done!')
```
