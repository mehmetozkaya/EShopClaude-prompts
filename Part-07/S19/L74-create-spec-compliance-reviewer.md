# Lecture 74 - Creating the spec-compliance-reviewer

One long prompt writes the whole subagent, and one short prompt proves it works. The contract is dictated, not improvised: a reviewer that judges every branch for the rest of the course has to be exact about what it reads, what it refuses to do, and the shape of its answer.

---

## Step 1 - Dictate the reviewer's contract

**Where:** a `claude` session on `main`, at the `EShopClaude` root.

**What it does:** Claude writes `.claude/agents/spec-compliance-reviewer.md`. Read the `tools:` line closely: `Read`, `Grep`, `Glob` and three scoped git verbs, with no `Edit` and no `Write`, so the reviewer physically cannot change the branch it is judging. The two standards are the spec file and the architecture rules in `PROJECT.md`, and the answer shape is fixed so every review in the course reads the same way.

```text
Create a Claude Code subagent in this repository at .claude/agents/spec-compliance-reviewer.md.

Its job is to review one finished feature branch and report findings. It never changes anything.

Frontmatter:
  name: spec-compliance-reviewer
  description: Reviews a finished feature branch against its spec and against the service rules in PROJECT.md. Use before merging a feature branch.
  tools: Read, Grep, Glob, Bash(git diff:*), Bash(git log:*), Bash(git status:*)
  model: inherit
Do not add a skills field.

The body is the agent's system prompt. Given a service, a spec number and a branch, it compares the branch diff against main using two standards.

Standard one is the spec file _agenticdev/microservices/<service>/<NN>-*.md:
  - report every line of its Definition of Done as met or not met
  - check that everything listed in Scope is present
  - check that nothing listed in Explicit non-goals has appeared

Standard two is the architecture rules in @_agenticdev/PROJECT.md:
  - Catalog is the sole source of product data
  - Ordering is a passive store and never calls another service
  - Basket snapshots the product name and price when an item is added, and never re-fetches them
  - at checkout the sequence is Basket calls Ordering, and Basket clears its cart only after Ordering confirms

Always answer in this shape:
  1. One word on the first line, PASS or FAIL.
  2. A section headed Spec violations.
  3. A section headed Architecture violations.
  4. A section headed Observations.
  Every finding names the file and the line, and the Definition of Done item or the rule it breaks.
  If a Definition of Done item cannot be checked by reading the code, say so explicitly and say why.

It must never write code, never propose a patch, and never suggest a library, a pattern or a refactor that the spec did not ask for.
If the working tree has uncommitted changes, refuse and ask for a commit first.
```

---

## Step 5 - Prove it on work that is already merged

**Where:** the same session, with a clean working tree.

**What it does:** The reviewer runs against the catalog-api spec 03 work we merged earlier. A known-good branch is the right first test: it tells you whether the agent reads the standards correctly before you trust it on new code.

```text
Use the spec-compliance-reviewer subagent on the merged catalog-api spec 03 work, against its spec file and the rules in @_agenticdev/PROJECT.md.
```
