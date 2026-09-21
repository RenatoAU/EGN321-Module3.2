# Initial Risk and Defect Inventory

Workbook: `INVENTORY_REORDER_SANITIZED_EXAMPLE.xlsx`  
Review date: September 21, 2026

These are investigation items. Formula text and missing workbook features are observed facts; their operational consequences and the intended business rules still require confirmation. No formulas were repaired.

| ID | Worksheet / Area | Observation | Why It May Be a Problem | Evidence Available Now | Priority |
|---|---|---|---|---|---|
| R-01 | `Reorder Logic!C7` | The formula adds a fixed 5 instead of referencing the safety-stock input. | Changing the input in `Inventory!F7` would not change this reorder point. An undocumented exception may be mistaken for a normal row. | `C7 = B7+5`; `Inventory!F7 = 5`. Neighboring C-column formulas reference Inventory column F. Current values agree, so no current numeric error is established. | High |
| R-02 | `Reorder Logic!F4:F9`; `Known Questions!A4:D4` | Order quantities use a fixed target of twice the reorder point; the safety-stock source is unknown. | The suggested order may not fit demand, storage limits or purchasing policy. The formula may be intentional, but its basis is undocumented. | `F4 = IF(E4="YES",C4*2-D4,0)`, repeated through row 9; the safety-stock question is marked “Unknown.” | High |
| R-03 | `Inventory!D3:E9`; `Known Questions!A5:C5` | The lead-time header says weeks, while the question about consistent units is answered “Mostly.” | An entry in days would overstate lead-time demand if treated as weeks. No particular row has been shown to contain days. | `E3 = Lead Time (weeks)`; `Known Questions!C5 = Mostly`. | High |
| R-04 | `Inventory!C4:F9`; formula outputs | No data-validation rules or numeric input guards were found. | Blank, text, negative or unsuitable fractional inputs may produce errors or misleading recommendations. Allowed values need a user-defined policy. | Worksheet XML contains no data-validation rules. Calculations multiply inputs directly. | High |
| R-05 | `Inventory!A4:G9`; `Reorder Logic!A4:F9` | Calculations cover six rows and use direct row references. No Excel Table or formulas beyond row 9 were found. | New SKUs may lack calculations unless a user extends the formulas correctly. | `Known Questions!A9:D9` asks what happens when a SKU is added; the answer is “Unknown.” | Medium |
| R-06 | `Inventory!C4:F9`; `Known Questions!A8:D8` | The workbook has no update date or usage averaging period. It says the updater is known but does not document the role. | Old stock counts or usage estimates may give a plausible recommendation that no longer fits current conditions. | The update-owner question is marked “Known,” with a follow-up to document the owner; no dated history is present. | Medium |

## Next Investigation
1. Ask whether R-01 is an approved exception. If the row should use its safety-stock input, check its response to a changed input in a disposable copy.
2. Confirm the buffer policy, target multiplier, review frequency, treatment of open orders and required quantity rounding.
3. Verify the source units for every lead-time value and the averaging period for usage.
4. Agree on valid inputs, then later test blanks, text, negative inputs and the equality boundary where On Hand equals Reorder Point.
5. Add a temporary seventh SKU in a disposable copy and check whether the workflow produces a complete recommendation.

## Current Evidence Limits
All 36 current formula results were checked against separate arithmetic and matching text/identifier values. The current data matched. This does not prove the purchasing policy is correct, validate every possible input, or establish a real user. These are initial audit checks, not the capstone's final tests.
