---
name: spreadsheet-template-builder
description: Generate polished, formula-driven Excel/Google Sheets templates (budgets, invoices, calendars, trackers) with Python openpyxl, plus a PDF preview. Use when asked to create a spreadsheet template or tracker.
---
# Spreadsheet Template Builder

## Workflow
1. Clarify purpose, currency/locale, and the 3–5 numbers the user must see at a glance (these become the summary block).
2. Build with `openpyxl` in one script `build.py` so the template is reproducible.
3. Layout: Sheet 1 "Start Here" (how to use, 5 bullets) → main sheet → "Lists" sheet (categories for dropdowns, hidden or protected).
4. Formulas, never pasted values: `SUMIFS` by category/month, `IFERROR` wrappers, totals in a frozen top block. Use defined names (e.g. `Categories`, `TaxRate`) for readability.
5. Data validation dropdowns from `Lists`; conditional formatting (over budget → red fill, paid → green).
6. Styling: one accent color, 11pt body, bold headers with fill, thin borders, column widths set, freeze panes under headers, number formats with locale currency.
7. Print setup: fit to 1 page wide, landscape if > 8 columns, header/footer with sheet name.
8. Protect formula cells (unlocked inputs, locked formulas, no password by default).
9. Export a PDF preview (LibreOffice headless: `soffice --headless --convert-to pdf`).
10. Verify: open with `openpyxl` and assert formulas exist in summary cells; recalc with LibreOffice and check no `#REF!`/`#NAME?`.

## Google Sheets compatibility
Avoid XLOOKUP/LET/dynamic arrays unless user is Excel-365 only; prefer INDEX/MATCH and SUMIFS. Keep < 10 conditional-format rules per sheet.

## Report back
File list, sheet map, input cells vs formula cells, and screenshots/PDF path.
