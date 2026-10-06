# Lecture 86 - The PreToolUse Hooks

Nine blocks. Eight are prompts; the first is a line you type into the `/permissions` panel. Two hook scripts get written, registered and tested here, and the test is the point: a rule you have not watched refuse something is not a guardrail yet.

---

## Step 1 - The permissions entry we can write

**Where:** the `/permissions` panel, in the deny list. This is not a prompt to send; it is the line you type into the panel.

**What it does:** Permissions match a command pattern, so a force push can be denied outright. What they cannot do is look at the current branch, which is why the rest of the lecture exists.

```text
Bash(git push --force:*)
```

---

## Step 1 - The rule permissions cannot express

**Where:** the `claude` prompt, after adding the deny entry.

**What it does:** Refused by the permission rule. Now ask yourself the harder question: how would you deny a commit only when it is on `main` and only when it touches `src/`? Permissions cannot see that. A hook can.

```text
Force push main to origin.
```

---

## Step 2 - Dictate the protect-main script

**Where:** the `claude` session on `main`.

**What it does:** Claude writes `.claude/hooks/protect-main.sh`. Note the order of the logic: the cheap exits come first, and the deny is last. Note also the `jq` or `python3` fallback - never assume a tool is installed on a student's machine - and that the message is written as an instruction to follow, not as an error report.

```text
Create a PreToolUse hook script at .claude/hooks/protect-main.sh for this repository.

It receives the tool call as JSON on standard input. Read the command from .tool_input.command, using jq if it is available and falling back to python3 if it is not. Never assume jq is installed.

Logic, in this order:
1. If the command is not a git commit, exit 0 immediately.
2. Get the current branch with git rev-parse --abbrev-ref HEAD. If it is not main, exit 0.
3. Work out which files the commit would include: git diff --cached --name-only, and also git diff --name-only when the command uses -a or --all.
4. If none of those paths start with src/, exit 0. Our spec files and our .claude folder are allowed on main.
5. Otherwise write a message to standard error and exit 2.

The message must say that direct source code commits to main are not allowed in this repository, that a feature branch has to be created first, and that /start-spec <service> <NN> is the command for spec work. Write it as an instruction to follow, not as an error report.

Keep it fast and plain POSIX shell, with no network calls and no output at all on the success path.
```

---

## Step 3 - Register it

**Where:** the same session.

**What it does:** The hook is added to `.claude/settings.json` with the `Bash` matcher. Check it is really loaded with `/hooks` afterwards: a hook that is written but not registered does nothing at all.

```text
Add a PreToolUse hook to .claude/settings.json with the matcher Bash, running the command: bash .claude/hooks/protect-main.sh
```

---

## Step 4 - The refusal, watched live

**Where:** the same session, on `main`.

**What it does:** A source-code commit on `main`. The hook blocks it, and Claude reads the message and offers to create a feature branch instead. This is the moment the guardrail becomes real.

```text
Add a one line comment at the top of the Program.cs in src/EShopClaude.Catalog.Api saying that this service owns product data, then commit it.
```

---

## Step 4 - The commit that still works

**Where:** the same session, still on `main`.

**What it does:** Documentation only, so no path starts with `src/` and the hook exits silently. A guardrail that blocked everything would just be turned off.

```text
Add a note under the status table in _agenticdev/microservices/README.md saying that all ten specs are complete, then commit it on main.
```

---

## Step 5 - Dictate the protect-sensitive script

**Where:** the same session.

**What it does:** The second hook, much shorter: `.claude/settings.json` and any `.env` file are maintained by a person, not by the agent.

```text
Create a PreToolUse hook script at .claude/hooks/protect-sensitive.sh. It receives the tool call as JSON on standard input. Read the file path from .tool_input.file_path, with the same jq or python3 approach as the other script. If the path ends with .claude/settings.json, or the file name starts with .env, write a message to standard error saying this file is maintained by a person and not by the agent, and exit 2. Otherwise exit 0.
```

---

## Step 5 - And the file it now protects

**Where:** the same session, immediately after registering it.

**What it does:** Asked on purpose: this edit is exactly what the new hook refuses, so you make the change yourself. The agent can no longer widen its own permissions.

```text
Add a permissions allow entry for dotnet build to .claude/settings.json.
```

---

## Step 5 - Commit the guardrails

**Where:** the same session, on `main`.

**What it does:** Hooks live in the repository, so everyone who clones it gets the same rules. The scripts are not under `src/`, so protect-main lets this commit through.

```text
Commit the two hook scripts and the settings file on main, with a message saying what each guardrail enforces, then push.
```
