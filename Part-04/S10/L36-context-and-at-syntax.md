# Lecture 36 - Reading and Targeting Context

Four prompts: one open exploration to show what it costs, then three that name the files with `@` instead of letting Claude search for them.

---

## Step 2 - What an open exploration costs

**Where:** the `claude` session, after a first `/context`.

**What it does:** Claude searches, reads and answers. Run `/context` again afterwards to see what that one question cost.

```text
explain how the three API projects are wired into the AppHost, and what each one gets from ServiceDefaults
```

---

## Step 3 - Name the files with @

**Where:** a **cleared** session, so the comparison is fair.

**What it does:** The same kind of question, but Claude reads exactly two files instead of searching the solution.

```text
Does @src/EShopClaude.AppHost/AppHost.cs match the first step of @_agenticdev/PLAN.md? List anything that is missing. Don't change any code.
```

---

## Step 4 - A whole directory

**Where:** the same session.

**What it does:** `@` on a directory pulls in what is there, which is useful when a project is still nearly empty.

```text
What is in @src/EShopClaude.Ordering.Api/ right now?
```

---

## Step 4 - Two files at once

**Where:** the same session.

**What it does:** Two `@` references in one prompt, for a comparison that would otherwise cost a search.

```text
Compare the placeholder endpoints in @src/EShopClaude.Catalog.Api/Program.cs and @src/EShopClaude.Basket.Api/Program.cs. Are they consistent?
```
