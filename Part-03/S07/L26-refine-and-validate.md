# Lecture 26 - Refining and Validating PROJECT.md

Three prompts: one precise refinement, one scope validation that changes nothing, and the commit.

---

## Step 2 - The refinement prompt

**Where:** a fresh `claude` session, after reading PROJECT.md yourself.

**What it does:** Claude changes only the sections these clarifications affect, so the rest of the document is left alone.

```text
Update _agenticdev/PROJECT.md with these clarifications:

Checkout:
- Basket.Api owns the checkout logic. A POST checkout request to Basket.Api reads the basket, sends a create-order request to Ordering.Api, and deletes the basket after the order is created.
- If Basket.Api needs product data, it calls Catalog.Api.
- Ordering.Api stays simple and only exposes CRUD operations for orders.

Data:
- Catalog.Api and Ordering.Api use one PostgreSQL server with two dedicated databases: catalogdb and orderingdb.
- Basket.Api uses Redis for storage.
- Catalog.Api seeds sample products when it starts.
- Add pgAdmin to the PostgreSQL server, so we can see the data in both databases.

Change only the sections these clarifications affect.
```

---

## Step 4 - The validation prompt

**Where:** the same session, after the refinement is applied.

**What it does:** Claude reports the problems as a short list and changes nothing, so you decide which ones to act on.

```text
Read _agenticdev/PROJECT.md and validate the project scope:
- Does every use case have one owning service and one storefront page?
- Does every service own its data, with no service reading another service's database?
- Does anything contradict the decisions, the out-of-scope list or the minimal approach?
- Are there open questions or vague statements left?
Report the problems you find as a short list. Don't change the file.
```

---

## Step 5 - The commit

**Where:** the same session.

**What it does:** Claude reads the diff and writes the commit message itself.

```text
commit _agenticdev/PROJECT.md with a descriptive message
```
