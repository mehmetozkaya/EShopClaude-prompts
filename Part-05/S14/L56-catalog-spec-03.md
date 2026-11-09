# Lecture 56 - Developing Spec 03, and Spec 04

The same two sentences, then the lecture's real lesson: when the plan reveals a gap, you amend the **spec**, not the prompt. A prompt patch is forgotten; a spec change is not.

---

## Step 1 - Spec 03-list-products

**Where:** a cleared, renamed `claude` session in plan mode, on the spec's branch.

**What it does:** Third time, unchanged. Only the file name moves.

```text
Develop _agenticdev/microservices/catalog-api/03-list-products.md feature following the _agenticdev/WOW.md file.
This is a fresh session for microservices spec development.
```

---

## Step 2 - Spec 04-get-product

**Where:** a cleared, renamed `claude` session in plan mode, on the spec's branch.

**What it does:** Third time, unchanged. Only the file name moves.

```text
Develop _agenticdev/microservices/catalog-api/04-get-product.md feature following the _agenticdev/WOW.md file.
This is a fresh session for microservices spec development.
```

---

## Step 3 - Add to the spec's Scope

**Where:** typed by hand into `_agenticdev/microservices/catalog-api/03-product-endpoints.md`. This is not a prompt to send; it is a line added to the spec.

**What it does:** The gap the plan revealed: nothing in the spec asked for a way to exercise the endpoints.

```text
- Add an EShopClaude.Catalog.Api.http file and exercise every endpoint from it: the list, a real id, and an id that does not exist.
```

---

## Step 4 - Add to the spec's Definition of Done

**Where:** typed by hand into the same file, under Definition of Done.

**What it does:** The check that proves the new Scope line, written as something you can actually run.

```text
- All three requests in EShopClaude.Catalog.Api.http return the expected result against the running catalog-api: the full seeded list, one correct product, and 404 for an unknown id.
```

---

## Step 5 - Ask Claude to re-plan from the amended spec

**Where:** the `claude` session, after saving the spec.

**What it does:** Claude re-reads the file and updates its plan. The correction now lives in the repository, so the next session and the next teammate both see it.

```text
I edited the spec: it now also requires a .http file that exercises every endpoint, including an unknown id. Re-read @_agenticdev/microservices/catalog-api/03-product-endpoints.md and update your plan to match it.
```
