# Lecture 54 - Verifying and Merging Spec 01

Two prompts. Claude closes the spec out by itself here, which is the trade-off this lecture ends on.

---

## Step 5 - Push

**Where:** the `claude` session, after the merge to `main`.

**What it does:** Claude has already committed, merged with `--no-ff`, marked the spec Done and deleted the branch, because WOW.md says so.

```text
push main
```

---

## Step 6 - Change the deal for the next spec

**Where:** the same session, at the end of the lecture.

**What it does:** One sentence that moves the human review *before* the commit instead of after it. It is the correction to the trade-off this lecture just demonstrated.

```text
For the next spec, stop after the verification step and wait for me before you commit or merge.
```
