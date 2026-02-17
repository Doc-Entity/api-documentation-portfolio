
# ⚡ PokéAPI Pagination

You can use pagination to retrieve large collections of resources from the PokéAPI in smaller, manageable pages.

This section explains how to:

- Retrieve paginated results using `limit` and `offset`  
- Navigate through multiple pages using the `next` and `previous` URLs  
- Handle both Named and Unnamed resource lists  

---

## About Pagination

Pagination enables you to divide large collections of resources into smaller pages. Any endpoint that returns multiple resources, such as Pokémon, moves, or abilities, uses pagination by default.

### Query Parameters

- `limit`: Number of results returned per page (default: 20)  
- `offset`: Number of resources to skip before returning results  

**Example request:**  
GET `https://pokeapi.co/api/v2/pokemon?limit=40&offset=0`

**Note:** You can open this URL directly in a browser to inspect the raw JSON response.

---
