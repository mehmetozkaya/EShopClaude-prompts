# Lecture 88 - Auditing the AppHost Wiring

Two prompts. The first is an audit written as five statements, so the answer is checkable rather than reassuring. The second is the decision not to fix what it found.

---

## Step 3 - The integration pass

**Where:** a `claude` session on `main`, with all ten service specs merged.

**What it does:** Five statements, pass or fail, each with the line that proves it. Ask for statements, not for an opinion: "does this look right?" gets you a paragraph, and a numbered list gets you evidence. `Report only. Do not change any file.` keeps it read-only.

```text
Read src/EShopClaude.AppHost/AppHost.cs and audit the wiring against the service rules in _agenticdev/PROJECT.md.

Answer these five statements one by one, with pass or fail, and quote the line you used for each:

1. catalog-api references its own database and nothing else.
2. ordering-api references its own database and nothing else.
3. basket-api references Redis, catalog-api and ordering-api, and waits for all three.
4. webfrontend references catalog-api, basket-api and ordering-api, and is the only resource with external HTTP endpoints.
5. Every service project calls AddServiceDefaults and MapDefaultEndpoints.

Report only. Do not change any file.
```

---

## Step 4 - The gap we are not closing today

**Where:** the same session, after the audit reports the storefront wiring as missing.

**What it does:** Claude offers to fix it. We say no, and say why: the storefront is not specified yet, so that wiring belongs in its own spec. Finding a gap and closing it are two different decisions.

```text
Do not change it. The storefront is a feature we have not specified yet, so that wiring belongs in its own spec.
```
