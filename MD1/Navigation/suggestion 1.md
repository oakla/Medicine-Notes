

```dataview
table key_concept as "Concept", file.link as "Used In Lecture"
flatten key-concepts
group by key-concepts
sort key-concepts
```