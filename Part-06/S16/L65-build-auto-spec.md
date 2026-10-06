# Lecture 65 - Building /auto-spec

The wrapper. It must not repeat the other three skills - it calls them by name, so each procedure keeps one source of truth.

---

## Step 2 - Dictate the wrapper

**Where:** the `claude` session on `main`.

**What it does:** Three skills, two human gates, and one rule that matters more than the rest: if any of the three refuses, stop, report which one and why, and never work around a refusal. The "When not to use this" section is part of the contract.

```text
Create a Claude Code skill in this repository at .claude/skills/auto-spec/SKILL.md.

It runs one spec end to end by invoking the three skills we already have. It must NOT repeat their steps - it calls them by name, so each procedure has one source of truth.

Invoked as /auto-spec <service> <NN>:

1. Run /new-spec <service> <NN>.
2. GATE ONE. Show me the completed spec and ask me to confirm it is buildable. Stop if I say no.
3. Run /start-spec <service> <NN>.
4. GATE TWO. Let me approve the implementation plan. Stop if I say no.
5. Run /finish-spec <service> <NN>.
6. If any of the three refuses, stop immediately. Report which skill refused and why, and never work around a refusal.
7. Print the close-out summary from /finish-spec.

Also add a short "When not to use this" section to the skill body, with these three cases:
- the spec introduces a pattern this repository has not built before
- the spec touches more than one service
- the spec's Definition of Done contains a check nobody can actually run

Set disable-model-invocation to true and an argument-hint. Keep the file short - the three skills do the work, this one only sequences them.
```

---

## Step 5 - Smoke test on a finished spec

**Where:** the same session. Run it on a spec that is already Done.

**What it does:** The chain stops at the first refusal, which proves the composition and the refusal handling in one command.

```text
/auto-spec catalog-api 01
```

---

## Step 6 - Commit the skill

**Where:** the same session.

**What it does:** The message says it chains the three and keeps both human gates.

```text
Commit the auto-spec skill on main. The message should say that it chains new-spec, start-spec and finish-spec and keeps both human gates. Show me the message first, then push.
```
