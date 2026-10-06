# Lecture 28 - Planning the Skeleton

Two prompts: the develop prompt that turns the first step of PLAN.md into a plan, and the one line added to that plan before approving it.

---

## Step 3 - The planning prompt

**Where:** a **fresh** `claude` session in **plan mode**, at the `EShopClaude` root. Write it with `Ctrl+G`.

**What it does:** Claude reads the plan and the solution, then proposes how to build the skeleton and nothing after it. Note the last line: it has to tell you how it will verify the result *before* it shows the plan.

```text
Read _agenticdev/PLAN.md and the existing solution in src/.

Develop the first step of the plan: the distributed microservices skeleton. Nothing after it.

In scope:
- Create three ASP.NET Core Web API projects, EShopClaude.Catalog.Api, EShopClaude.Basket.Api and EShopClaude.Ordering.Api, on net10.0, and add them to the solution.
- Each project references EShopClaude.ServiceDefaults and calls AddServiceDefaults() and MapDefaultEndpoints(), like the existing sample project does.
- Each project exposes one placeholder endpoint: GET / returns "<Service> API is running.".
- Register the three services in AppHost.cs as project resources with an HTTP health check on /health.
- Remove the sample EShopClaude.ApiService and everything in EShopClaude.Web that depends on it, including the Weather page and its client.

Out of scope, don't touch: databases, Redis, pgAdmin, service-to-service references, domain models and real endpoints.

Tell me how you will verify the result before you show me the plan.
```

---

## Step 5 - The line you add to the plan

**Where:** the VS Code tab that `Ctrl+G` opens on Claude's plan, before you approve it. This is not a prompt to send; it is a line typed into the plan.

**What it does:** The approved plan also clears the Weather nav link, which Claude's first pass missed.

```text
Also remove the nav link to the Weather page in EShopClaude.Web/Components/Layout/NavMenu.razor.
```
