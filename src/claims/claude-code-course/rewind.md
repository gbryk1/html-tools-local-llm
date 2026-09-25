# Claims ledger — claude-code-course.html — rewind

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0114 · rewind · L1 · p
> Claude Code saves a checkpoint before each prompt: the conversation state plus snapshots of the files Claude edited. Press Esc Esc on an empty prompt (or run /rewind), pick a message, and choose: restore code, restore conversation, or both — or summarize from that point. That makes experiments cheap: let Claude try a bold approach, and rewind if you don't like it.
- pass 1:
- pass 2: ✅ checkpointing.md "How checkpoints work"/"Rewind and summarize" — "captures the state of your code before each prompt"; "press `Esc` twice when the prompt input is empty"; options Restore code / Restore conversation / both / Summarize from here

### C0115 · rewind · L1 · figcaption
> Real behavior: checkpoints track edits made by Claude's file tools. Changes made by Bash commands (rm, mv, cp), by you outside the session, or by other sessions are not restored. Checkpoints are not a replacement for git.
- pass 1:
- pass 2: ✅ checkpointing.md "Limitations" — "Checkpointing does not track files modified by Bash commands"; external/other-session edits "normally not captured"; "Not a replacement for version control"

### C0116 · rewind · L1 · tr
> claude -c / --continue | Continue the most recent conversation in this directory
- pass 1:
- pass 2: ✅ cli-reference.md `--continue`, `-c` — "Load the most recent conversation in the current directory"

### C0117 · rewind · L1 · tr
> claude -r / /resume | Pick any older session (by name or ID)
- pass 1:
- pass 2: ✅ cli-reference.md `--resume`, `-r` — "Resume a specific session by ID or name, or show an interactive picker"; commands.md `/resume [session]`

### C0118 · rewind · L1 · tr
> /rename, claude -n name | Name a session so you can resume it by name
- pass 1:
- pass 2: ✅ cli-reference.md `--name`, `-n` — "You can resume a named session with `claude --resume`"; commands.md `/rename [name]`

### C0119 · rewind · L1 · tr
> /branch | Branch the conversation at this point to try something different
- pass 1:
- pass 2: ✅ commands.md `/branch [name]` — "Create a branch of the current conversation at this point, so you can try a different direction"

### C0120 · rewind · L1 · tr
> --fork-session | Resume into a new session ID, leaving the original intact
- pass 1:
- pass 2: ✅ cli-reference.md `--fork-session` — "When resuming, create a new session ID instead of reusing the original"

### C0121 · rewind · L1 · tr
> /rewind, Esc Esc | Restore code and/or conversation to a checkpoint, or summarize from there
- pass 1:
- pass 2: ✅ commands.md `/rewind` — "Rewind the conversation and/or code to a previous point, or summarize from a selected message"

### C0122 · rewind · L1 · tr
> /diff | Review the working tree changes so far
- pass 1:
- pass 2: ✅ commands.md `/diff` — "Review the changes in your working tree, including the edits Claude has made so far"

### C0123 · rewind · L1 · tr
> /export, /copy | Save the conversation / copy the last answer
- pass 1:
- pass 2: ✅ commands.md `/export` — "Export the current conversation as plain text"; `/copy` — "Copy the last assistant response to clipboard"

### C0124 · rewind · L1 · p
> Checkpoints are local undo, git is history. Commit at every green state (“commit this with a descriptive message” is a perfectly good prompt). Then even a rm -rf through Bash is one git checkout away.
- pass 1:
- pass 2: n/a advice; consistent with checkpointing.md "Not a replacement for version control" (git restore only covers committed files)

### C0125 · rewind · L1 · li
> Every prompt = a checkpoint. Esc Esc → restore code, conversation, or both.
- pass 1:
- pass 2: ✅ checkpointing.md — "Every prompt you send that starts a turn creates a new checkpoint"; menu offers code / conversation / both

### C0126 · rewind · L1 · li
> Bash-made file changes are not tracked. Commit often.
- pass 1:
- pass 2: ✅ checkpointing.md "Bash command changes not tracked" — "These file modifications cannot be undone through rewind"

### C0127 · rewind · L1 · li
> Name sessions, resume with -c / -r, branch with /branch.
- pass 1:
- pass 2: ✅ cli-reference.md `-n`/`-c`/`-r`; commands.md `/rename`, `/branch`
