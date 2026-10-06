# Lecture 16 - The First Read-Only Prompt

The very first thing we ask Claude Code, straight after signing in. It only reads, so the repository stays exactly as it was.

**Where:** the `claude` session, at the `EShopClaude` root, right after `/status`.

**What it does:** Claude searches for the projects, reads `AppHost.cs` and `Extensions.cs`, and explains what the Aspire starter gives us. `git status` is clean afterwards.

```text
Read the AppHost and ServiceDefaults projects and tell me what this template gives me out of the box. List the resources defined in AppHost and what each one does. Don't change anything.
```
