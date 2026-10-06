# Lecture 93 - Storefront Spec 02

The cart and checkout pages: the branch where it is easiest to break the architecture, because calculating a total in the page would be so much quicker. Three commands, then one audit prompt that checks we did not.

---

## Step 1 - The second spec

**Where:** a `claude` session on `main`.

**What it does:** The condition in the backlog fires here: web 02 depends on web 01, which is Done, so the skill proceeds.

```text
/new-spec web 02
```

---

## Step 2 - The branch

**Where:** the same session.

**What it does:** Branch, spec commit, plan.

```text
/start-spec web 02
```

---

## Step 2 - Implement, verify, review, merge

**Where:** the same session, on the branch.

**What it does:** Read the checkout diff slowly: the page calls Basket, and Basket does the work. The page never talks to Ordering.

```text
/finish-spec web 02
```

---

## Step 5 - Read what Claude wrote, in four places

**Where:** a `claude` session on `main`, after the merge.

**What it does:** Three questions, each needing a quoted line for every yes. This is the same audit the reviewer ran, done by you, on the merged result - because these three rules are the ones the storefront is most likely to break.

```text
Read the Razor pages and the API clients under src/EShopClaude.Web.

Answer these three questions one by one, and quote a line for every yes:

1. Does any page calculate a price or a total itself?
2. Does any page call the Ordering service to create something?
3. Does any page read a database directly?

Report only. Do not change any file.
```
