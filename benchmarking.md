---
layout: page
nav_order: 10
title: Benchmarking
---

{: .note }
I assume you already know that you should use `--log-level ERROR` to ensure there is no IO activity on your terminal during the benchmark. You can try to scale up with e.g. `--worker-num 4` and also try `--loop uvloop` for a slight performance boost.

You will probably find that the performance of the following plain text is not that surprising:
```python
# hello.py

print('Hello, World!')
```

It may still be able to beat the average framework, but that's not where httpout's strengths lie!

As you know, httpout loads the `.py` file every request (although at least 50% of requests will be cached), this will degrade performance to some degree.

But it's a small price to pay to be able to **run blocking and non-blocking code in one place**, with no difficult syntaxes:
```python
# hello.py
import asyncio
import time


# run blocking code here
time.sleep(1)


async def main():
    # run non-blocking code here
    await asyncio.sleep(1)
    print('Hello, World!')


run(main())
```

And that's where the httpout's muscles come in handy. It easily lifts blocking io code, when async-only frameworks have trouble doing so.
