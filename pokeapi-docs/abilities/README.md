# ✨ PokéAPI Abilities

You can use the Abilities endpoint to retrieve detailed information about Pokémon ability resources.

Ability data supports applications that display passive effects, describe battle modifiers, or analyze gameplay mechanics.

This section explains how to:

- Retrieve ability data using identifiers or names
- Understand key response fields
- Process ability metadata for application use

---

## About Abilities

The Abilities endpoint returns metadata describing a specific ability resource.

**Example request:**

GET `https://pokeapi.co/api/v2/ability/{id or name}/`

You can provide:

- A numeric ability ID
- An ability name string

--- 
