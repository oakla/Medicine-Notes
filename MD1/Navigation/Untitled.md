

```dataviewjs
const property = "key_concept";
const conceptMap = new Map();

for (let page of dv.pages()) {
    const concepts = page[property];
    if (!concepts) continue;

    const conceptList = Array.isArray(concepts) ? concepts : [concepts];

    for (let concept of conceptList) {
        const conceptKey = concept.toString(); // normalize for map key
        if (!conceptMap.has(conceptKey)) {
            conceptMap.set(conceptKey, []);
        }
        conceptMap.get(conceptKey).push(page.file.link);
    }
}

// Display as a table
dv.table(
    ["Concept", "Mentioned In"],
    Array.from(conceptMap.entries()).map(([concept, pages]) => [dv.markdown(concept), pages])
);
```