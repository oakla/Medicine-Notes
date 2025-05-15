

```dataviewjs
const concepts = new Map();

for (let page of dv.pages('#Class/Literature-Note/Lecture')) { // adjust folder name if needed
  if (!page["key_concept"]) continue;
  for (let concept of page["key_concept"]) {
    const name = concept.path;
    if (!concepts.has(name)) {
      concepts.set(name, { concept, sources: [] });
    }
    concepts.get(name).sources.push(page.file.link);
  }
}

dv.table(["Concept", "Mentioned In"],
  Array.from(concepts.values()).map(({ concept, sources }) => [
    concept,
    dv.list(sources)
  ])
);
```