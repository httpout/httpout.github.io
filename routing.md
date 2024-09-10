---
layout: page
nav_order: 5
title: File-based routing
---

Rather than mapping URLs to functions like a typical framework routing,
httpout uses file-based routing.
This concept is familiar to those of you who have used PHP or [CGI scripts](https://en.wikipedia.org/wiki/Common_Gateway_Interface).

So instead of you writing like this:
```python
@app.route('/hello')
def hello():
    return 'Hello, World!'
```

You simply create a file and the file name will be used in routing.
```python
# hello.py

print('Hello, World!')
```

Such routing may not be the fastest, as it involves querying the file system (IO).
But it is less CPU-intensive than regex-based routing.

Of course, file-based routing might be ugly and not SEO-friendly if this is the case:
```
/posts.py?title=hello-world
```

To workaround this, you can use `PATH_INFO` instead of `QUERY_STRING`.
```
/posts.py/title/hello-world
```

And here's the snippet:
```python
# posts.py

print(__server__.SCRIPT_NAME)  # '/posts.py'
print(__server__.PATH_INFO)    # '/title/hello-world'
```

A 101 question, how is routing handled in the following case?
```
/posts.py/title/hello.py
```

httpout will still assume `/posts.py` is the destination file (whether it exists or not),
and `hello.py` will be part of `PATH_INFO`.

There will be no smart fallback.
