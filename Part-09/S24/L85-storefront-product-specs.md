# Lecture 85 - Storefront Specs: Listing Products and Adding to the Cart

Two blocks per spec, the same shape as the Basket specs: `/auto-spec` and the standing review instruction, sent as one message. This lecture runs every web spec up to and including the Products page. The numbers below assume the backlog came out as web 01 (clients, buyer constant, navigation) and web 02 (Products page); use the numbers in your own status table.

---

## Step 2 - The first storefront spec

**Where:** a `claude` session on `main`, after `/clear` and `/rename web-01`. One message: the command, a blank line, then the instruction.

**What it does:** `/auto-spec` runs `/new-spec`, `/start-spec` and `/finish-spec` in a row, and stops at gate one (the completed spec) and gate two (the plan). The instruction makes the spec-compliance-reviewer audit the branch before the merge. It says "the spec" rather than a number, so it is the same sentence for every storefront spec.

```text
/auto-spec web 01

Use the spec-compliance-reviewer subagent to review this branch against the spec's Definition of Done and the storefront rules in @_agenticdev/PROJECT.md before I merge.
```

---

## Step 5 - The next spec, the same two blocks

**Where:** the same terminal, after `/clear` and `/rename web-02`. Repeat it for every web spec up to and including the Products page.

**What it does:** `/start-spec` refuses if an earlier web spec is not Done, so the build order from the backlog is enforced. On this branch, read the add to cart code: the page sends a product id and a quantity, never a price.

```text
/auto-spec web 02

Use the spec-compliance-reviewer subagent to review this branch against the spec's Definition of Done and the storefront rules in @_agenticdev/PROJECT.md before I merge.
```
Continue to next spec development:

```text
/auto-spec web 03

Use the spec-compliance-reviewer subagent to review this branch against the spec's Definition of Done and the storefront rules in @_agenticdev/PROJECT.md before I merge.
```
Continue to next spec development:

```text
/auto-spec web 04

Use the spec-compliance-reviewer subagent to review this branch against the spec's Definition of Done and the storefront rules in @_agenticdev/PROJECT.md before I merge.
```
