---
layout: api-command
language: Python
permalink: api/python/day_of_year/
command: day_of_year
related_commands:
    now: now/
    time: time/
---

# Command syntax #

{% apibody %}
time.day_of_year() &rarr; number
{% endapibody %}

# Description #

Return the day of the year of a time object as a number between 1 and 366 (following ISO 8601 standard).

__Example:__ Retrieve all the users who were born the first day of a year.

```py
r.table("users").filter(
    r.row["birthdate"].day_of_year() == 1
).run(conn)
```



