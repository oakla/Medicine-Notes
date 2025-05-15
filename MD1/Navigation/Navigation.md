
```dataviewjs
const filter = "#System-block/CVS or #Topic/Haematology"

const property = "key_concepts"; // change this to your desired property
let results = new Set();

for (let page of dv.pages(filter)) {
    let value = page[property];
    if (Array.isArray(value)) {
        value.forEach(v => results.add(v));
    } else if (value) {
        results.add(value);
    }
}

// Display results as a list
dv.header(3, `All '${property}' in '${filter}'`);
dv.list(Array.from(results).sort());
```

