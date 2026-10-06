# Lecture 94 - Connecting Claude to Chrome

Three prompts. The first is asked before the extension is installed, on purpose, so you see what Claude can and cannot do without it. Everything else typed here is a command (`/chrome`, `claude --chrome`).

---

## Step 1 - Ask before the extension exists

**Where:** the `claude` prompt, with no browser connection yet.

**What it does:** Claude cannot open a browser, and says so. Asking first is what makes the next two prompts meaningful.

```text
Open our storefront in the browser and tell me what is on the products page.
```

---

## Step 3 - Look, and do not touch

**Where:** the `claude` session with Chrome connected, and the storefront running under `aspire run`.

**What it does:** A screenshot and a description. The two `Do not` lines are the whole safety story of this lecture: a browser session can click things, so the first prompt you send it should not.

```text
Open our storefront products page in the browser.

Take a screenshot, then describe what you see. List the navigation items and the product names with their prices.

Do not click anything yet. Do not change any file.
```

---

## Step 4 - A second tab, and the honest limits

**Where:** the same session.

**What it does:** Claude drives the Aspire dashboard like any other page. This is also where the limits show: it reads what is on screen, so a filter it cannot find is a filter it cannot use.

```text
Open our Aspire dashboard in a second tab, go to the structured logs, and filter them to the storefront resource.

Tell me the three most recent lines. Do not change any file.
```
