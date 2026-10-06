# Lecture 87 - The Stop Hook Build Gate

A PreToolUse hook stops Claude before it acts. A Stop hook stops Claude from finishing. Four prompts: write it, watch it pass, break it on purpose, commit it.

---

## Step 2 - Dictate the build gate

**Where:** the `claude` session on `main`.

**What it does:** Claude writes `.claude/hooks/build-gate.sh`. The first rule has nothing to do with building: read `stop_hook_active` and exit immediately if it is true, otherwise the hook blocks its own retry forever.

```text
Create a Stop hook script at .claude/hooks/build-gate.sh for this repository.

It receives JSON on standard input, with the same jq or python3 reading approach as our other hooks.

Logic, in this order:
1. Read stop_hook_active. If it is true, exit 0 immediately, because we are already blocking and must not block forever.
2. Run: dotnet build src/EShopClaude.sln --nologo --verbosity quiet
3. If the build succeeds, exit 0 and print nothing at all.
4. If it fails, write the first ten lines of the build output that contain "error" to standard error, followed by one sentence saying the solution does not build and that these errors must be fixed before finishing. Then exit 2.

Keep it fast. No restore of NuGet packages beyond what dotnet build does itself, no tests, and no interactive prompts.
```

---

## Step 3 - Watch it pass

**Where:** the same session, after registering the hook with `/hooks`.

**What it does:** A small, safe change. The solution still builds, so the hook exits silently and Claude finishes normally. This is what a passing gate looks like: nothing.

```text
Add one line to the README in _agenticdev explaining that this repository now enforces its rules with hooks.
```

---

## Step 4 - Break it on purpose

**Where:** the same session. Type the comment so that it does not compile.

**What it does:** The build fails, so the Stop hook refuses to let Claude finish, shows the first error lines, and Claude fixes its own mistake without being asked.

```text
Add a one line comment at the top of Program.cs in src/EShopClaude.Ordering.Api saying that this service is a passive store.
```

---

## Step 6 - Commit the gate

**Where:** the same session, on `main`.

**What it does:** The last guardrail goes into the repository with the other two.

```text
Commit the build gate hook and the settings file on main, with a message saying that the Stop hook blocks finishing on a failed build, then push.
```
