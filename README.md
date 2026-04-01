# SpriteCook Codex Plugin

This repository is the source of truth for the SpriteCook Codex plugin.

It packages:

- the SpriteCook plugin manifest
- the hosted SpriteCook MCP connection for Codex
- bundled SpriteCook skills
- local marketplace metadata for Codex installs

## Install locally in Codex

Recommended install:

```powershell
iwr -useb https://spritecook.ai/install-codex.ps1 | iex
```

macOS / Linux:

```bash
curl -fsSL https://spritecook.ai/install-codex.sh | bash
```

Then:

1. Restart Codex.
2. Open the plugin directory in Codex.
3. Choose the `SpriteCook` marketplace.
4. Install `SpriteCook`.
5. Complete the SpriteCook OAuth flow when Codex opens the connect page.

Codex installs local plugins from the marketplace entry in [`.agents/plugins/marketplace.json`](/path/to/spritecook-codex-plugin/.agents/plugins/marketplace.json).

## Repository layout

- [`.agents/plugins/marketplace.json`](/path/to/spritecook-codex-plugin/.agents/plugins/marketplace.json): local marketplace entry for Codex
- [`plugins/spritecook/.codex-plugin/plugin.json`](/path/to/spritecook-codex-plugin/plugins/spritecook/.codex-plugin/plugin.json): plugin manifest and install-surface metadata
- [`plugins/spritecook/.mcp.json`](/path/to/spritecook-codex-plugin/plugins/spritecook/.mcp.json): production SpriteCook MCP endpoint for Codex
- [`plugins/spritecook/skills/`](/path/to/spritecook-codex-plugin/plugins/spritecook/skills): bundled SpriteCook skills
- [`plugins/spritecook/assets/`](/path/to/spritecook-codex-plugin/plugins/spritecook/assets): plugin icons and branding assets

## Authentication

The plugin points Codex at the hosted production MCP endpoint:

- `https://api.spritecook.ai/mcp/openai`

Codex should handle authentication through the SpriteCook OAuth flow during install or first protected use.

For non-Codex editors or legacy local bootstrap flows, use:

```powershell
npx spritecook-mcp setup
```

## Release notes

- No plugin repo environment variables are required.
- No database migrations are required by this plugin package.
- If you change plugin metadata or assets, bump the plugin version in [`plugins/spritecook/.codex-plugin/plugin.json`](/path/to/spritecook-codex-plugin/plugins/spritecook/.codex-plugin/plugin.json) so Codex refreshes the installed cache cleanly.

## Skill source of truth

The bundled skills are maintained separately in:

- `/path/to/spritecook-skills`

When those skills change, sync the updated `SKILL.md` files into [`plugins/spritecook/skills/`](/path/to/spritecook-codex-plugin/plugins/spritecook/skills).
