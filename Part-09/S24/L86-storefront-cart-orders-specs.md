# Lecture 86 - Storefront Specs: Cart, Checkout and Orders

The same two blocks for every remaining web spec, then one read-only audit that asks for a quoted line for every yes. The numbers below assume web 03 (Cart page) and web 04 (Orders list and Order detail); use the numbers in your own status table.

---

## Step 1 - The orders specs

**Where:** the same terminal, after `/clear` and `/rename web-05`. Repeat it for every web spec that is left.

**What it does:** The first spec that calls Ordering adds the `ordering-api` reference to `webfrontend`. Both order pages only read, and the Order detail page is also the checkout confirmation.

```text
/auto-spec web 05

Use the spec-compliance-reviewer subagent to review this branch against the spec's Definition of Done and the storefront rules in @_agenticdev/PROJECT.md before I merge.
```

---

## Step 2 - The Place Order

**Where:** a `claude` session on `main`, after `/clear` and `/rename web-06`.

**What it does:** Read this spec slowly at gate one: prices come from the Basket snapshot, Place order is disabled while the cart is empty, and checkout is one call to Basket. The page never calls Ordering to create anything.

```text
/auto-spec web 06

Use the spec-compliance-reviewer subagent to review this branch against the spec's Definition of Done and the storefront rules in @_agenticdev/PROJECT.md before I merge.
```

Continue to next spec:

```text
/auto-spec web 07

Use the spec-compliance-reviewer subagent to review this branch against the spec's Definition of Done and the storefront rules in @_agenticdev/PROJECT.md before I merge.
```

---

## Step 4 - Prove it, line by line

**Where:** a `claude` session on `main`, after the last storefront spec is merged.

**What it does:** Four questions about the storefront rules, with a quoted file and line for every yes. A yes without a line is an opinion. Report only.

```text
Read the Razor pages, the typed clients and Program.cs under src/EShopClaude.Web.

Answer these four questions one by one, and quote the file and line for every yes:

1. Does any page send a price to a service, or ask Catalog for the price of a line that is already in the cart?
2. Does any page or client call the Ordering service to create something?
3. Does any page read a database directly?
4. Is a service address written anywhere in the Web project's code or configuration?

Report only. Do not change any file.
```
