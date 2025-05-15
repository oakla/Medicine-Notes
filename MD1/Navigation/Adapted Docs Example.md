---
aliases: 
tags:
---

```dataviewjs
for (let group of dv.pages("#Class/Literature-Note/Lecture").groupBy(p => p.key_concept)) {
    dv.header(3, group.key);
    dv.table(["Name", "Time Read", "Rating"],
        group.rows
            .sort(k => k.rating, 'desc')
            .map(k => [k.file.link, k["time-read"], k.rating]))
}
```
```dataviewjs
const concepts = new Map();

for (let concept of dv.pages('#Class/Literature-Note/Lecture').groupBy(p => p.key_concept)) { 
  dv.header(3, concept.key);
  dv.table(
	  ["Session"],
	  concept.rows
		  .map(k => [k.file.link])
	  )
}
```

