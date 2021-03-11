# Vue-3-Forms Notes

### Two-Way Data Binding and the v-model directive

- Bind data in both directions
- The easiest way to track what a user types into an input field is v-model, another vue directive
- it allows us to sync a form field with component data via two way data binding
- component data and template inputs are bound

### Useful techniques

- Putting form inputs into an array

### Vue Directive Notes

- When using `v-for`, Vue expects a unique `key` for each element we're looping cycling through

```
<div v-for="skill in skills" :key="skill">{{skill}}...
```

### Handle Submit

- Validation
- Chain the `prevent` event mod onto the `@submit` directive in the form tag === `e.preventDefault()`
