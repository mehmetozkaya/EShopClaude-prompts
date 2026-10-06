# Lecture 41 - Planning and Implementing the Data Infrastructure

Four prompts: the develop prompt for the data persistence step, the nudge to continue it, the build, and the check on what Claude did *not* do.

---

## Step 1 - The develop prompt

**Where:** a fresh `claude` session in **plan mode**. Write it with `Ctrl+G`.

**What it does:** The out-of-scope list is the working part of this prompt: it names the persistence code Claude must not write yet, so the step stays small. Claude breaks the step into sub-steps, updates PLAN.md, and shows a plan.

```text
Develop the data persistence step of _agenticdev/PLAN.md — the AppHost infrastructure. Nothing after that step.

In scope:
- One PostgreSQL server resource in the AppHost, with two databases: catalogdb and orderingdb.
- pgAdmin attached to that PostgreSQL server.
- One Redis resource for Basket.Api. No data volume.
- The Aspire hosting packages the AppHost needs, and the Aspire client integration packages in the services that will use them: PostgreSQL with EF Core in Catalog.Api and Ordering.Api, Redis in Basket.Api. Packages only.

Out of scope, don't write any of it: DbContext classes, entities, seed data, Redis client code, AddNpgsqlDbContext or AddRedisClient calls, and any WithReference or WaitFor wiring between the API resources and these new resources.

First break this step into small sub-steps and update PLAN.md with them. Then tell me how you will verify the result, and show me your plan.
```

---

## Step 4 - Continue the step

**Where:** the same session, when Claude stops part-way through the sub-steps.

**What it does:** Claude picks up the remaining sub-steps from the plan it just wrote.

```text
continue with the remaining sub-steps of the data persistence step
```

---

## Step 5 - Ask for the build, and for the output

**Where:** the same session.

**What it does:** The same build prompt as Lecture 29. It is the first step of THE VERIFICATION LADDER, and it is asked for by name every time.

```text
run dotnet build on the solution and show me the result
```

---

## Step 5 - Check what Claude did not do

**Where:** the same session, after the build passes.

**What it does:** A green build only proves the code compiles. This asks Claude to confirm the boundary it was given: resources registered, no service code calling them yet.

```text
list every file you changed in this step, and confirm that no service code calls the new resources yet
```
