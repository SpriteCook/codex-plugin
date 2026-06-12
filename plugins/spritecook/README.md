# SpriteCook Codex Plugin

This plugin packages the SpriteCook MCP connection and the core SpriteCook skills for Codex.

## What it includes

- Hosted SpriteCook MCP server configuration at `https://api.spritecook.ai/mcp/openai`
- `spritecook-workflow-essentials`
- `spritecook-generate-sprites`
- `spritecook-animate-assets`
- `spritecook-use-assets-in-godot`

## Authentication

SpriteCook's MCP server is private. Users still need a SpriteCook account, but Codex should authenticate through the native OAuth flow on the hosted production MCP endpoint.

Preferred path:

1. Install this plugin in Codex.
2. Connect SpriteCook when Codex prompts for authentication.
3. Approve the requested MCP scopes on the SpriteCook consent screen.

Manual fallback:

- For non-Codex editors or any legacy local bootstrap flow, run `npx spritecook-mcp setup`.

## Relationship to the existing installer

Codex install commands:

```powershell
iwr -useb https://spritecook.ai/install-codex.ps1 | iex
```

```bash
curl -fsSL https://spritecook.ai/install-codex.sh | bash
```

The current one-liner installer:

```powershell
iwr -useb https://spritecook.ai/install.ps1 | iex
```

still matters as a fallback bootstrap flow because it:

- verifies `node >= 18`
- finds `npx`
- runs `npx spritecook-mcp@latest setup`

This plugin replaces the old "install the skills plus MCP manually" workflow for Codex discovery and packaging. The existing installer remains the fallback path for non-Codex editors and local MCP bootstrap outside the OAuth flow.

