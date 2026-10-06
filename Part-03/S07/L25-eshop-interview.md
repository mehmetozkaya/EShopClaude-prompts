# Lecture 25 - The EShop Architecture Interview

The interview prompt. Claude interviews you with the `AskUserQuestion` tool about everything that is still open, and then writes your decisions to `_agenticdev/PROJECT.md`. Its four parts are Goal, Decided, Open, Output.

**Where:** the `claude` terminal, in **plan mode**, at the `EShopClaude` root. Press `Ctrl+G` to write it in a VS Code tab, save, close, then send.

**What it does:** Several `AskUserQuestion` rounds, then `_agenticdev/PROJECT.md`. **Your questions will differ**: Claude chooses its own questions, wording and order. The course's own answers are in the lecture script's Recommended Answers table.

```text
I want to build EShopClaude, a minimal e-commerce demo on top of the Aspire starter solution in src/.
The goal is to show agentic coding with microservices in a minimalist way: a small scope, few tokens and fast delivery.

Already decided:
- Services: three microservices, Catalog.Api, Basket.Api and Ordering.Api, and one Blazor web storefront, all orchestrated by Aspire.
- Databases: one PostgreSQL server with two separate databases, catalogdb for Catalog.Api and orderingdb for Ordering.Api. Basket.Api stores baskets in a Redis cache.
- Communication: synchronous HTTP calls through Aspire service discovery. No API gateway, no message broker and no event-driven communication.
- Use cases, each with a page in the storefront: list products, add to cart, checkout, and see the order.
- Checkout is owned and orchestrated by Basket.Api.
- Out of scope: login, identity, payments and deployment.

Interview me in detail using the AskUserQuestion tool about what is still open:
- which data each service owns, and what each API exposes
- what the basket stores versus what it looks up from Catalog.Api
- how a basket is identified without a login
- the checkout flow step by step, and what an order contains
- the storefront pages and the user journey between them
- what we should deliberately leave out to keep the demo minimal

Don't ask about the decisions above, and don't ask obvious questions. Dig into the parts I'd get wrong. Keep the design minimal: no retries, fallbacks or failure-handling patterns beyond the Aspire defaults.

Keep interviewing until we've covered everything, then write a complete project document to _agenticdev/PROJECT.md.
```
