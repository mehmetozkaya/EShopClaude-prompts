# Lecture 32 - Committing the Skeleton

Three prompts: check the work against the plan, let Claude write the commit, and push.

---

## Step 1 - Compare the work against the plan

**Where:** the `claude` session, before anything is staged.

**What it does:** Claude lists what the plan asked for and is missing, and what it changed that the plan never asked for. It changes nothing.

```text
Compare the changes in the working tree with the first step of _agenticdev/PLAN.md.
List anything in the plan that is not done, and anything you changed that the plan did not ask for. Don't change any code.
```

---

## Step 2 - Let Claude write the commit

**Where:** the same session, once the comparison is clean.

**What it does:** Claude reads the diff and drafts the message, and shows it to you before committing. Naming what goes in the subject and what goes in the body is what makes the message useful.

```text
Stage the skeleton changes and commit them on main with a descriptive message.

The subject line: short and in the imperative.
The body: which projects were added, how they are registered in the AppHost, and why the sample ApiService and the Weather page were removed.

Show me the message before you commit.
```

---

## Step 4 - Push

**Where:** the same session.

**What it does:** Two words, because Claude already knows the branch and the remote.

```text
push main
```
