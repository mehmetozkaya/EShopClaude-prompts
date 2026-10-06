# Lecture 75 - The First Independent Review

One prompt, handed to a subagent in a deliberately empty window. Everything else typed in this lecture is a command (`/clear`, `/rename`, `/context`, `/code-review`), and commands live in the lecture's On-Screen Action blocks, not in this library.

**Where:** a cleared, renamed `claude` session, after `/context` has shown you how empty the window is.

**What it does:** The subagent reviews the ordering-api spec 01 and 02 work with fresh context of its own. Name both the Definition of Done and the service rules: two standards, so the review is measured against what we wrote down rather than against Claude's taste.

```text
Use the spec-compliance-reviewer subagent to review the ordering-api spec 01 and 02 work on main against their spec files' Definition of Done and against the Ordering rules in @_agenticdev/PROJECT.md.
```
