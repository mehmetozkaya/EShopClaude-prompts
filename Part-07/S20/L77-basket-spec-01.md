# Lecture 77 - Basket Spec 01 Through the Skill Loop

The full loop on one spec: the refusal that proves the gate is real, the spec, the standing review instruction, and the branch. Redis is a new pattern in this project, so this spec gets the commands one at a time rather than `/auto-spec`.

---

## Step 1 - The refusal that now passes

**Where:** a `claude` session on `main`, before the spec exists.

**What it does:** Run first, on purpose. `/start-spec` refuses, because the spec file is still a backlog stub. The preflight we wrote in Lecture 63 is doing exactly what it was built to do.

```text
/start-spec basket-api 01
```

---

## Step 2 - A clean window, then the spec

**Where:** the same terminal. Three lines, sent one at a time.

**What it does:** `/clear` and `/rename` are session housekeeping; `/new-spec basket-api 01` is the skill. It reads the backlog stub, asks the design questions, and completes the spec file.

```text
/clear
/rename basket-01
/new-spec basket-api 01
```

---

## Step 3 - The standing review instruction

**Where:** the same session, at gate one, before any code exists.

**What it does:** Read the spec yourself first. Then tell Claude now - not at the end - that the reviewer will audit this branch before anything merges. An instruction given at the start cannot be forgotten in the middle of a long run.

```text
Read _agenticdev/microservices/basket-api/01-cart-storage-apphost-wiring.md.

Use the spec-compliance-reviewer subagent to review this branch against basket-api spec 01's Definition of Done and the Basket rules in @_agenticdev/PROJECT.md before I merge.
```

---

## Step 4 - The branch, named by the rule

**Where:** the same session.

**What it does:** All five preflight checks pass, so the skill creates the branch, names it from the rule in WOW.md, and commits the spec file alone as the branch's first commit.

```text
/start-spec basket-api 01
```
