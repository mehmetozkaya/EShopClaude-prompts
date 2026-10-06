# Lecture 23 - Everyday Workflow Prompts

Five prompts covering the everyday jobs: asking about a codebase, reading a screenshot, and fixing a real bug through the full Execution Loop.

---

## Step 1 - Start broad

**Where:** a fresh `claude` session at the `EShopClaude` root.

**What it does:** Claude reads the solution and summarises the AppHost, the service defaults, the API and the web frontend.

```text
give me an overview of this codebase
```

---

## Step 1 - Then go specific

**Where:** the same session, straight after the overview.

**What it does:** The answer names real files: `Weather.razor`, `WeatherApiClient.cs`, the `apiservice` address and `WithReference` in `AppHost.cs`.

```text
trace what happens when the Weather page loads its data: from the Blazor page to the API, and how service discovery resolves apiservice
```

---

## Step 2 - Explain a screenshot

**Where:** the `claude` prompt, straight after pasting the image with `Alt+V` on Windows, or `Ctrl+V` on macOS and Linux.

**What it does:** Claude connects what it sees in the image with what it knows about the code, and names the stopped `apiservice`.

```text
What does this screenshot show, and why is it happening in this solution?
```

---

## Step 3 - Explore and plan a bug fix

**Where:** **Plan mode**, after stopping the app.

**What it does:** Claude finds the conversion in two places and plans a failing test first, then the root-cause fix, then the tests and the build. The degree signs are reproduced exactly as typed.

```text
TemperatureF is sometimes off by one degree: for example, 100°C shows 211°F instead of 212°F. Find every place this conversion is calculated. Plan the fix: first add an xUnit test project that reproduces the bug with a failing test, then fix the root cause, then run all tests and the build.
```

---

## Step 5 - Let Claude write the commit

**Where:** the `claude` prompt, after reviewing the diff in Source Control.

**What it does:** Claude reads the diff and writes the message itself, saying what was wrong, how it was fixed, and that a test now covers it.

```text
commit these changes with a descriptive message
```
