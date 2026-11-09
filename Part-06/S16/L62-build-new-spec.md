# Lecture 62 - Building /new-spec

The contract that builds the first skill, then both of its paths tried out, then the commit. The contract prompt is long on purpose: a skill is a procedure the team will run for months, so it is dictated, not improvised.

---

## Step 2 - Dictate the contract

**Where:** a cleared, renamed `claude` session on `main`, with an empty `.claude/skills/` folder.

**What it does:** Claude writes `SKILL.md` from your specification. Read the last block closely: the rules say what the skill must *not* do - no branch, no commit, no code in `src/` - and `disable-model-invocation: true` means only you can run it, never Claude on its own.

```text
Create a Claude Code skill in this repository at .claude/skills/new-spec/SKILL.md.

It prepares one feature spec for the spec-driven workflow in @_agenticdev/WOW.md, and it has two paths.

Invoked as /new-spec <service> <NN> [slug] ["title"]:

1. Resolve the spec file _agenticdev/microservices/<service>/<NN>-*.md.
2. If it does NOT exist, create it from _agenticdev/templates/spec-template.md, named <NN>-<slug>.md, with Status: Not started. Draft each section from the matching parts of _agenticdev/PROJECT.md and _agenticdev/PLAN.md. Never overwrite an existing spec file.
3. If it DOES exist, read it and report, section by section, which parts are complete and which are still stubs or too vague to build from. Then continue with the steps below to fill the gaps.
4. Read _agenticdev/microservices/README.md. Fill "Depends on" from the status table, and add a row for this spec if it does not have one.
5. Before writing anything, ask me the design questions you cannot answer from those documents - field names and their types, how the database schema is created, and how the service gets its connection string. One question per decision.
6. Write the spec: fill Context, Data model, Tasks and Files touched, and sharpen every line of the Definition of Done into a check a person can actually run.
7. Print the spec path, and a list of anything still to be decided by hand.

Rules for this skill:
- It only touches Markdown under _agenticdev. It must not create a branch, must not commit, and must not write any code in src/.
- Set disable-model-invocation to true, an argument-hint, and allowed-tools with Read, Write, Edit and Glob only. No Bash.
- Leave Status as Not started. A status that runs ahead of reality is worse than no status.

Write clear frontmatter and numbered steps, and keep it short enough to read in one screen.
```

---

## Step 5 - Path A, a spec that does not exist

**Where:** the same session. This is your own skill, invoked like any slash command.

**What it does:** The skill creates the spec from the template, fills what it can from PROJECT.md and PLAN.md, and asks about the rest.

```text
/new-spec catalog-api 05 health-endpoint "Health endpoint"
```

---

## Step 6 - Path B, a spec that already exists

**Where:** the same session.

**What it does:** Same command, different path: it reports section by section what is complete and what is still a stub, and never overwrites the file.

```text
/new-spec catalog-api 01
```

---

## Step 6 - Commit the skill

**Where:** the same session.

**What it does:** A project skill lives in the repository, so the whole team gets it on clone. The message says so.

```text
Commit the new-spec skill on main. The message should say what the command does and that it is a project skill, so the team gets it on clone. Show me the message first, then push.
```
