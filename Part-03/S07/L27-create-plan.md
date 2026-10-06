# Lecture 27 - Creating the Phased PLAN.md

Three prompts: the planning prompt, the one line added to the plan before approving it, and the commit and push.

---

## Step 2 - The planning prompt

**Where:** a **fresh** `claude` session in **plan mode**, so PLAN.md is built from the file and not from an old conversation. Write it with `Ctrl+G`.

**What it does:** An ordered, phased `_agenticdev/PLAN.md`, grouped per microservice, with the verification named for every step.

```text
Read _agenticdev/PROJECT.md and create an actionable, well-organized overall plan in _agenticdev/PLAN.md.

Order the plan the way we will build the EShop:
1. Project skeleton: the three microservice projects and the storefront, wired in the AppHost.
2. Data persistence design: PostgreSQL with catalogdb and orderingdb, pgAdmin, Redis, and the Catalog seed data.
3. The microservices one by one: Catalog.Api, then Ordering.Api, then Basket.Api.
4. Service communication: Basket.Api calling Catalog.Api and Ordering.Api, and the checkout flow.
5. The storefront pages for each use case.
6. End-to-end verification of the whole user journey.

Group the tasks per microservice. For each step, list the tasks, the projects it touches, and how we verify it: build, tests, aspire run, HTTP checks, traces or the browser. Keep each step small enough for its own feature branch. Don't write any code.
```

---

## Step 4 - The line you add to the plan

**Where:** the VS Code tab that `Ctrl+G` opens on Claude's plan, before you approve it. This is not a prompt to send; it is a line typed into the plan.

**What it does:** The approved plan starts by clearing the starter samples out of the way.

```text
- Remove the starter ApiService, the Weather and Counter samples and their test project; the Web project becomes the storefront.
```

---

## Step 6 - The commit and push

**Where:** the same session, after the plan is written.

**What it does:** Claude commits PLAN.md and pushes `main`, so both planning documents are on GitHub.

```text
commit _agenticdev/PLAN.md with a descriptive message and push main
```
