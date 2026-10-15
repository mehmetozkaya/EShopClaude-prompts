# Lecture 52 - From Backlog Stub to a Buildable Spec

Four prompts that turn a stub into a spec you could hand to anyone. No code is written in this lecture.

---

## Step 1 - Let Claude name the branch

**Where:** a cleared, renamed `claude` session on `main`.

**What it does:** Claude reads the branch naming rule from the way of working instead of being told it, which is a live test that WOW.md is really loaded.

```text
Create the feature branch for _agenticdev/microservices/catalog-api/01-product-data.md, following the branch naming rule in our way of working. Then show me the current branch.
```

---

## Step 3 - Let Claude interview you about the design

**Where:** the same session, in plan mode.

**What it does:** The AskUserQuestion pattern again, now at spec level. Naming the questions you *expect* is what stops Claude from guessing the Product fields, the schema creation and the connection string.

```text
Read @_agenticdev/microservices/catalog-api/01-product-data.md, @_agenticdev/templates/spec-template.md and the Catalog section of @_agenticdev/PROJECT.md.

Fill in this spec's empty sections: Context, Data model, Tasks and Files touched. Sharpen the Definition of Done so every line is a check I can run.

Before you write anything, ask me the design questions you cannot answer from those documents. I expect questions about the Product fields and their types, how the database schema gets created, and how the service gets its connection string.

Don't write any C# in this lecture, and don't change the Scope or the non-goals.
```

---

## Step 4 - Make every line of the Definition of Done runnable

**Where:** the same session, after reading the completed spec.

**What it does:** Anything you cannot run is replaced by the command, what to run, and what you should see and where.

```text
In the Definition of Done, replace anything I cannot run with the exact check: the build command, what I run, and what I should see and where.
```

---

## Step 5 - Commit the spec, before any code

**Where:** the same session, still on the feature branch.

**What it does:** The spec is the first commit on the branch. That is the rule from WOW.md, and it is what makes the later diff readable.

```text
Commit the completed spec on this branch, on its own, with a message saying which spec it is and that this is the spec commit before implementation. Show me the message first.
```
