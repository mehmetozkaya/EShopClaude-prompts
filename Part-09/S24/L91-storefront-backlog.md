# Lecture 91 - Extending the Backlog to the Storefront

Four blocks: the backlog rows the skill reads, the command that creates the spec, the correction at gate one, and the same command run again.

---

## Step 2 - The backlog rows

**Where:** `_agenticdev/microservices/README.md`, appended to the status table. This is not a prompt to send; it is the paperwork `/new-spec` reads.

**What it does:** Two rows in the same five-column shape as every service row. The `Depends on` column is what makes `/start-spec` refuse later if you try to build web 02 before web 01 is done.

```text
| web | 01 | storefront-shell-and-product-pages | Not started | catalog-api 01-03 |
| web | 02 | cart-and-checkout-pages | Not started | web 01 |
```

---

## Step 3 - Create the first storefront spec

**Where:** a `claude` session on `main`.

**What it does:** The skill reads the new backlog row and interviews you about the storefront pages, exactly as it did for the services.

```text
/new-spec web 01
```

---

## Step 4 - Two changes at gate one

**Where:** the same session, after reading the completed spec yourself.

**What it does:** Both corrections are architectural, not cosmetic. The AppHost registration is what lets the pages resolve `catalog-api` at all, and the non-goals are written in the exact words the reviewer checks on the branch.

```text
Two changes to this spec.

The scope must include registering the Web project in the AppHost with a reference to catalog-api and a wait on it. Without that the product pages cannot resolve the service.

The explicit non-goals must say, in these words, that no page calculates a price or a total, no page reads a database, and no page calls Ordering to create anything. Those are the rules our reviewer checks on the branch.
```

---

## Step 4 - Re-open the spec and confirm

**Where:** the same session, after the changes are applied.

**What it does:** Path B of the skill: it reports the spec section by section so you can see the corrections landed, and it never overwrites the file.

```text
/new-spec web 01
```
