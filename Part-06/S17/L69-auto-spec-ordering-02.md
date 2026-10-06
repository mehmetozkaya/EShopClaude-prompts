# Lecture 69 - /auto-spec on Ordering 02

One line runs the whole loop. The second prompt is what happens when the loop finds a real bug: you fix the cause and re-run the *whole* Definition of Done, not just the failing check.

---

## Step 1 - One line, the whole loop

**Where:** a cleared, renamed `claude` session on `main`.

**What it does:** `/new-spec`, gate one, `/start-spec`, gate two, `/finish-spec`. Two human decisions in the middle, and nothing else typed.

```text
/auto-spec ordering-api 02
```

---

## Step 5 - Fix the cause, then re-check everything

**Where:** the same session, when a Definition of Done check fails.

**What it does:** The diagnosis is specific - the EF Core tracking cause, not the symptom - and the last sentence is the habit: run the whole Definition of Done again, not just the check that failed.

```text
The PUT is failing because new OrderLines are added through the navigation collection with an Id already set, so EF Core tracks them as Modified. Add new lines through db.OrderLines directly, with OrderId set explicitly. Then run the whole Definition of Done again, not just the PUT.
```
