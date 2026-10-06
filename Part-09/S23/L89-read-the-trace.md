# Lecture 89 - Letting Claude Read the Trace

One prompt, and the only one in the course where you paste live telemetry into it. The Aspire dashboard shows you the spans; this asks whether they match the architecture we wrote down.

**Where:** the `claude` prompt. Replace `<paste the spans here>` with the span list copied from the trace detail view in the Aspire dashboard. Use `Ctrl+G` if the list is long.

**What it does:** Three questions about one add-to-cart request, each answerable from the spans alone: did Basket read from Catalog, did the write follow the lookup, and was Ordering involved at all. The trace is evidence the code review cannot give you, because it shows what actually ran.

```text
Here is the span list from one add-to-cart request in our Aspire dashboard.

<paste the spans here>

Check it against the service rules in _agenticdev/PROJECT.md and answer these three questions one by one:

1. Did Basket read the product from Catalog, rather than from its own store?
2. Did the cart write happen after the product lookup?
3. Was the Ordering service involved in this request at all?

Report only. Do not change any file.
```
