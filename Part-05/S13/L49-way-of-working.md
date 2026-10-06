# Lecture 49 - Writing the Way of Working

Five prompts that produce WOW.md, the spec template, and the one line in CLAUDE.md that loads them into every session. The first one is long on purpose: it dictates the headings, so Claude writes our rules and not its own.

---

## Step 2 - Draft WOW.md

**Where:** the `claude` session, in **Manual** mode, so every write is reviewed.

**What it does:** Claude writes the file from the headings you give it. The last three lines do the real work: a hard line limit, no duplication with CLAUDE.md, and the line count reported back.

```text
Read @_agenticdev/PROJECT.md and @_agenticdev/PLAN.md, then create _agenticdev/WOW.md: the Way of Working that our team and Claude Code both follow on this repository.

Structure it with these headings.

Principles
- One spec is one sub-feature, one feature branch, one merge to main.
- A spec changes exactly one microservice and its own AppHost registration.
- main always builds and runs. Every merge leaves a working solution.
- Every spec is self-contained, so a fresh session only needs to read that one file.

Branches and merges
- One spec is one feature branch, named feature/<service>-<NN>-<short-name>, branched from main.
- The spec is the first commit on the branch, before any code.
- Merge into main with git merge --no-ff, then delete the branch. Feature branches stay local and are never pushed.
- No direct commits to main.

Folder layout
- Specs live in _agenticdev/microservices/<service>/NN-<short-name>.md, numbered per service, and are never renumbered.
- Every spec follows _agenticdev/templates/spec-template.md.
- _agenticdev/microservices/README.md holds the status table for all specs.

The cycle, per spec
Write it as nine numbered steps: pick the next spec, create the feature branch from main, start a fresh Claude Code session, plan in plan mode and approve the plan, implement in auto mode, verify manually, commit on the branch and merge to main with git merge --no-ff, mark the spec Done in the spec file and in the microservices README status table, delete the feature branch.

Ordering rules
- Specs run in number order inside a service.
- A spec does not start until every spec it depends on is merged to main.

Session hygiene
- One spec, one fresh session. Clear the context between specs.
- Plan mode before implementing, and a human approves the plan.
- Before any commit: dotnet build passes, aspire run starts every resource healthy, and the spec's Definition of Done passes.

Keep it under 120 lines, short bullets, no long paragraphs. Don't repeat anything that is already in CLAUDE.md. Tell me the line count when you are done.
```

---

## Step 3 - Cut what cannot be checked

**Where:** the same session, after reading the draft.

**What it does:** Every rule a person cannot verify by looking at the repository comes out, and vague rules are replaced by the concrete check behind them.

```text
Cut WOW.md down to about 120 lines. Remove every rule that a person cannot check by looking at the repository, and replace any vague rule with the concrete check behind it. Keep the nine-step cycle complete. Show me what you removed.
```

---

## Step 4 - The spec template as its own file

**Where:** the same session.

**What it does:** Seven sections, in order, left empty with one guidance line under each. Every spec in the course is filled in from this file.

```text
Create _agenticdev/templates/spec-template.md: the empty template that every spec in _agenticdev/microservices/ follows.

Sections, in this order:
1. Title line with the service, the spec number and the name, plus Status: Not started | In progress | Done.
2. Goal — one paragraph: why this sub-feature exists.
3. Depends on — which specs must already be merged to main, or "nothing".
4. Scope — a checklist of what to build.
5. Explicit non-goals — what must not be added while building it.
6. Definition of Done — the checks that prove it works: build, aspire run, and what to see where.
7. References — the PROJECT.md and PLAN.md sections this spec implements.

Leave every section empty, but put one short guidance line under each heading. Then add one line to WOW.md pointing at this template.
```

---

## Step 5 - Load the rules in every session

**Where:** the same session.

**What it does:** One `@import` line in CLAUDE.md, and nothing copied. This is why a fresh session already knows the way of working.

```text
Add a short "Way of working" section to CLAUDE.md with one line that imports our way of working: @_agenticdev/WOW.md

Add one sentence above it saying that the spec-driven delivery rules live in that file. Don't copy any rules from WOW.md into CLAUDE.md.
```

---

## Step 6 - Commit and push

**Where:** the same session.

**What it does:** The message explains the process this adds, not only the files it touches.

```text
Commit _agenticdev/WOW.md, _agenticdev/templates/spec-template.md and the CLAUDE.md change on main.

The message should explain the process this adds, and say that the way of working is imported from WOW.md rather than copied into CLAUDE.md.

Show me the message before you commit, then push main.
```
