---
title: print()
parent: Reference
---

`print()` behaves like a regular [print()](https://docs.python.org/3/library/functions.html#print). it will add `'\n'` to the end.

If you prefer bytes-oriented and want to be more efficient, you can use `response.write()`. This method is async and should be *awaited*.

or wrapped with `wait()` if you want to use it outside the async context.
