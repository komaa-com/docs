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
| `teams/overview.mdx` | Teams setup landing: what you create, setup path, applies to all six bridges |
| `teams/azure-bot.mdx` | Entra app + Azure Bot + Teams channel/calling (redacted portal screenshots); canonical Microsoft Graph permissions table |
| `teams/app-package.mdx` | Download the generated manifest zip from StandIn; example manifest, placeholders, manual packaging |
| `teams/publish.mdx` | Upload routes (client / Developer Portal / org publish), register in StandIn, first call |
| `community.mdx` | Free community tier (shared bot, public Teams meeting) |
| `troubleshooting.mdx` | HMAC mismatch, unreachable agent, daily limits, port/path, ClawHub |
| `concepts/architecture.mdx` | StandIn bridge, HMAC WebSocket wire contract, call flow |
| `concepts/modes.mdx` | Realtime (speech-to-speech) vs. streaming (STT -> agent -> TTS) |
| `concepts/features.mdx` | Vision, group etiquette, outbound, recap, governance, security |
| `openclaw/installation.mdx`, `openclaw/configuration.mdx` | OpenClaw plugin (`@komaa/openclaw-msteams-bridge`) |
| `hermes/installation.mdx`, `hermes/configuration.mdx` | Hermes plugin (`hermes-msteams-bridge`) |
| `elevenlabs/example.mdx` | Step-by-step basic-bridge example walkthrough (clone, env, tunnel, StandIn, vision hook) |
| `livekit/example.mdx` | Step-by-step examples walkthrough (voice agent + bridge, avatar variant, Docker, integration points) |
| `openai/installation.mdx`, `openai/example.mdx`, `openai/configuration.mdx` | OpenAI Realtime bridge (`@komaa/openai-msteams-bridge`): install, basic-bridge example walkthrough (vision hook + custom lookup_order tool), env reference incl. OPENAI_MCP_SERVERS |
| `deepgram/installation.mdx`, `deepgram/example.mdx`, `deepgram/configuration.mdx` | Deepgram Voice Agent bridge (`@komaa/deepgram-msteams-bridge`, Python sibling `deepgram-msteams-bridge` on PyPI): install, basic-bridge example walkthrough (vision hook + custom lookup_order tool), env reference incl. DEEPGRAM_THINK_ENDPOINT_URL and VISION_REQUIRES_RECORDING |
| `cartesia/installation.mdx`, `cartesia/example.mdx`, `cartesia/configuration.mdx` | Cartesia Line bridge (`@komaa/cartesia-msteams-bridge`): install, basic-bridge example walkthrough (transport-only: agent code lives on Cartesia's platform, context via custom events), env reference incl. CARTESIA_TTS_MODEL goodbye and per-call overrides |

## Navigation (docs.json)

- Groups: Getting Started, Teams setup, Concepts, OpenClaw plugin, Hermes plugin, ElevenLabs
  bridge, LiveKit bridge, OpenAI bridge, Deepgram bridge.
- New pages must be added to `navigation.pages` in `docs.json` or they will not appear.
- Internal links are root-relative without extension, e.g. `/teams/azure-bot#8-grant-graph-permissions`.
- `/teams-app` (the old single-page Teams setup) redirects to `/teams/azure-bot` via
  `redirects` in `docs.json`; do not recreate the page.

## Style rules

- **No em dashes (the U+2014 character) anywhere.** This is client-facing content: use "-" or
  rewrite the sentence.
- Casing: **StandIn** (capital S, capital I), never "Standin" or "standin" in prose.
  Also: OpenClaw, Hermes Agent, ClawHub, Komaa.
- Use active voice and second person ("you"); sentence case for headings.
- Bold for UI elements (Click **Settings**); code formatting for files, commands, paths, keys.

## Single sources of truth

- The Microsoft Graph permissions table lives ONLY in
  `teams/azure-bot.mdx#8-grant-graph-permissions`. Other pages (`concepts/architecture.mdx`,
  `openclaw/configuration.mdx`, `hermes/configuration.mdx`) link to it; do not re-add copies.
- The example Teams manifest and placeholders table live ONLY in `teams/app-package.mdx`.
- Screenshots in `images/teams/` are pre-redacted (placeholder GUIDs, generic labels, no tenant
  or account info). Never add raw portal screenshots; regenerate redacted ones instead.
- The `quickstart.mdx#verify-optional` section documents downloading `install.sh` / `install.ps1`
  and reviewing them before running. It intentionally carries **no SHA-256 checksums** - a pinned
  hash goes stale on every installer change and silently breaks the documented verify step, so it was
  removed. Do not re-add checksums here.

## Content boundaries

- Do not document internal infrastructure (AKS cluster, MediaNode internals, portal admin APIs).
- Never publish real GUIDs, secrets, or tenant IDs in examples; use obvious placeholders.
