# 🧩 Handling Nested Responses

Some API endpoints return responses that contain nested objects or arrays rather than a flat list of fields.

Nested responses are common when an API represents relationships between resources or hierarchical data.

You may encounter this type of structure when working with endpoints such as evolution chains, where one resource can contain additional related resources.

This guide explains how to:

- Identify nested response structures
- Navigate nested objects and arrays
- Extract the data relevant to your application

---

## Understanding Nested Data

A nested response contains objects or arrays inside other objects.

For example, an evolution chain includes a `chain` object that contains an `evolves_to` array.  
Each entry in that array may contain another object with the same structure.

This creates a hierarchical structure where related resources are grouped together in a single response.

Example structure:

```
species
└── evolves_to[]
    └── species
        └── evolves_to[]
```

Because the structure can repeat multiple times, you may need to navigate several levels to access all related data.

---

## Working with Nested Responses

A typical approach includes:

1. Retrieve the resource from the API.
2. Inspect the response structure.
3. Identify nested objects or arrays.
4. Navigate through each level of the structure.
5. Extract only the fields your application requires.

This approach helps you work with complex responses while keeping your application logic clear and manageable.

---

## Example (JavaScript)

The following example demonstrates one way to navigate a nested evolution chain response.

```javascript
function printEvolutionChain(chain) {
  console.log(chain.species.name);

  chain.evolves_to.forEach(evolution => {
    printEvolutionChain(evolution);
  });
}
```

In this example:

- The function prints the current species name
- It then navigates each entry inside `evolves_to`
- The function continues until no further evolutions exist

This pattern allows your application to process the full evolution structure regardless of how many stages exist.

---

## Summary

Nested responses enable APIs to represent relationships and hierarchical data inside a single response.

When working with nested structures:

- Identify embedded objects and arrays
- Navigate through each level of the structure
- Extract only the fields your application needs

Understanding nested responses helps you integrate more complex API resources into your applications.
