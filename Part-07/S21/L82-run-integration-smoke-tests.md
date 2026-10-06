# Lecture 82 - Running the Integration Smoke Tests

Two prompts, one standard each. The subagent's contract says either standard can be asked for on its own, so we ask for them one at a time and read each report before moving on.

---

## Step 2 - The happy path, end to end

**Where:** a cleared, renamed `claude` session, with the application already running under `aspire run`.

**What it does:** One line per step of the buying journey, with the request, the status code and PASS or FAIL. Nothing is stopped or broken yet.

```text
Use the integration-smoke-tester subagent to walk the end to end buying journey in @_agenticdev/PROJECT.md against the running services, and report pass or fail for each step.
```

---

## Step 3 - Now break it on purpose

**Where:** the same session, straight after the happy-path report.

**What it does:** The agent stops services one at a time and checks the real behaviour against the failure-handling table in PROJECT.md. It restores everything it stopped and ends with the final system state.

```text
Now walk the full failure-handling table in @_agenticdev/PROJECT.md against the running services, and report which scenarios behave as documented.
```
