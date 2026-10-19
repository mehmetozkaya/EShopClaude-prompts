# Lecture 64 - Building /finish-spec

The biggest skill of the four, built the honest way: dictate it, check it against WOW.md, find what it missed, fix it on camera, then harden the three details that make merging safe.

---

## Step 2 - Dictate five steps of the cycle

**Where:** the `claude` session on `main`.

**What it does:** Steps 5 to 9 of the cycle: implement, verify, mark Done, update the README, merge. The VERIFY step is the important one - it walks the spec's own Definition of Done and asks you about the checks it cannot run itself.

```text
Create a Claude Code skill in this repository at .claude/skills/finish-spec/SKILL.md.

It performs steps 5 to 9 of the cycle in @_agenticdev/WOW.md for one spec: implement it, verify it, merge it and close it out.

At the top of the skill body, inject the current repository state:
  Current branch: the output of git branch --show-current
  Commits so far: the output of git log --oneline main..HEAD
  Working tree:   the output of git status --porcelain

Invoked as /finish-spec <service> <NN>:

1. Preflight. Stop and explain if the current branch is not this spec's feature branch. Never run on main. If no branch exists for the spec, tell me to run /start-spec first.
2. DEVELOP. Implement the spec at _agenticdev/microservices/<service>/<NN>-*.md on this branch, following the plan already approved, honouring the spec's Explicit non-goals and the conventions in CLAUDE.md. Commit the work on the branch as you go.
3. VERIFY. Run dotnet build and stop on any error. Then walk the spec's own "Definition of Done" line by line. Run the checks you can run. For the checks you cannot run yourself - aspire run being healthy, a table or row in pgAdmin, a request in the .http file - ask me and wait for my answer. Any "no" stops the skill here, before anything is merged.
4. Mark the spec Done. Set its Status line to Done with the current commit SHA from git rev-parse HEAD.
5. Update the matching row in _agenticdev/microservices/README.md to the same status.
6. Commit those two documentation changes. Stage only the spec file and the README by explicit path. Never use git add -A.
7. Ask me to confirm, showing the branch name and the target. Then git checkout main, git merge --no-ff, and delete the feature branch. Stop on any merge conflict instead of resolving it yourself.
8. Report: the merge commit SHA, the files changed, and which Definition of Done lines were verified how.

Rules for this skill:
- Set disable-model-invocation to true, an argument-hint, and allowed-tools with Read, Write, Edit, Glob, git and dotnet build.
- Never push a feature branch. Push main after the merge.
- Treat step 7 as confirm-before-executing, because merging and deleting a branch are hard to reverse.
```

---

## Step 3 - Check it against the cycle

**Where:** the same session, after reading the generated skill.

**What it does:** The last sentence matters: do not fix anything yet. A review that fixes as it goes never tells you how big the gap was.

```text
Check .claude/skills/finish-spec/SKILL.md against the cycle in @_agenticdev/WOW.md. List every step of the cycle from 5 to 9 that the skill does not actually perform. Do not fix anything yet - just tell me what is missing.
```

---

## Step 4 - Fix the skill

**Where:** the same session.

**What it does:** The two missing steps are added where they belong, with everything else left alone.

```text
Add the two missing steps to .claude/skills/finish-spec/SKILL.md, after the preflight and before the status update.

First, DEVELOP: implement the spec on this feature branch, following the plan already approved, honouring the spec's Explicit non-goals and the conventions in CLAUDE.md, committing the work on the branch as you go.

Second, VERIFY: run dotnet build and stop on any error, then walk the spec's Definition of Done line by line - running the checks you can run, and asking me and waiting for the checks you cannot, such as aspire run, pgAdmin and the .http file. Any "no" stops the skill before anything is merged.

Keep everything else as it is.
```

---

## Step 5 - The three safety details

**Where:** the same session.

**What it does:** Stage by explicit path, never `git add -A`, and stop on a merge conflict instead of resolving it. These are the details that decide whether a skill is safe to let run.

```text
In .claude/skills/finish-spec/SKILL.md, make the documentation commit stage only the spec file and _agenticdev/microservices/README.md, by explicit path. Never git add -A or git add dot. And make the merge step stop and report on any merge conflict instead of resolving it.
```

---

## Step 6 - Commit the skill

**Where:** the same session.

**What it does:** The message names the three things it does: develop on the branch, verify the Definition of Done, merge with `--no-ff`.

```text
Commit the finish-spec skill on main. The message should say that it develops the spec on its feature branch, verifies the Definition of Done, and merges to main with --no-ff. Show me the message first, then push.
```
