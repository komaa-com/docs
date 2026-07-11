# Microsoft Teams Bridge (StandIn) - documentation

Source for **[docs.komaa.com](https://docs.komaa.com)** - the docs for the Microsoft Teams Bridge
plugins: voice/video (CVI) for **OpenClaw** (`@komaa/openclaw-msteams-bridge`) and **Hermes Agent**
(`hermes-msteams-bridge`), connected to the hosted **StandIn** media bridge
([standin.komaa.com](https://standin.komaa.com)).

Built with [Mintlify](https://mintlify.com); pushes to `main` auto-deploy to production.

## Structure

| Path | Contents |
|---|---|
| `docs.json` | site config + navigation |
| `index.mdx`, `quickstart.mdx` | Getting Started |
| `concepts/` | architecture · modes · features |
| `openclaw/`, `hermes/` | per-runtime installation + configuration |
| `logo/`, `favicon.svg` | brand assets |

## Local preview

```bash
npm i -g mint
mint dev          # http://localhost:3000  (run where docs.json lives)
```

## Scope

This repo documents the **plugins + the hosted StandIn evaluation flow** only. Internal worker /
control-plane runbooks live elsewhere and are intentionally not part of this site.
