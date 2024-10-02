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

You simply create a `.py` file and the file name (including extension) will be used in routing.
```python
# hello.py

print('Hello, World!')
```

{: .note }
Routing or importing modules in the document root is expected to be stateless. It will not generate a [\_\_pycache\_\_](https://docs.python.org/3/tutorial/modules.html#compiled-python-files) folder and `.pyc` files.

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

There will be no smart fallback. You can still alter the routing behavior in the middleware, though.

## Security
File-based routing is generally secure, but issues can arise **if users are allowed to upload files**.

Without proper file name sanitization, an attacker can upload `malicious.py` and be able to run it through the URL.
To prevent this there are a few tricks to consider.
### 1. Sanitize names
Only allow `A-Z a-z 0-9 - _` in file names. You can allow `.` as well if you are validating the entire filename and extension. This will prevent many problematic characters such as [\\x00](https://en.wikipedia.org/wiki/Null-terminated_string) or `%`.

Double encoding is a source of loopholes that can occur due to developer confusion around [percent-encoding](https://en.wikipedia.org/wiki/Percent-encoding).

### 2. Append a hardcoded extension, e.g. `.jpg`
```python
NAME = normalize_or_hash_it(USER_PROVIDED_NAME) + '.jpg'
```

This limits the user's control over the final file name.

### 3. Upload to a folder that starts with `.`, e.g. `project_dir/.uploads/`
This is specific to httpout. Visitors will simply get a `403` if there are dotfiles in the URL.

This method is used when you do not intend to expose the upload result directly to the URL.
However, you should still be aware of the possibility of [path traversal](https://en.wikipedia.org/wiki/Directory_traversal_attack),
especially **if you intend to read those files through your code**.
