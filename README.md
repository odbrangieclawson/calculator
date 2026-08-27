# Profit Calculator

A single-page utility for working out what you actually keep on a sale, after
cost of goods and every fee that comes off the top.

No build step, no dependencies, no server. Open `index.html` in a browser.

## What it does

Enter the cost of goods, the selling price and a quantity, then add any fees.
Each fee row carries a name, an amount, and — the part that matters — **how it
is charged**:

| Fee type | Charged as | Typical use |
| --- | --- | --- |
| `% of selling price` | percentage of revenue | marketplace commission, card processing, ad spend |
| `% of cost of goods` | percentage of COGS | import duty, handling |
| `flat, per unit` | fixed amount × quantity | shipping, packaging, per-transaction fees |
| `flat, one-time` | fixed amount for the whole batch | listing fee, sample order |

The receipt on the right updates as you type: revenue, cost of goods, itemised
fees, net profit, and a bar showing how each sale splits three ways.

Four figures underneath:

- **Profit per unit** — net profit ÷ quantity
- **Profit margin** — net profit as a share of revenue
- **Markup** — net profit as a share of *total* cost (goods **and** fees)
- **Break-even price** — the per-unit price at which profit is exactly zero

## Break-even

Percentage fees compound on the selling price, so break-even is not simply
`cost + fees`. Solving for the price `P` where profit is zero:

```
Q·P·(1 − Σ%price) = Q·C·(1 + Σ%cost) + Q·flatPerUnit + flatOneTime
```

where `Q` is quantity and `C` is the unit cost of goods. When percentage-of-price
fees reach 100%, no price breaks even and the field shows `—` rather than a
misleading number.

## Other bits

- 17 currencies, formatted with `Intl.NumberFormat`
- Light and dark themes, following the system setting until you override it
- **Copy summary** puts a plain-text breakdown on the clipboard
- Inputs persist in `localStorage` between visits

Everything is calculated in the browser. Nothing is sent anywhere.

## Files

```
index.html   the entire application — markup, styles and logic
```
