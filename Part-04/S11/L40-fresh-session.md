# Lecture 40 - Loading Only What the Next Step Needs

One prompt. The rest of this lecture is `/clear`, `/rename` and `/context`.

**Where:** a cleared, renamed `claude` session, before any planning starts.

**What it does:** Two `@` references load exactly the plan and the AppHost. The last sentence stops Claude from running ahead into the plan.

```text
Read @_agenticdev/PLAN.md and @src/EShopClaude.AppHost/AppHost.cs.
In one short list: which resources does the data persistence step add, and which projects does it touch? Don't change anything, and don't plan yet.
```
