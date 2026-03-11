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
