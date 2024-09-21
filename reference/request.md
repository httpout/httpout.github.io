---
layout: page
title: Request object
parent: Reference
---

The request object gives you access to an HTTP request.

| Name                           | Description                                                                        |
|--------------------------------|------------------------------------------------------------------------------------|
| request.environ                | A dict object, identical to [\_\_server\_\_](/reference/builtins/server.html)
| request.headers                | A dict object
| request.cookies                | A dict object
| request.body()                 | An awaitable object, to get the request body at once
| request.form()                 | An awaitable object, to get the request body with `application/x-www-form-urlencoded` type
| request.files()                | An *async generator*, to stream the request body with `multipart/form-data` type
| request.stream()               | An *async generator*, to stream the request body
