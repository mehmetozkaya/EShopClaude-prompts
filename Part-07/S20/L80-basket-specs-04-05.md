# Lecture 80 - Basket Specs 04 and 05

The same two speeds again, and then the hardest review in the course. Spec 05 is where the order of operations is the specification: get it wrong and a buyer can lose a paid cart.

---

## Step 1 - Spec 04, gate and all

**Where:** a `claude` session on `main`. Two blocks, sent one after the other.

**What it does:** Autopilot plus the standing review instruction. Speed never removes the gate.

```text
/auto-spec basket-api 04

Use the spec-compliance-reviewer subagent to review this branch against basket-api spec 04's Definition of Done and the Basket rules in @_agenticdev/PROJECT.md before I merge.
```

---

## Step 3 - A clean window, then spec 05

**Where:** the same terminal. Three lines, sent one at a time.

**What it does:** `/new-spec basket-api 05` opens the checkout spec, where the order of the steps is the design.

```text
/clear
/rename basket-05
/new-spec basket-api 05
```

---

## Step 3 - The branch, and the standing instruction

**Where:** the same session, after you have read the spec.

**What it does:** Branch created from the rule, reviewer told in advance what it will audit.

```text
/start-spec basket-api 05

Use the spec-compliance-reviewer subagent to review this branch against basket-api spec 05's Definition of Done and the Basket rules in @_agenticdev/PROJECT.md before I merge.
```

---

## Step 4 - The hardest review in the course

**Where:** the same session, on the spec 05 branch.

**What it does:** Implement, verify, review, merge. Read the review's fourth rule check carefully: the cart must be cleared only after Ordering confirms, never before.

```text
/finish-spec basket-api 05
```
