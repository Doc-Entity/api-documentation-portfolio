# 📄 PokéAPI Pagination

You can use pagination to retrieve large collections of resources from the PokéAPI in smaller, manageable pages.

> **Note:** Pagination follows the standard resource navigation model using cursor-like traversal through result pages.

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

## Response Structure

A paginated response returns the following fields:

- `count`: Total number of resources available  
- `next`: URL for the next page (or `null` if last page)  
- `previous`: URL for the previous page (or `null` if first page)  
- `results`: Array of resources returned for the current page

### Example Response

The following example shows the response from:

GET `https://pokeapi.co/api/v2/pokemon?limit=2&offset=0`

```json
{
  "count": 1350,
  "next": "https://pokeapi.co/api/v2/pokemon?offset=2&limit=2",
  "previous": null,
  "results": [
    {
      "name": "bulbasaur",
      "url": "https://pokeapi.co/api/v2/pokemon/1/"
    },
    {
      "name": "ivysaur",
      "url": "https://pokeapi.co/api/v2/pokemon/2/"
    }
  ]
}
```

---

## Named vs. Unnamed Endpoints

- **Named endpoints** (like Pokémon, abilities) return `NamedAPIResource` objects with `name` and `url`.  
- **Unnamed endpoints** (like evolution-chain, machine) return `APIResource` objects with only a `url`.

---

## Retrieving All Pages

To retrieve all available resources from a paginated endpoint, continue sending requests until the `next` field returns `null`.

Basic workflow:

1. Send an initial request.
2. Inspect the `next` field in the response.
3. If `next` is not `null`, send a request to that URL.
4. Repeat until `next` is `null`.

### Example (JavaScript)

The following example demonstrates one way to implement this workflow in JavaScript.

```javascript
async function fetchAllPokemon() {
  let url = "https://pokeapi.co/api/v2/pokemon?limit=100&offset=0";
  const allResults = [];

  while (url) {
    const response = await fetch(url);
    const data = await response.json();
    allResults.push(...data.results);
    url = data.next;
  }

  return allResults;
}
```
---

## Summary

Pagination allows you to efficiently navigate large resource collections by retrieving data in smaller sequential responses.

Use the `limit` and `offset` parameters to control page size and position.

Follow the `next` field to move forward through pages, or the `previous` field to move backward, until no additional pages are available.
