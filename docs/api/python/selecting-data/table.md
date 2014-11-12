---
layout: api-command
language: Python
permalink: api/python/table/
command: table
related_commands:
    filter: filter/
    get: get/
---

# Command syntax #

{% apibody %}
db.table(name[, use_outdated=False]) &rarr; table
{% endapibody %}

# Description #

Select all documents in a table. This command can be chained with other commands to do
further processing on the data.

__Example:__ Return all documents in the table 'marvel' of the default database.

```py
r.table('marvel').run(conn)
```


__Example:__ Return all documents in the table 'marvel' of the database 'heroes'.

```py
r.db('heroes').table('marvel').run(conn)
```


__Example:__ If you are OK with potentially out of date data from this table and want
potentially faster reads, pass a flag allowing out of date data.

```py
r.db('heroes').table('marvel', True).run(conn)
```

