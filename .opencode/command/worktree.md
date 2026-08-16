---
description: Create a git worktree with a context-based name.
agent: build
---

Execute the following command and nothing else:

```
git worktree add ".worktrees/<NOMBRE>"
```

Where `<NOMBRE>` must be derived from `$ARGUMENTS`:

- Convert the argument to a short `kebab-case` slug (lowercase, hyphens instead of spaces, no special characters).
- Keep it concise: max 3-4 meaningful words from the argument.

Do NOT change directory, inspect repos, or run any additional commands.
