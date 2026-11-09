# Lecture 42 - Reviewing and Committing the Data Infrastructure

Two prompts: a review of Claude's own work against the plan, and the commit that closes the foundation.

---

## Step 2 - Let Claude review its own work

**Where:** the `claude` session, before anything is staged.

**What it does:** Three questions in one prompt: what is missing, what was added that nobody asked for, and what contradicts PROJECT.md. It changes nothing.

```text
Review the changes in the feature branch against the 2.1 data persistence step in _agenticdev/PLAN.md.

Report as a short list:
- anything in the step that is not done
- anything you changed that the step did not ask for
- anything that contradicts _agenticdev/PROJECT.md

Don't change any code.
```

---

## Step 5 - Commit, and say what is not there yet

**Where:** the same session, after the dashboard shows every resource healthy.

**What it does:** The message names what the step added *and* what it deliberately did not, so the next session starts from an honest history.

```text
Commit the changes on main with a descriptive message: the data persistence step of the plan — Redis, one PostgreSQL server with catalogdb and orderingdb, pgAdmin, and the Aspire client packages — and say explicitly that no service wiring or persistence code was added yet. Include the updated PLAN.md. Show me the message before you commit, then push main.
```
