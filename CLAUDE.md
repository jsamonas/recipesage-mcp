# CLAUDE.md: recipesage-mcp

Jonathan Samonas's first public open-source project. It's an MCP server that lets Claude create and search recipes in RecipeSage. Owner: jsamonas. Licence: MIT.

## Decisions so far
- **Language:** TypeScript on Node 20+, using the official `@modelcontextprotocol/sdk`. Transport: stdio. Docker image later.
- **API:** RecipeSage `/compat/v2` (OpenAPI at https://docs.recipesage.com/api/).
  - Create: `POST /compat/v2/recipes/createRecipe`.
  - Login: `POST /compat/v2/users/login`, which returns a Bearer token valid for about 60 days.
- **Config** by environment variables: `RECIPESAGE_URL`, `RECIPESAGE_EMAIL`, `RECIPESAGE_PASSWORD` (only for the first login), `RECIPESAGE_TOKEN_FILE`.
- **Reference:** the RecipeSage adapter in github.com/poisdahl/meal-concierge (MIT). Its issue #6 covers handling the token safely.
- **Jonathan's own instance** is self-hosted on his Unraid server ("Alexandria").

## Working rules
- Use per-session branches and pull requests. Never push straight to `main` once v0.1 lands.
- Claude never handles Jonathan's RecipeSage password. He enters credentials into the config himself.
- Keep the README honest about status.
- Jonathan is new to open source. When a practice is standard (semver, changelog, releases, the MCP registry listing), explain it once in a line, then do it.

## Definition of done for v0.1
`create_recipe` works against his self-hosted RecipeSage from Claude, and a test recipe appears there. There's a README quick-start, a tagged release `v0.1.0`, and the linked issue is closed.
