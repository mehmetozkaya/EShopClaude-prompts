# Lecture 84 - Breaking the Storefront into Specs

The same breakdown we used for the microservices, run on the storefront step of the plan. Four prompts: the breakdown in plan mode, the coverage check in both directions, one source of truth in PLAN.md, and the commit. The number of storefront specs is decided by the sizing rules in WOW.md, so your backlog may have more or fewer specs than the recording.

---

## Step 2 - The breakdown prompt, in plan mode

**Where:** a `claude` session at the `EShopClaude` root, after `/clear` and `/rename web-backlog`, in **plan mode**. Write it with `Ctrl+G`.

**What it does:** Claude reads PLAN.md, PROJECT.md and the spec template, and proposes the storefront backlog as a table first: one spec per sub-feature under `_agenticdev/microservices/web/`, with its branch name, its dependencies and the use case and page it delivers. Nothing is created until you approve. Every spec carries the storefront rules as explicit non-goals, which is what the reviewer checks on each branch later.

```text
Read @_agenticdev/PLAN.md, @_agenticdev/PROJECT.md and @_agenticdev/templates/spec-template.md. Our way of working is already in your context.

Every microservice spec in _agenticdev/microservices/README.md is Done. The plan now continues with Step 5, the storefront pages, and it still describes the whole frontend as one step with four large sub-steps and their own branch names.

I want to build the storefront the same way we built the services: as a fourth service with its own spec backlog, one small sub-feature at a time, each on its own feature branch.

So break Step 5 into a spec backlog:
- Create _agenticdev/microservices/web/ for the EShopClaude.Web project, next to the three service folders.
- Inside it, one file per sub-feature, named NN-<short-name>.md, numbered in build order.
- Add one row per spec to the status table in _agenticdev/microservices/README.md, in the same shape as the service rows. The branch name follows our rule: feature/web-NN-<short-name>.

Size every spec by the rules in WOW.md. A web spec changes only the Web project, plus the webfrontend registration in the AppHost. Its pages may call the three services, but it never changes them. If two things cannot be verified separately, keep them in one spec and say why.

The webfrontend resource has no references yet. The first spec whose pages call a service adds the WithReference and WaitFor for that service, and no spec adds a reference it does not use.

Each spec's Depends on lists the earlier web specs it needs and the service specs whose endpoints its pages call.

In each spec file, fill only these sections from the template: the title line with Status: Not started, the Goal, Depends on, Scope as a short checklist, Explicit non-goals, and the Definition of Done. Leave the rest empty. We write each spec in full when we start its branch.

In every spec's Explicit non-goals, carry the storefront rules from PROJECT.md: prices come only from what Basket and Ordering return, so no page asks Catalog for a price again or sends a price to a service. Checkout is one call to Basket, and no page calls Ordering to create anything. No page reads a database. Nothing from the PROJECT.md "Out of scope" list is added.

Every Definition of Done line is a check I can run: dotnet build, aspire run with every resource healthy, and what I should see in the browser, in an HTTP request or in a dashboard trace.

Show me the proposed list as a table before you create anything, with the branch name for each spec, what it depends on, and the use case and page it delivers.
```

---

## Step 4 - Coverage in both directions

**Where:** the same session, after the web spec files exist.

**What it does:** Three lists: what Step 5 and the Storefront section ask for that no spec covers, what two specs both cover, and what a spec added that nobody asked for. It changes nothing.

```text
Compare @_agenticdev/microservices/web/ with Step 5 of @_agenticdev/PLAN.md and with the Storefront section of @_agenticdev/PROJECT.md.

Give me three lists:
1. Anything in Step 5 or in the Storefront section that no web spec covers.
2. Anything covered by more than one web spec.
3. Anything in a web spec that PLAN.md and PROJECT.md never asked for.

Don't change any files.
```

---

## Step 5 - One source of truth

**Where:** the same session.

**What it does:** Step 5 of PLAN.md becomes a pointer to the web folder with an `Owns:` line, the same shape Step 3 already has for the microservices. Read the diff before it is written.

```text
We now have the storefront work in two places: the detailed sub-steps in Step 5 of PLAN.md, and the specs in _agenticdev/microservices/web/.

Update PLAN.md so there is one source of truth, the same way Step 3 already works for the microservices:
- Keep Step 5 and its build order, and add one short "Owns:" line saying what the storefront is responsible for.
- Replace the detailed sub-steps with a pointer to _agenticdev/microservices/web/, and list the spec file names.
- Update the Step 5 rows of the step overview table to match.
- Don't change any other step.

Show me the diff before you write it.
```

---

## Step 5 - Commit and push

**Where:** the same session, after the PLAN.md change.

**What it does:** One commit on `main` with the backlog, the README rows and the plan change. The message explains the decision, not only the files.

```text
Commit everything on main: the storefront spec backlog in _agenticdev/microservices/web/, the new rows in the README status table and the PLAN.md change.

The message should explain the decision, not only the files: the storefront is built like a fourth service, so its detail moved from PLAN.md into one spec per sub-feature.

Show me the message before you commit, then push main.
```
