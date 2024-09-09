---
layout: page
nav_order: 2
title: Hybrid async-sync
---

Let's explore how a typical synchronous framework handles requests.

When a request arrives, the web server (WSGI server) assigns it to a worker, usually **a thread** or a process,
which handles the request from **start** to **finish**.

```python
# a typical synchronous framework routing
@app.route('/hello')
def hello():
    # start

    return 'Hello, World!'
    # finish
```

This works fine for short requests, where processing times are in milliseconds,
and many requests can be handled with relatively few threads.

However, this model struggles with long-lived connections like WebSocket or SSE,
as each thread remains occupied for the duration of the connection.

For example, if you have 5 worker threads and all are tied up with long-lived connections,
the 6th request must wait until a thread is free.

This problem can be replicated on httpout with `wait` because httpout is also threaded by nature.

```python
# hello.py (httpout's file-based routing)
# start
import asyncio


async def main():
    # simulate a long-lived connection
    await asyncio.sleep(10)
    print('Done!')


wait(main())
# finish
```

But not if you use `run` instead of `wait`:

```python
# hello.py (httpout's file-based routing)
# start
import asyncio


async def main():
    # simulate a long-lived connection
    await asyncio.sleep(10)
    print('Done!')


run(main())
print('OK')
# finish (worker thread), main() will still run (on the main thread)
# should print the 'OK' first
```

With `run()` you can immediately leave the worker thread while it is running `main()`.

This essentially switches the style from threaded to asynchronous to handle long-lived connections -
which should explain why the hybrid async-sync in httpout is so powerful in this case.

Note that this does not mean you should use `run` in all cases, simply use `wait` if you want to wait.
