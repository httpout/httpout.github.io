---
layout: default
title: WebSocket object
parent: Reference
has_children: true
has_toc: true
---

To work with a websocket connection. The `websocket` object will be `None` on requests that are not considered a websocket type.

Example:
```python
# ws.py
import sys

from httpout import run, response, websocket

if websocket is None:
    response.set_status(400, 'Bad Request')
    print('Not a websocket request')
    sys.exit()


async def main():
    async for message in websocket:
        await websocket.send(f'You said: {message}')


run(main())
```
