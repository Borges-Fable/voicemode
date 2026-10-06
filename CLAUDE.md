# voicemode

This repo's profile: only what an agent can't read from the code (ClaudeSetup #13). A line here changes only through the queue (`~/.claude/extensions/proposing.md`).

## What it is

Our own voice stack for Claude sessions, started from mbailey/voicemode as a base. A Python MCP server that gives a session speech in and speech out (Whisper for speech-to-text, Kokoro for text-to-speech, both local). We no longer pull from upstream: this is our thing (the owner, 2026-10-06).

## Where it runs

The operator's own computer, as the voice every session carries (ClaudeSetup #10). The services it talks to answer on that computer (`~/.voicemode/voicemode.env` holds the addresses).

## Issues

GitHub: Borges-Fable/voicemode, with the kinds and flags of `~/.claude/extensions/conventions.md`. Our changes to the voice flow (the floor, turn-taking) are tracked in Borges-Fable/VoiceModeSessions and ClaudeHub, where they are used.

## Language

Python 3.10 or newer, managed with `uv` (never pip directly). FFmpeg is required.

## What has to pass

Before a change counts as done:

- `make test` (the unit tests under `tests/`); `tests/manual/` needs a person and is not part of it.

## Working here

- `make dev-install` sets up a development copy.
- Logs and saved audio live under `~/.voicemode/` (`logs/conversations/`, `logs/events/`, `audio/`).
- Upstream's release process (`make release`, PyPI, the registry, its changelog rules) is not ours: we publish nothing. The version file and `CHANGELOG.md` are left as they are.

## Secrets

None in the vault for this repo today; a cloud speech provider would need a key, and that key would be a vault entry, never a file here.

## Procedures

Sheets in Borges-Fable/Runbooks, folder `voicemode/`: deploy, backup, rotating a secret, release. Read one only when you run it.
