# Lecture 20 - One Prompt per Permission Mode

Four prompts, one for each mode, run in order on `EShopClaude.ApiService`. Together they build a `/ping` endpoint with request logging, and the demo changes are restored at the end of the lecture.

---

## Step 1 - Manual: Claude asks before acting

**Where:** Manual mode, after one `Shift+Tab` from Auto.

**What it does:** Claude proposes the edit as a diff and waits. In the lecture we answer **No**, so nothing is written.

```text
Add an XML doc comment to the /weatherforecast endpoint in EShopClaude.ApiService/Program.cs.
```

---

## Step 2 - Accept Edits: files change freely

**Where:** Accept Edits mode, one more `Shift+Tab`.

**What it does:** Claude writes the endpoint directly, with no prompt. Review it afterwards in Source Control. A build command still asks.

```text
Add a GET /ping endpoint to EShopClaude.ApiService that returns the text "pong".
```

---

## Step 3 - Plan: read, propose, decide

**Where:** Plan mode, one more `Shift+Tab`.

**What it does:** Claude reads and writes a plan without touching a source file. Press `Ctrl+G` to edit the plan before approving it.

```text
Plan how to log every /ping request with the built-in ILogger, including the time of the request.
```

---

## Step 4 - Auto: implement and verify

**Where:** Auto mode, entered by approving the plan with "Yes, and use auto mode". Start the app in the `aspire` terminal first.

**What it does:** Claude finds the URL, runs `curl`, and shows `pong`. The dashboard shows the new log line.

```text
The app is running with aspire run. Find the ApiService URL, call GET /ping with curl and show me the response.
```
