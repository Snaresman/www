---
layout: api-command
language: Ruby
permalink: api/ruby/inner_join/
command: inner_join
related_commands:
    eq_join: eq_join/
    outer_join: outer_join/
    zip: zip/
---

# Command syntax #

{% apibody %}
sequence.inner_join(other_sequence, predicate) &rarr; stream
array.inner_join(other_sequence, predicate) &rarr; array
{% endapibody %}

# Description #

Returns an inner join of two sequences. The returned sequence represents an intersection of the left-hand sequence and the right-hand sequence: each row of the left-hand sequence will be compared with each row of the right-hand sequence to find all pairs of rows which satisfy the predicate. Each matched pair of rows of both sequences are combined into a result row. In most cases, you will want to follow the join with [zip](/api/ruby/zip) to combine the left and right results.

Note that `inner_join` is slower and much less efficient than using [eq_join](/api/ruby/eq_join/) or [concat_map](/api/ruby/concat_map/) with [get_all](/api/ruby/get_all/). You should avoid using `inner_join` in commands when possible.

__Example:__ Return a list of all matchups between Marvel and DC heroes in which the DC hero could beat the Marvel hero in a fight.

```rb
r.table('marvel').inner_join(r.table('dc')) {|marvel_row, dc_row|
    marvel_row[:strength] < dc_row[:strength]
}.zip().run(conn)
```

(Compare this to an [outer_join](/api/ruby/outer_join) with the same inputs and predicate, which would return a list of *all* Marvel heroes along with any DC heroes with a higher strength.)