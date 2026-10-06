# Lecture 37 - Fighting Context Rot

Four lines: two that fill the window on purpose, the focused `/compact`, and the question that proves what survived it.

---

## Step 1 - Fill the window, first question

**Where:** the `claude` session.

**What it does:** An open question, on purpose, to put real weight into the context window.

```text
explain what ServiceDefaults adds to each service
```

---

## Step 1 - Fill the window, second question

**Where:** the same session.

**What it does:** A second, unrelated question, so the window holds two different topics before we compact it.

```text
what does docker version tell us about the engine we need for Aspire?
```

---

## Step 2 - Compact with a focus

**Where:** the same session. This is a command with a prose argument, and the argument is the part that matters.

**What it does:** Without the focus, compaction keeps whatever it judges important. With it, you decide what survives.

```text
/compact focus on the AppHost wiring and the health checks
```

---

## Step 2 - Prove what survived

**Where:** the same session, straight after compacting.

**What it does:** Claude answers from the compacted summary, which shows that the focus was kept and the rest was dropped.

```text
which resources are registered in the AppHost, and what health check do they use?
```
