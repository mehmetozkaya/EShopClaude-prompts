# Lecture 54 - Verifying and Merging Spec 01

Two prompts. Claude closes the spec out by itself here, which is the trade-off this lecture ends on.

---

## Step 5 - Push

**Where:** the `claude` session, after the merge to `main`.

**What it does:** Claude has already committed, merged with `--no-ff`, marked the spec Done and deleted the branch, because WOW.md says so.

```text
proceed the rest of the cycle as you suggested. Follow the steps but change to place of step 3 and step 4, Mark it Done before merging.
Steps:
I followed the order you asked for, marking it Done before the merge:
1. Committed the implementation as ab2d16f.
2. Stopped the AppHost.
3. Set the status to Done in the spec and in _agenticdev/microservices/README.md, committed on the branch as 0781bc9.
4. Merged into main with --no-ff (0b2f3b4). The branch carried three commits: the spec, the implementation and Done.
5. Deleted the branch with git branch -d.
```

---

## Step 6 - Change the deal for the next spec

**Where:** the same session, at the end of the lecture.

**What it does:** One sentence that moves the human review *before* the commit instead of after it. It is the correction to the trade-off this lecture just demonstrated.

```text
For the next spec, stop after the verification step and wait for me before you commit or merge.
```
