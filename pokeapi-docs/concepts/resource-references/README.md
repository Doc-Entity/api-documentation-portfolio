# 🔗 Handling Resource References

Some APIs return references to related resources rather than including the full data in a single response.

These references typically contain a resource name and a URL that points to the complete resource.

This approach enables APIs to return smaller responses while still providing access to related data.

This guide explains how to:

- Identify resource references in API responses
- Retrieve full resource data using reference URLs
- Integrate referenced resources into your application

---

## Understanding Resource References

A resource reference usually contains a `name` and a `url`.

Example:

```json
{
  "name": "bulbasaur",
  "url": "https://pokeapi.co/api/v2/pokemon/1/"
}
```

The reference provides enough information to identify the resource and retrieve the full data when needed.

Instead of returning the complete resource immediately, the API provides a link to the resource endpoint.

---

## Retrieving Referenced Resources

When your application encounters a resource reference, you can send a request to the provided URL to retrieve the full resource data.

Typical workflow:

1. Retrieve the initial resource from the API.
2. Identify fields that contain resource references.
3. Extract the reference URL.
4. Send a request to that URL to retrieve the full resource.

This approach allows your application to load additional data only when required.

---

## Example (JavaScript)

The following example demonstrates one way to retrieve a referenced resource.

```javascript
async function fetchResource(url) {
  const response = await fetch(url);

  if (!response.ok) {
    throw new Error("Failed to retrieve resource");
  }

  return await response.json();
}
```

This function retrieves the full resource using the URL provided in the reference object.

---

## Summary

Resource references allow APIs to represent relationships between resources without returning large response payloads.

When working with references:

- Identify reference objects containing resource URLs
- Retrieve the resource when additional data is required
- Integrate the retrieved data into your application

Understanding resource references helps you work effectively with APIs that separate related resources across multiple endpoints.
