# Lecture 63 - Building /start-spec

Permissions first, body second. The `allowed-tools` line is decided before a single step is written, and the contract then enforces it.

---

## Step 1 - The permission line, decided first

**Where:** shown on a scratch tab in VS Code. This is not a prompt to send; it is the `allowed-tools` line that the next prompt asks for.

**What it does:** Five git verbs and nothing else. What is missing is the design decision: no `push`, no `merge`, no `rm`, no `reset`. `Bash(git commit:*)` scopes one command family, not a shell.

```text
allowed-tools: Read, Glob, Bash(git status:*), Bash(git branch:*), Bash(git checkout:*), Bash(git add:*), Bash(git commit:*)
```

---

## Step 2 - Dictate the preflight

**Where:** the `claude` session on `main`.

**What it does:** Steps 2 to 4 of the cycle in WOW.md. The preflight is the heart of it: five conditions that make the skill stop and explain instead of acting. Note that the branch name is derived from the rule in WOW.md, never invented and never asked for.

```text
Create a Claude Code skill in this repository at .claude/skills/start-spec/SKILL.md.

It performs steps 2 to 4 of the cycle in @_agenticdev/WOW.md for one spec: create the feature branch, commit the spec on it, and plan the implementation.

At the top of the skill body, inject the current repository state so you already know it before you start:
  Current branch: the output of git branch --show-current
  Working tree:   the output of git status --porcelain

Invoked as /start-spec <service> <NN>:

1. Resolve the spec file _agenticdev/microservices/<service>/<NN>-*.md.
2. Preflight. Stop and explain, without changing anything, if any of these is true:
   - the current branch is not main
   - the working tree has changes other than that spec file
   - the spec's "Depends on" entries are not all Done in _agenticdev/microservices/README.md
   - the spec still has empty or placeholder sections, in which case tell me to run /new-spec first
   - the spec is already marked Done
3. Derive the branch name from the branch naming rule in WOW.md. Never invent one and never ask me for one.
4. Create that branch from main.
5. Commit the spec file on its own, as the branch's first commit, with a message saying which spec it is and that this is the spec commit before implementation.
6. Read the spec and produce an implementation plan for it, in plan mode, scoped to the spec's Tasks and bounded by its Explicit non-goals.
7. Stop at the plan and let me approve it. Do not implement anything.

Rules for this skill:
- Set disable-model-invocation to true, an argument-hint, and allowed-tools with Read, Glob and only these scoped git commands: git status, git branch, git checkout, git add, git commit. No push, no merge, no rm.
- Never push a feature branch. In this repository feature branches stay local.
- When you refuse, say which check failed and what I should do next.
```

---

## Step 4 - The refusal that enforces our own rule

**Where:** the same session. Run it on a spec whose dependencies are not Done.

**What it does:** The skill refuses, names the failed check and says what to do next. That refusal is the feature, not a bug.

```text
/start-spec basket-api 01
```

---

## Step 5 - A second refusal, a spec already Done

**Where:** the same session.

**What it does:** A different preflight check fails, and the skill stops just as cleanly.

```text
/start-spec catalog-api 01
```

---

## Step 6 - Commit the skill

**Where:** the same session.

**What it does:** The message says what the skill does and that it refuses when dependencies are not Done.

```text
Commit the start-spec skill on main. The message should say what the skill does and that it refuses when a spec's dependencies are not Done. Show me the message first, then push.
```
