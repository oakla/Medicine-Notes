---
aliases: 
tags:
---


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

