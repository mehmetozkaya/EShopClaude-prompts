# Lecture 80 - Basket Specs 04 Checkout Orchestration

The same two speeds again, and then the hardest review in the course. Spec 04 is where the order of operations is the specification: get it wrong and a buyer can lose a paid cart.

---

## Step 1 - A clean window, then spec 04

**Where:** the same terminal. Three lines, sent one at a time.

**What it does:** `/new-spec basket-api 04` opens the checkout spec, where the order of the steps is the design.

```text
/clear
/rename basket-04
/new-spec basket-api 04
```

---

## Step 2 - The branch, and the standing instruction

**Where:** the same session, after you have read the spec.

**What it does:** Branch created from the rule, reviewer told in advance what it will audit.

```text
/start-spec basket-api 04

Use the spec-compliance-reviewer subagent to review this branch against basket-api spec 04's Definition of Done and the Basket rules in @_agenticdev/PROJECT.md before I merge.
```

---

## Step 3 - The hardest review in the course

**Where:** the same session, on the spec 04 branch.

**What it does:** Implement, verify, review, merge. Read the review's fourth rule check carefully: the cart must be cleared only after Ordering confirms, never before.

```text
/finish-spec basket-api 04
```
