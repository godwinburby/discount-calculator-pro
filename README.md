
# Discount Calculator Pro

A powerful, fully client-side single-page web app for creating price quotes with complex discounts, tax calculations, per-product deductions, quote history management, price list import, and rich sharing capabilities. No server or build step required — just open `index.html` in a browser.

---

## Features

### 1. Product Management

- **Multi-Product Quotes** — Add any number of products, each with its own name, unit price, and quantity.
- **Drag-and-Drop Reordering** — Rearrange product rows by dragging.
- **Auto-fill Quote Name** — On a fresh quote, the quote name is automatically populated from the first product name and any memo text you type. Manual edits to the quote name input disable auto-fill.
- **Per-Product Deductions** — Toggle a deduction line on any product (e.g. "Less: Charger"). The deduction amount is subtracted after the discount is applied.

### 2. Flexible Discounts

Three discount modes per product, all with real-time calculation:

| Mode | Description |
|------|-------------|
| **% Disc** | Apply a percentage discount off the subtotal |
| **Amount** | Apply a fixed currency amount off the subtotal |
| **Final Price** | Specify the exact final price; the discount amount is derived automatically |

All discounts are capped so the final price never goes below zero or exceeds the subtotal.

### 3. Tax & Currency

- **Global Sales Tax / GST** — Set a percentage tax rate that applies to the net amount (after discounts and deductions). Clamped between 0% and 100%.
- **Currency Selector** — Switch between ₹ (INR), $ (USD), € (EUR), £ (GBP), and ¥ (JPY). All monetary values update in real time.
- **Quote Totals Summary** — Displays total subtotal, total savings, net amount before tax, tax amount, and grand total.

### 4. Quote Management (localStorage)

All quotes are saved in your browser's local storage — no account needed.

| Action | Behavior |
|--------|----------|
| **Save Quote** | Saves the current product list, tax rate, currency, and memo under the entered name. The screen clears after saving. |
| **Update Quote** | If you loaded a saved quote, the button reads "Update Quote" and overwrites the existing entry. |
| **Clear Quote** | Resets all fields and starts a fresh quote. |
| **Quote History** | Opens a modal listing all saved quotes. Search by name with **glob patterns** (e.g. `laptop*`, `nexia*micro`). |
| **Load Quote** | Click "Load" on any history entry to restore its products, tax, currency, and memo. |
| **Delete Quote** | Removes a saved quote from history. |
| **Duplicate Name Handling** | If a saved quote name already exists, the app auto-appends the memo text (or a numeric suffix if no memo) to avoid overwrites. |

### 5. Quote Comparison

Select 2–4 saved quotes from the history modal and view a side-by-side comparison grid. The grid shows:
- Total Subtotal
- Total Discount / Savings
- Net Amount (Before Tax)
- Tax Amount
- Grand Total

Each column displays the quote name and its tax rate for easy reference.

### 6. Price List Management

Upload a product catalog from CSV or Excel (`.xlsx`/`.xls`) and reuse products across multiple quotes.

| Action | Behavior |
|--------|----------|
| **Upload Price List** | Import products from a CSV or Excel file. The parser auto-detects name and price columns. |
| **My Price List** | Opens a modal with the saved products. Search by name with **glob patterns**. Edit prices inline or delete individual items. |
| **Load Selected** | Load only the checked products into the current quote. |
| **Load Filtered** | Load all products matching the current search filter into the current quote. |
| **Load All** | Load every product in the price list into the current quote. |
| **Clear All** | Two-tap confirmation to wipe the entire price list. |
| **Import Choice** | When uploading to an existing price list, choose whether to add to or replace the current list. |

### 7. Sharing & Export

| Action | Behavior |
|--------|----------|
| **Share via WhatsApp** | Opens WhatsApp with a richly formatted quote summary (markdown-style bold/italic). Includes product details, discounts, deductions, totals, tax, and memo. |
| **Copy Price Quote** | Copies the same formatted summary to your clipboard. Button gives a "Copied!" confirmation. |
| **Copy Share Link** | Encodes the full quote state (products, tax, currency, name, memo) into a shareable URL via base64. Open the link to restore the exact quote. |
| **Export All** | Downloads all saved quotes and the price list as a single JSON backup file. |
| **Import All** | Restores quotes and price list from a previously exported JSON file. Merges new entries and skips duplicates. |

### 8. User Feedback

Non-intrusive toast messages at the bottom of the screen confirm actions (save, load, delete, import, etc.) and show errors or warnings.
