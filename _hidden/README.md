# Temporarily unpublished bridges

`openai/`, `deepgram/` and `cartesia/` live here so the docs site ships only the four
supported backends (OpenClaw, Hermes, LiveKit, ElevenLabs) while those are finished.

Removing a page from `docs.json` navigation is NOT enough on its own: Mintlify still
builds and serves an unlisted page, so it stays reachable by direct URL and findable in
site search. That is what happened here - the pages were dropped from the nav while the
home page still carried three cards linking straight to them.

To restore: `git mv _hidden/<name> <name>` and add the group back to `docs.json`.
