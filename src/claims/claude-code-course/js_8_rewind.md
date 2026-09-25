# Claims ledger — claude-code-course.html — js_8_rewind

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0365 · js:8. rewind · L- · script
> P4 broke the tests. Two ways out: rewind code, or rewind only the conversation.
- pass 1:
- pass 2: n/a simulated scenario

### C0366 · js:8. rewind · L- · script
> Rewinding code + conversation to the checkpoint before P2…
- pass 1:
- pass 2: ✅ checkpointing.md — "Restore code and conversation: revert both code and conversation to that point" (scenario n/a)

### C0367 · js:8. rewind · L- · script
> utils.ts and posts.ts restored — Claude edited them with its file tools. notes.txt is still gone: it was deleted by a Bash command, and checkpoints don't track Bash. That's what git is for.
- pass 1:
- pass 2: ✅ checkpointing.md — "Only direct file edits made through Claude's file editing tools are tracked"; Bash `rm` "cannot be undone through rewind" (file names n/a)

### C0368 · js:8. rewind · L- · script
> Rewinding only the conversation to before P4…
- pass 1:
- pass 2: ✅ checkpointing.md — "Restore conversation: rewind to that message while keeping current code" (scenario n/a)

### C0369 · js:8. rewind · L- · script
> Conversation rewound, code kept. P4 is gone from Claude's memory but utils.ts still has the regex version. Useful when the code is fine and the chat just went off the rails.
- pass 1:
- pass 2: ✅ checkpointing.md — "Restore conversation: rewind to that message while keeping current code" (scenario n/a)
