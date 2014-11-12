---
layout: api-command
language: Python
permalink: api/python/index_drop/
command: index_drop
related_commands:
    index_create: index_create/
    index_list: index_list/
---

# Command syntax #

{% apibody %}
table.index_drop(index_name) &rarr; object
{% endapibody %}

# Description #

Delete a previously created secondary index of this table.

__Example:__ Drop a secondary index named 'code_name'.

```py
r.table('dc').index_drop('code_name').run(conn)
```

