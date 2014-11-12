---
layout: api-command
language: Python
permalink: api/python/coerce_to/
command: coerce_to
related_commands:
    object: object/
---

# Command syntax #

{% apibody %}
sequence.coerce_to('array') &rarr; array
value.coerce_to('string') &rarr; string
string.coerce_to('number') &rarr; number
array.coerce_to('object') &rarr; object
object.coerce_to('array') &rarr; array
binary.coerce_to('string') &rarr; string
string.coerce_to('binary') &rarr; binary
{% endapibody %}

# Description #

Convert a value of one type into another.

* a sequence, selection or object can be coerced to an array
* an array of key-value pairs can be coerced to an object
* a string can be coerced to a number
* any datum (single value) can be coerced to a string
* a binary object can be coerced to a string and vice-versa

__Example:__ Coerce a stream to an array to store its output in a field. (A stream cannot be stored in a field directly.)

```py
r.table('posts').map(lambda post: post.merge(
    { 'comments': r.table('comments').get_all(post['id'], index='post_id').coerce_to('array') }
)).run(conn)
```

__Example:__ Coerce an array of pairs into an object.

```py
r.expr([['name', 'Ironman'], ['victories', 2000]]).coerce_to('object').run(conn)
```

__Note:__ To coerce a list of key-value pairs like `['name', 'Ironman', 'victories', 2000]` to an object, use the [object](/api/python/object) command.

__Example:__ Coerce a number to a string.

```py
r.expr(1).coerce_to('string').run(conn)
```

