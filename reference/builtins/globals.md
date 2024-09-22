---
layout: page
title: __globals__
parent: Built-ins
grand_parent: Reference
nav_order: 6
---

A worker-level context. It points to the `__globals__.py` module in document root (if it exists).

You can put initial objects and also apply middlewares through the `__globals__.py`.
You can see an example of this file in [httpout/examples/\_\_globals\_\_.py](https://github.com/nggit/httpout/blob/main/examples/__globals__.py).
