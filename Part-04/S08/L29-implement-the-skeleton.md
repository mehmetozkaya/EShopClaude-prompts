# Lecture 29 - Implementing the Skeleton

Two prompts: the build that closes the loop, and the one to use when that build fails.

---

## Step 5 - Ask for the build, and for the output

**Where:** the `claude` session, in auto mode, after the plan is implemented.

**What it does:** The first two steps of THE VERIFICATION LADDER. Asking for the result is what turns a claim into evidence.

```text
run dotnet build on the solution and show me the result
```

---

## Step 5 - When the build fails

**Where:** the same session. Replace `<paste>` with the real error text.

**What it does:** Claude fixes the root cause and runs the build again, rather than stopping at a description of the failure.

```text
the build failed with this error: <paste>. fix it and run the build again
```
