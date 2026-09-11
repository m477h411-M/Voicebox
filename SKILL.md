---
name: backtalk-setup
description: Install and set up backtalk, the voice loop that lets you talk to your Claude Code agent out loud and hear it answer in a real voice about a second later. Clones a working copy, runs the installer, then walks the setup wizard — agent folder, push-to-talk key, voice engine, permissions — and test-fires the loop. Use when someone asks to set up backtalk or Voicebox, add a voice to their agent, talk to Claude out loud, or wants their assistant to speak back.
---

# backtalk — install and set up

backtalk is a voice loop for a Claude Code agent: hold a key, talk, and the person's own assistant answers out loud, sentence by sentence. This skill gets it installed and configured on their machine.

## The one rule about where it lives

**Never run the setup against `${CLAUDE_PLUGIN_ROOT}`.** A plugin directory is replaced when the plugin updates, and backtalk's setup writes `backtalk.json`, a `.venv/`, about a gigabyte of downloaded models and a `logs/` folder into whatever folder it runs in. Putting that in a plugin directory means an update silently takes all of it. Clone a working copy into a normal folder the person owns, and run everything there.

## Step 1 — Find or create the working copy

Ask where they want it; suggest `~/voicebox` unless they have a preference. If a clone already exists there — the folder contains `backtalk.json.example`, `run.sh` and `install.sh` — use it as-is and skip the clone.

```bash
git clone https://github.com/m477h411-M/Voicebox.git ~/voicebox
cd ~/voicebox
```

## Step 2 — Run the wizard from that folder

Read `backtalk.md` at the root of the clone and **execute it**. It is a setup wizard written to be followed phase by phase with the person — not summarized, not described. Start at Phase 1 and work through in order. Do not skip phases. Do not improvise.

From there the wizard owns the job: proving the install, finding their agent, picking the talk key and the voice engine, wiring permissions and the optional integrations, test-firing the loop, and leaving them a launcher icon.

## Worth knowing before you start

- **`agent_dir` is not the backtalk folder.** It points at the folder whose `CLAUDE.md` defines their own assistant. Never default it to the current directory — an unrelated project is not an agent. If they don't have one yet, Phase 2 says what to offer.
- **API keys go in the system keychain**, never into `backtalk.json`, a shell profile, or the chat.
- **Don't swap the `model`** for a deeper tier on their behalf. The fast tier is what makes the reply land in about a second.
- `install.sh` and `run.sh` are Mac and Linux. On Windows, Phase 1 makes you the installer — do it natively and use forward slashes in every path you hand a tool.
- When a test-fire step fails, `TROUBLESHOOTING.md` in the clone has the fix. Read it and apply it instead of improvising.
