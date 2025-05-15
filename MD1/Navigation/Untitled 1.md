

```dataviewjs
const property = "key_concept"; // change this to your desired property
let results = new Set();

for (let page of dv.pages('#System-block/CVS')) {
    let value = page[property];
    if (Array.isArray(value)) {
        value.forEach(v => results.add(v));
    } else if (value) {
        results.add(value);
    }
}

// Display results as a list
dv.header(2, `All unique values for "${property}"`);
dv.list(Array.from(results).sort());
```

