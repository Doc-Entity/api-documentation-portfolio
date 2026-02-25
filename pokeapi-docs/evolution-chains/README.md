# 🌿 PokéAPI Evolution Chains

You can use the Evolution Chain endpoint to retrieve structured evolution data for Pokémon species.

Evolution chain data supports applications that display progression trees, analyze evolution requirements, or model branching evolution paths.

This section explains how to:

- Retrieve evolution chain data
- Understand the nested chain structure
- Navigate nested evolution chain data.

---

## About Evolution Chain

Evolution data is accessed in two steps:

1. Retrieve a Pokémon species resource.
2. Use the `evolution_chain.url` field from that response to request the full evolution chain.

**Example species request:**

GET `https://pokeapi.co/api/v2/pokemon-species/{id or name}/`

The species response includes:

```json
"evolution_chain": {
  "url": "https://pokeapi.co/api/v2/evolution-chain/1/"
}
```

You then request:

GET `https://pokeapi.co/api/v2/evolution-chain/{id}/`

---
