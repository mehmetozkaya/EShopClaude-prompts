# Lecture 92 - Storefront Spec 01

One framing prompt and two commands. The framing prompt is the pattern worth copying: it names the one file to work from, the conventions to follow, and the review that will happen before the merge - all before any code exists.

---

## Step 1 - The framing prompt

**Where:** a cleared `claude` session on `main`.

**What it does:** Three sentences that set the boundary of the work. `Work only from` the spec file is the important one: it stops Claude from inventing pages the spec never asked for.

```text
We are about to build the storefront spec web 01 on its own feature branch.

Work only from _agenticdev/microservices/web/01-storefront-shell-and-product-pages.md. Follow the conventions in CLAUDE.md and the cycle in _agenticdev/WOW.md.

When the work is finished, use the spec-compliance-reviewer to review this branch against the spec's Definition of Done and the storefront rules in PROJECT.md, before I merge.
```

---

## Step 2 - The branch

**Where:** the same session.

**What it does:** The preflight passes, the branch is named from the rule, and the spec file is committed alone as the first commit.

```text
/start-spec web 01
```

---

## Step 3 - Implement, verify, review, merge

**Where:** the same session, on the storefront branch.

**What it does:** The two diffs worth reading properly are the Razor pages and the API clients. Everything the storefront shows has to come from a service call.

```text
/finish-spec web 01
```
