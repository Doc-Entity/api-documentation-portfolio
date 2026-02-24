# 🎯 PokéAPI Moves

You can use the Moves endpoint to retrieve detailed information about individual Pokémon move resources.

Move data supports applications that simulate battle mechanics, present move statistics in user interfaces, or analyze gameplay behavior.

This section explains how to:

- Retrieve move data using move identifiers or names
- Understand key response fields
- Process move metadata for application use

--- 

## About Moves

The Moves endpoint returns metadata describing a specific move resource.

**Example request:**

GET `https://pokeapi.co/api/v2/move/{id or name}/`

You can provide:

- A numeric move ID
- A move name string

---

## Response Structure

A move resource includes metadata describing battle behavior and classification.

Commonly used fields include:

- `accuracy`:  Hit probability
- `power`:  Base damage value
- `pp`: Number of uses before depletion
- `priority`: Execution order modifier
- `damage_class`: Physical, special, or status classification
- `effect_entries`: Human-readable effect descriptions

> **Note:** Typically, you extract only the fields required for your application rather than processing the full response payload.

---

## Integration Workflow

A typical integration pattern includes:

1. Request move data from the endpoint.
2. Parse the response fields relevant to the application.
3. Map the metadata to internal data models or UI components.
4. Handle optional or nullable fields as needed.

This workflow allows move metadata to be incorporated into battle systems, analytics tools, or data-driven applications.

### Example (JavaScript)

The following example demonstrates one way to retrieve move data in JavaScript.

```javascript
async function fetchMove(moveName) {
  const response = await fetch(
    `https://pokeapi.co/api/v2/move/${moveName}`
  );

  if (!response.ok) {
    throw new Error("Failed to retrieve move data");
  }

  return await response.json();
}
```

---

## Summary

The Moves endpoint provides structured battle metadata for individual move resources.

Use move identifiers to retrieve data, extract relevant properties, and integrate move metadata into application systems according to development requirements.
