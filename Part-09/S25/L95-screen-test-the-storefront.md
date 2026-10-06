# Lecture 95 - Screen-Testing the Storefront

The browser walk that produces a report, the backlog row that turns the report into work, and the autopilot run that fixes it. Asking for a report and forbidding the fix is the point: findings and changes are two separate decisions.

---

## Step 1 - Ask for a report, and forbid the fix

**Where:** the `claude` session with Chrome connected, and the storefront running.

**What it does:** Claude walks the buying journey as a first-time buyer, screenshots each step, and returns a numbered list of what looks broken. The three closing lines stop it from quietly fixing anything.

```text
Walk our storefront in the browser as a first-time buyer.

Open the products page, open one product, add it to the cart, then open the cart page. Take a screenshot at each step.

Then give me a numbered report of what looks broken, confusing or unfinished, one line each.

Do not change any code. Do not fix anything. I only want the report.
```

---

## Step 4 - The backlog row

**Where:** `_agenticdev/microservices/README.md`. This is not a prompt to send; it is the row `/auto-spec` reads.

**What it does:** web 03 depends on web 02, so the skill will refuse if the cart and checkout pages are not Done.

```text
| web | 03 | storefront-ux-fixes | Not started | web 02 |
```

---

## Step 4 - Hand the report to the autopilot

**Where:** a `claude` session on `main`, in the same window as the browser report.

**What it does:** The whole spec-to-merge cycle in one command. The report is still in context, which is why the next block can point at it.

```text
/auto-spec web 03
```

---

## Step 4 - Scope it to the report

**Where:** the same session, sent immediately after the command, while `/new-spec` is asking its questions.

**What it does:** This is what keeps a UX pass from becoming a redesign. Defects in pages we already have go into scope; everything else goes into the explicit non-goals with a reason; and the Definition of Done is the same browser walk, run again.

```text
Base the scope on the browser report above, and only on the items that are defects in pages we already have.

Every finding we are not doing goes into the explicit non-goals with a one-line reason.

The Definition of Done is the same browser walk we just ran, coming back with those items resolved.
```
