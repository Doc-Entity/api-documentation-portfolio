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

## Response Structure

The Evolution Chain endpoint returns a nested object representing the full evolution tree.

The main structure includes:

- `id`: Evolution chain identifier
- `chain`: Root of the evolution tree

The `chain` object contains
- `species`: Current Pokémon species
- `evolves_to`: Array of next-stage evolutions
- `evolution_details`: Conditions required for evolution

### Nested Chain Model

The structure is nested. Each entry inside `evolves_to` may contain another chain object with the same structure:

```text
species
└── evolves_to[]
    └── species
        └── evolves_to[]        
```

> **Note:** Evolution chains may branch. A single species can evolve into multiple different species depending on conditions.

## Common Evolution Fields

Within evolution_details, commonly used fields include:

- `min_level`: Minimum level required
- `item`: Required evolution item
- `trigger`: Evolution trigger (level-up, trade, use-item, etc.)
- `min_happiness`: Required friendship level
- `time_of_day`: Day or night evolution condition

Typically, you extract only the evolution details relevant to your application rather than processing the entire nested structure.

---
