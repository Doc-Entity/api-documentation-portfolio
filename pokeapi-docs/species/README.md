# 🧬 PokéAPI Species

You can use the Species endpoint to retrieve detailed metadata about a Pokémon species.

Species data provides high-level information such as flavor text descriptions, evolution relationships, growth rate, egg groups, and classification details.

This section explains how to:

- Retrieve species data using a name or ID
- Understand key response fields
- Work with linked resources such as evolution chains
- Integrate species metadata into your application

---

## Species Overview

The Species endpoint returns metadata about a specific Pokémon species rather than individual Pokémon instances.

**Example request:**

GET `https://pokeapi.co/api/v2/pokemon-species/{id or name}/`

You can provide:

- A numeric species ID  
- A species name string  

---

## Response Structure

A species resource includes classification data, descriptive text, and links to related resources.

Commonly used fields include:

- `name`: Species name  
- `flavor_text_entries`: Pokédex descriptions across versions  
- `evolution_chain`: URL reference to the evolution chain resource  
- `growth_rate`: Growth category reference  
- `egg_groups`: Breeding classification  
- `habitat`: Natural habitat reference  
- `is_legendary`: Boolean flag  
- `is_mythical`: Boolean flag  

> **Note:** Typically, you extract only the fields required for your application rather than processing the full response payload.

Some fields link to additional endpoints, which means you may need to send follow-up requests if your application requires deeper data.

---

## Integration Workflow

A typical integration pattern includes:

1. Request species data from the endpoint.
2. Parse the fields relevant to your application.
3. Follow linked resource URLs when additional data is required (e.g., evolution chains).
4. Map the structured data to your internal models or UI components.

This allows species metadata to be used in encyclopedic views, gameplay systems, or data-driven tools.

---

### Example (JavaScript)

The following example demonstrates one way to retrieve species data in JavaScript.

```javascript
async function fetchSpecies(speciesName) {
  const response = await fetch(
    `https://pokeapi.co/api/v2/pokemon-species/${speciesName}`
  );

  if (!response.ok) {
    throw new Error("Failed to retrieve species data");
  }

  return await response.json();
}
```

---

## Summary

The Species endpoint provides structured metadata about Pokémon species, including descriptive text, classification details, and linked resources.

Use species identifiers to retrieve data, extract relevant properties, and follow related resource URLs when additional information is needed.
