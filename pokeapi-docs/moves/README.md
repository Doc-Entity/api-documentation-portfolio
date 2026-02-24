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
