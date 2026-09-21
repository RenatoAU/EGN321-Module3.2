# Workbook Audit Notes

Source: the supplied `INVENTORY_REORDER_SANITIZED_EXAMPLE(1).xlsx`. The included copy has identical bytes and a filename without `(1)`. Review date: September 20, 2026.

## Inspection Performed
All four sheets, their cell values and formulas, workbook relationships and file-package contents were inspected. All sheets are visible. No hidden rows or columns, macros, external links, data connections, named ranges, comment/note objects, embedded files, document-property parts, Excel Tables or sheet/workbook protection were found. The Comment column contains ordinary cell text, which was also reviewed.

The 36 formula cells are in `Reorder Logic!A4:F9`. No data-validation rules were found. `Read Me!B8` states that names and values are fictional; inspection found no personal, regulated or security-sensitive content. This is a content review, not an ownership or permission certification.

## Current Calculation Checks
The supplied workbook was imported and recalculated in a spreadsheet engine without saving changes. All 36 formula results were compared with separately computed numeric results and expected text/identifier values. They matched. This verifies the present formulas for the six supplied records, not the correctness of the business policy or every possible input. Desktop Excel interaction was not tested.

All quantities below are in `each`.

| SKU | Lead-time demand | Reorder point | On hand | Reorder? | Order quantity |
|---|---:|---:|---:|---|---:|
| P-100 | 24 | 34 | 38 | NO | 0 |
| P-110 | 24 | 30 | 24 | YES | 36 |
| P-120 | 12 | 16 | 9 | YES | 23 |
| P-130 | 10 | 15 | 22 | NO | 0 |
| P-140 | 10 | 13 | 7 | YES | 19 |
| P-150 | 20 | 28 | 42 | NO | 0 |

### Worked Example for P-110
`Inventory!C5:F5` contains 24 on hand, 8 each/week, 3 weeks and 6 safety-stock units.

- Lead-time demand: 8 each/week × 3 weeks = 24 each.
- Reorder point: 24 + 6 = 30 each.
- Decision: 24 ≤ 30, so YES.
- Order quantity under the current rule: 2 × 30 − 24 = 36 each.

### Why C7 Deserves Investigation
`Reorder Logic!C7` contains `=B7+5`. Since `Inventory!F7` currently equals 5, both the fixed formula and a formula linked to the input give 15 each. This establishes a different formula pattern, not a current numeric error.

For a later investigation, consider changing safety stock to 12 in a disposable copy. If the intended rule uses the input, the reorder point would become 10 + 12 = 22. With 22 on hand, the equality condition would recommend YES and 22 each. The current formula would remain at 15 and recommend NO. This is a conditional arithmetic illustration; that workbook edit was not performed, and the intended policy still needs confirmation.

### Avoid an Unsupported Negative-Quantity Claim
For valid nonnegative inputs, if stock H is at or below reorder point R, the current quantity is 2R − H, which is at least R and therefore nonnegative. The current six rows do not show a negative quantity. Invalid inputs and policy choices still deserve later investigation.

## Source References
- `README_STUDENT(1).md`, Example: identifies the supplied workbook as a demonstration.
- Workbook `Read Me!B3:B10`: purpose, scenario, users and privacy statement.
- Workbook `Inventory!A3:G9` and `Reorder Logic!A3:G9`: inputs and formulas.
- Workbook `Known Questions!A3:D9`: unresolved assumptions and workflow questions.
- `EXAMPLE_ONE_PAGE_ANALYSIS(1).docx`, Who Depends on It: weekly review and scenario roles.
- `ASSIGNMENT_SPEC(1).md` and the detailed guide: required source, privacy, analysis and suitability review.


