# Documentation project instructions

## About this project

- Mintlify docs site for **StandIn**, the hosted Teams media bridge by Komaa (docs.komaa.com).
- Covers the Teams Voice Plugin for OpenClaw and Hermes Agent: install, configure, register a
  BYO Teams bot, and troubleshoot.
- Pages are MDX with YAML frontmatter; site config lives in `docs.json`. Deploys on push to `main`.

## Page inventory

| Page | Purpose |
|---|---|
| `index.mdx` | Landing page: what StandIn is, CVI pillars, capabilities |
| `quickstart.mdx` | Install the plugin, connect to StandIn, place a test call |
| `teams-app.mdx` | Register a BYO Teams bot; canonical Microsoft Graph permissions table |
| `community.mdx` | Free community tier (shared bot, public Teams meeting) |
| `troubleshooting.mdx` | HMAC mismatch, unreachable agent, daily limits, port/path, ClawHub |
| `concepts/architecture.mdx` | StandIn bridge, HMAC WebSocket wire contract, call flow |
| `concepts/modes.mdx` | Realtime (speech-to-speech) vs. streaming (STT -> agent -> TTS) |
| `concepts/features.mdx` | Vision, group etiquette, outbound, recap, governance, security |
| `openclaw/installation.mdx`, `openclaw/configuration.mdx` | OpenClaw plugin (`@komaa/msteams-bridge`) |
| `hermes/installation.mdx`, `hermes/configuration.mdx` | Hermes plugin (`hermes-msteams-bridge`) |

## Navigation (docs.json)

- Four groups: Getting Started, Concepts, OpenClaw plugin, Hermes plugin.
- New pages must be added to `navigation.pages` in `docs.json` or they will not appear.
- Internal links are root-relative without extension, e.g. `/teams-app#graph-permissions`.

## Style rules

- **No em dashes (the U+2014 character) anywhere.** This is client-facing content: use "-" or
  rewrite the sentence.
- Casing: **StandIn** (capital S, capital I), never "Standin" or "standin" in prose.
  Also: OpenClaw, Hermes Agent, ClawHub, Komaa.
- Use active voice and second person ("you"); sentence case for headings.
- Bold for UI elements (Click **Settings**); code formatting for files, commands, paths, keys.

## Single sources of truth

- The Microsoft Graph permissions table lives ONLY in `teams-app.mdx#graph-permissions`.
  Other pages (`concepts/architecture.mdx`, `openclaw/configuration.mdx`,
  `hermes/configuration.mdx`) link to it; do not re-add copies.
- The `quickstart.mdx#verify-optional` section documents downloading `install.sh` / `install.ps1`
  and reviewing them before running. It intentionally carries **no SHA-256 checksums** - a pinned
  hash goes stale on every installer change and silently breaks the documented verify step, so it was
  removed. Do not re-add checksums here.

## Content boundaries

- Do not document internal infrastructure (AKS cluster, MediaNode internals, portal admin APIs).
- Never publish real GUIDs, secrets, or tenant IDs in examples; use obvious placeholders.
