# Lecture 96 - End-to-End Validation

Two prompts, and the first one is the lesson: write the test, not the walk-through. Every step carries its expected outcome, so Claude reports pass or fail instead of describing what it saw.

---

## Step 1 - The buyer journey, as a test

**Where:** the `claude` session with Chrome connected, and the whole application running under `aspire run`. Use `Ctrl+G` - this one is long.

**What it does:** Nine steps, each with an `Expected:` line. Step 3 is the one that finds real bugs: adding the same product twice should raise a quantity, not create a second line.

```text
Run our full buyer journey in the browser and check every expected outcome. Take a screenshot at each step.

1. Open the products page. Expected: at least three products, each with a name and a price.
2. Open one product and add it to the cart. Expected: the cart count rises by one.
3. Go back and add a different product to the cart twice. Expected: the cart holds two lines, and the second product has quantity two rather than two separate lines.
4. Open the cart. Expected: the product names and prices match what the product pages showed, each line total is the price times the quantity, and the cart total is the sum of the line totals.
5. Change the quantity of one line. Expected: that line total and the cart total both change.
6. Remove one line. Expected: it disappears and the cart total is recalculated.
7. Check out. Expected: a confirmation page showing an order number.
8. Open Orders from the navigation. Expected: the order we just placed is in the list, and opening it from there shows the same products and the same total.
9. Open the cart again. Expected: it is empty.

Report each step as pass or fail with the evidence you used. Do not change any code.
```

---

## Step 5 - One failure on purpose

**Where:** the same session, after stopping the Ordering service from the Aspire dashboard.

**What it does:** Three questions about the same failure: what the buyer sees, whether an order was created, and whether the cart survived. The third is the one that matters - a buyer who loses a full cart to a failed checkout will not come back.

```text
Ordering is stopped. In the browser, add a product to the cart and then try to check out.

Report three things:
1. What the buyer sees.
2. Whether an order was created.
3. Whether the cart still holds the item afterwards.

Do not change any code.
```
