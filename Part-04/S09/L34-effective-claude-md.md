# Lecture 34 - Writing an Effective CLAUDE.md

Four prompts: cut what Claude can read for itself, add what it can never know, prove the file is actually loaded, then commit and push.

---

## Step 2 - Cut what Claude can read itself

**Where:** the `claude` session, on the raw `/init` baseline.

**What it does:** The file loses the directory tree, the project list and the framework explanations, and keeps the commands, the conventions and the naming. Asking for the line count before and after makes the cut measurable.

```text
Rewrite CLAUDE.md so it only contains what you cannot read from the code itself.

Cut: the directory tree, the project list, package versions, and any general explanation of ASP.NET Core, Aspire or Blazor.

Keep and sharpen:
- The build and run commands: dotnet build on the solution, and aspire run from the src folder.
- Our conventions: net10.0, minimal APIs, and that every API project calls AddServiceDefaults() and MapDefaultEndpoints() in Program.cs.
- The project and resource naming: EShopClaude.<Name> for projects, and catalog-api, basket-api, ordering-api and webfrontend for the AppHost resources.

Use short sections with bullets, and tell me the line count before and after.
```

---

## Step 3 - Add what Claude can never know

**Where:** the same session.

**What it does:** The architecture rules and the workflow go in, taken from PROJECT.md and referenced rather than copied, with a hard limit on the file length.

```text
Add a short "Architecture rules" section and a short "Workflow" section to CLAUDE.md, from the decisions in _agenticdev/PROJECT.md.

Architecture rules:
- Three microservices, Catalog.Api, Basket.Api and Ordering.Api, plus a Blazor storefront, orchestrated by the Aspire AppHost.
- Database per service: one PostgreSQL server with catalogdb for Catalog and orderingdb for Ordering, and Redis for Basket. No service reads another service's database.
- Checkout is owned and orchestrated by Basket.Api.
- Services talk over synchronous HTTP through Aspire service discovery. No API gateway, no message broker, no events.
- Out of scope: login, identity, payments and deployment. Don't propose them.

Workflow:
- Foundation work is committed on main. From the first spec, one spec is one sub-feature on one feature branch, merged with a pull request.
- Before committing, the solution must build and aspire run must start every resource healthy.
- The detailed scope lives in _agenticdev/PROJECT.md and the build order in _agenticdev/PLAN.md. Reference them, don't copy them.

Keep both sections short, as bullets, and keep the whole file under 200 lines.
```

---

## Step 4 - Prove it is loaded

**Where:** a **cleared** session, so nothing but project memory can answer.

**What it does:** If Claude answers correctly without reading a file, CLAUDE.md is really in context. That is the test, not the fact that the file exists.

```text
Which database does Ordering.Api use, and who owns the checkout flow? Answer from project memory, and don't read any files.
```

---

## Step 5 - Commit and push

**Where:** the same session.

**What it does:** The message says what was cut and what was added, so the history explains the rewrite.

```text
commit CLAUDE.md with a descriptive message explaining what was cut and what was added, then push main
```
