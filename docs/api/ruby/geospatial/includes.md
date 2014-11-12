---
layout: api-command
language: Ruby
permalink: api/ruby/includes/
command: includes
related_commands:
    intersects: intersects/
---
# Command syntax #

{% apibody %}
sequence.includes(geometry) &rarr; sequence
geometry.includes(geometry) &rarr; bool
{% endapibody %}

# Description #

Tests whether a geometry object is completely contained within another. When applied to a sequence of geometry objects, `includes` acts as a [filter](/api/ruby/filter), returning a sequence of objects from the sequence that include the argument.


__Example:__ Is `point2` included within a 2000-meter circle around `point1`?

```rb
> point1 = r.point(-117.220406,32.719464)
> point2 = r.point(-117.206201,32.725186)
> r.circle(point1, 2000).includes(point2).run(conn)

true
```

__Example:__ Which of the locations in a list of parks include `circle1`?

```rb
circle1 = r.circle([-117.220406,32.719464], 10, unit='mi')
r.table('parks')['area'].includes(circle1).run(conn)
```
