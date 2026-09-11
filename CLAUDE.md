# Repo Boot — backtalk

<!-- This is the REPOSITORY's own boot file, loaded by Claude Code when `claude`
     runs inside a clone of this repo. It is not part of the shipped program, and
     it is NOT the person's agent config — their agent lives in whatever folder
     `agent_dir` points at, and backtalk only borrows its voice. -->

You are running inside a clone of **backtalk** (the repo is named `Voicebox`; the program inside it is backtalk).

Unless the person says otherwise, assume they are here to get the voice loop working.

**Do this first.** Read `backtalk.md` at the root of this repo and execute it. It is a setup wizard, written to be followed phase by phase with the person — not summarized, not described, not skimmed for highlights. Start at Phase 1 and work through in order. Do not skip phases. Do not improvise.

Open with one line, then wait for a yes. Something like: "I've got the backtalk setup wizard loaded — want me to set up your voice line? It's a few minutes, and the first run pulls about a gigabyte of speech models."

If they say they are only looking around, or ask a question about the code, answer it normally and leave the wizard alone until they ask for it.

## Five things to get right

- **The wizard runs from this folder.** `backtalk.json`, `.venv/`, the models and `logs/` all live here. If Claude Code was launched somewhere else, stop and have them `cd` here first.
- **`agent_dir` is NOT this folder.** It points at the folder whose `CLAUDE.md` defines the person's own assistant — the one with a name and a personality. This file you are reading is the repo's boot config, not an agent, and pointing the voice at it gives them a voice with nobody behind it. Phase 2 covers what to do when they don't have an agent yet.
- **No API key ever goes in a file.** The ElevenLabs key goes into the system keychain (or `ELEVENLABS_API_KEY` on Windows). Never into `backtalk.json`, never into a shell profile you write for them, never into the chat.
- **Don't change `model`.** The voice runs on the fast tier on purpose — that is most of the difference between a reply in about a second and one that feels broken. Never swap it for a deep-work model on their behalf without first saying what it costs in latency. The voice console's "switch to the deep model" is the sanctioned route, and it lasts one session.
- **`backtalk.json` is theirs and untracked.** Create it from `backtalk.json.example` if it's missing. Never overwrite an existing one without asking.

## What's in here

- `backtalk.md` — the setup wizard. Phases 1 through 6.
- `backtalk/` — the program: the ears (`ptt.py`, transcription), the mouth, the session loop.
- `install.sh` / `run.sh` — Mac and Linux only. On Windows, Phase 1 of the wizard makes **you** the installer; do the equivalent natively.
- `update.sh` / `update.bat` — updates, which never touch `backtalk.json`.
- `TROUBLESHOOTING.md` — when a test-fire step fails, read this and apply it rather than improvising.
- `skills/backtalk-setup/` + `.claude-plugin/` — the same setup, packaged so any Claude Code session can bootstrap an install.
