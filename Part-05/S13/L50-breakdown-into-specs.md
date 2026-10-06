# Lecture 50 - Breaking the Microservices into Specs

One long prompt. It turns one enormous plan step into a spec backlog: one folder per service, one file per sub-feature, and a status table.

**Where:** a cleared, renamed `claude` session in **plan mode**. The way of working is already in context through CLAUDE.md, which is why the prompt can say "size every spec by the rules in WOW.md" instead of repeating them.

**What it does:** Claude proposes the whole backlog as a table first, with branch names and dependencies, and creates nothing until you approve it. Note that each spec is only stubbed here: the full spec is written when its branch starts.

```text
Read @_agenticdev/PLAN.md and @_agenticdev/templates/spec-template.md. Our way of working is already in your context.

We finished the skeleton step and the data infrastructure step. The plan now continues with the microservices, one by one, and the first section develops the whole Catalog service in a single step: entities, persistence, AppHost wiring, seed data and endpoints together.

I don't want to develop a whole microservice at once. I want spec-driven development: small sub-features, one at a time, each on its own feature branch.

So break the microservices step into a spec backlog:
- Create _agenticdev/microservices/ with one folder per service: catalog-api, ordering-api and basket-api.
- Inside each folder, one file per sub-feature, named NN-<short-name>.md, numbered in build order.
- Also create _agenticdev/microservices/README.md with a status table: service, spec, branch name and status, for every spec.

Size every spec by the rules in WOW.md. A spec changes one service, delivers one behaviour, and can be verified on its own branch. If two things cannot be verified separately, keep them in one spec and say why.

In each spec file, fill only these sections from the template: the title line with Status: Not started, the Goal, Depends on, Scope as a short checklist, Explicit non-goals, and the Definition of Done. Leave the rest empty. We write each spec in full when we start its branch.

Show me the proposed list as a table before you create anything, with the branch name for each spec and what it depends on.
```
