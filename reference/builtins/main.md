---
layout: page
title: __main__
parent: Built-ins
grand_parent: Reference
---

A reference to your main route. It is available across your submodule imports.

```python
# index.py
import foo

MESSAGE = 'This is index.py'

foo.main()
```

```python
# foo.py
# /: __main__ should point to index.py
# /foo.py: __main__ should point to foo.py (itself)
import __main__

MESSAGE = 'This is foo.py'

def main():
    print(__main__.MESSAGE)


if __name__ == '__main__':
    main()

```

