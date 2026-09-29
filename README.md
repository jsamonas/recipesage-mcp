# recipesage-mcp

An [MCP](https://modelcontextprotocol.io) server that lets Claude, and other AI assistants that speak MCP, add recipes to and search recipes in [RecipeSage](https://recipesage.com). It works with the hosted service or your own self-hosted instance.

> **Status: pre-alpha.** Nothing to install yet. Follow along, open an issue with ideas, or help build it.

## Why

RecipeSage has a documented API ([docs.recipesage.com/api](https://docs.recipesage.com/api/)), but as of September 2026 there's no MCP server for it. An AI assistant can already write a good recipe. This project lets it save that recipe straight to your RecipeSage, so you don't have to copy and paste.

## Planned tools

| Tool | What it does |
|---|---|
| `create_recipe` | Saves a recipe (title, description, yield, times, ingredients, instructions, notes, source) to your RecipeSage |
| `search_recipes` | Searches your recipes by text |
| `get_recipe` | Returns one recipe in full |

## How it will work

- It logs in to your RecipeSage once with your own account and calls the `/compat/v2` API.
- RecipeSage has no API keys. It issues a session token that lasts about 60 days, which this server keeps in a local file only you can read and renews when needed.
- It runs locally over stdio, or as a small Docker container next to a self-hosted RecipeSage.
- It uses the same API whether you point it at `https://api.recipesage.com` or your own instance.

## Roadmap

- [ ] v0.1: `create_recipe` against a self-hosted instance, configured by environment variables
- [ ] v0.2: `search_recipes`, `get_recipe`, token renewal
- [ ] v0.3: Docker image, plus Unraid template
- [ ] v1.0: listed on the MCP registry, with tests against a disposable RecipeSage instance

## Not affiliated

This is an independent community project. It isn't made or endorsed by RecipeSage or its author. RecipeSage is licensed AGPL-3.0 for non-commercial use (see its [repository](https://github.com/julianpoy/recipesage)). This server only calls RecipeSage's public API over HTTP; respect RecipeSage's terms when you use it.

## Contributing

Contributions are welcome, including your first one ever. Start with [CONTRIBUTING.md](CONTRIBUTING.md). Please follow the [Code of Conduct](CODE_OF_CONDUCT.md).

## License

[MIT](LICENSE) © 2026 Jonathan Samonas
