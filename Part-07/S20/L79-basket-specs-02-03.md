# Lecture 79 - Basket Specs 02 and 03

Two specs, two different speeds. Spec 02 is a pattern we have already used, so it goes on autopilot. Spec 03 is the checkout sequence - the one design answer that decides the whole architecture - so it gets the commands one at a time.

---

## Step 1 - Spec 02 on autopilot

**Where:** a `claude` session on `main`. Two blocks, sent one after the other.

**What it does:** `/auto-spec` runs `/new-spec`, `/start-spec` and `/finish-spec` in sequence. The standing review instruction follows it immediately, so the branch is still reviewed before the merge.

```text
/auto-spec basket-api 02

Use the spec-compliance-reviewer subagent to review this branch against basket-api spec 02's Definition of Done and the Basket rules in @_agenticdev/PROJECT.md before I merge.
```

---

## Step 4 - A clean window, then spec 03

**Where:** the same terminal. Three lines, sent one at a time.

**What it does:** A fresh window for the spec that matters most. `/new-spec basket-api 03` asks the checkout questions: who calls whom, and when the cart is cleared.

```text
/clear
/rename basket-03
/new-spec basket-api 03
```

---

## Step 4 - The branch, and the standing instruction

**Where:** the same session, after the spec is complete and you have read it.

**What it does:** The branch is created and the reviewer is told, up front, what it will audit.

```text
/start-spec basket-api 03

Use the spec-compliance-reviewer subagent to review this branch against basket-api spec 03's Definition of Done and the Basket rules in @_agenticdev/PROJECT.md before I merge.
```

---

## Step 5 - Finish it, then read the architecture section slowly

**Where:** the same session, on the spec 03 branch.

**What it does:** The review's Architecture violations section is the one to read line by line here. This is the sequence the whole EShop depends on: Basket calls Ordering, and clears its cart only after Ordering confirms.

```text
/finish-spec basket-api 03
```
