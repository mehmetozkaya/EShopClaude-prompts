# Lecture 51 - Reviewing the Spec Backlog

Six prompts: check the backlog in both directions, fix what the review found, remove the duplicated source of truth, feed the lessons back into WOW.md, and commit.

---

## Step 2 - Coverage, both directions

**Where:** the `claude` session, with the backlog created.

**What it does:** Three lists: what no spec covers, what two specs cover twice, and what a spec invented. Asking in both directions is what catches a gap.

```text
Compare @_agenticdev/microservices/ with the microservices sections of @_agenticdev/PLAN.md and with @_agenticdev/PROJECT.md.

Give me three lists:
1. Anything in PLAN.md's microservice sections that no spec covers.
2. Anything covered by more than one spec.
3. Anything in a spec that PLAN.md and PROJECT.md never asked for.

Don't change any files.
```

---

## Step 3 - Split a spec that does two things

**Where:** the same session.

**What it does:** The rule is quoted back to Claude, and the renumbering and the README update are part of the same change.

```text
Spec catalog-api/02 has two behaviours: seeding the data and the product endpoints. Our rule in WOW.md is one behaviour per spec, and these two have different checks.

Split it into 02-seed-data.md and 03-product-endpoints.md, renumber the rest of the catalog specs, and update _agenticdev/microservices/README.md so the table matches the files.
```

---

## Step 3 - Replace a vague Definition of Done

**Where:** the same session.

**What it does:** "The endpoints work" is replaced by the exact requests, the status codes and what you should see.

```text
The Definition of Done in catalog-api/03 says the endpoints work. Replace it with the checks I can run: the exact requests, the expected status codes, and what I should see in the response.
```

---

## Step 4 - One source of truth

**Where:** the same session.

**What it does:** PLAN.md stops repeating the specs and points at them instead. The finished steps are left alone, because their detail is history.

```text
We now have the same information in two places: the detailed checklists in PLAN.md's microservice sections, and the specs in _agenticdev/microservices/.

Update PLAN.md so there is one source of truth:
- Keep the build order, and keep one short "Owns:" line for each service saying what that service is responsible for.
- Replace each detailed checklist with a pointer to that service's spec folder, and list the spec file names.
- Don't change the skeleton step or the data infrastructure step. Those are finished, and their detail is history.

Show me the diff before you write it.
```

---

## Step 5 - Feed the review back into WOW.md

**Where:** the same session.

**What it does:** The three rules this review exposed go into the way of working, so the next backlog does not repeat the same mistakes.

```text
Add to WOW.md the rules this review exposed:
- A spec's Definition of Done lists checks I can run, with the exact command or request and the expected result. "It works" is not a definition of done.
- _agenticdev/microservices/README.md is updated in the same change as any spec that is added, split or renamed.
- Specs are numbered per service in build order. Once a spec is merged, its number never changes.

Keep them short, put them under the existing headings, and keep the file under 120 lines.
```

---

## Step 6 - Commit and push

**Where:** the same session.

**What it does:** The message explains the decision, not only the files: the microservice detail moved out of PLAN.md into one spec per sub-feature.

```text
Commit everything on main: the microservices spec backlog, the README status table, the PLAN.md changes and the WOW.md rules.

The message should explain the decision, not only the files: the microservice detail moved from PLAN.md into one spec per sub-feature, so there is one source of truth per feature.

Show me the message before you commit, then push main.
```
