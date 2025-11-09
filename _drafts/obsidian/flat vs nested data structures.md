A nested data structure typically gives you the advantage of not having any data duplication.  But, they can be hard to navigate.  If you have to filter or search or just pull out a specific value, it can be a pain to navigate.

While a flat data structure might have data duplication (even if it's just from a developer's perspective, and references all point to the single shared instance) but they are great for filtering, searching, or grouping.

A flat data structure is pretty simple.  You take all of the leaf nodes, or all of the deepest nested objects, and add a reference to each of the parent nodes.

For example:

```json
{
	school_a: {
		subject_a: {
			teacher_a: {
			},
			teacher_b: {
			},
		},
		subject_b: {
			teacher_a: {
			},
			teacher_b: {
			},
		},
	},
}
```

Would become:

```json
[
	Teacher(School school, Subject subject),
	Teacher(School school, Subject subject),
	Teacher(School school, Subject subject),
	Teacher(School school, Subject subject),
]
```

So whether you need all the teachers at harvard, or all the history teacher, you're still just have 1 loop that iterates over the array.

