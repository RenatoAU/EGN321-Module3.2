# Workbook Intake Form

## Student
- Name: Renato Jacinto
- Course / Section: EGN 321 / section to be confirmed
- Assignment: Module 3, Assignment 3.2
- Date: September 20, 2026

## Workbook
- Supplied file: `INVENTORY_REORDER_SANITIZED_EXAMPLE(1).xlsx`
- Copy included with this review: `INVENTORY_REORDER_SANITIZED_EXAMPLE.xlsx`
- Operational original: not supplied; this file is a classroom example.
- File type: `.xlsx`
- Worksheets: **4**, all visible.
- Formula cells: **36**, all in `Reorder Logic!A4:F9`.
- Inventory items: **6**, in `Inventory!A4:G9`.
- Macros: none found.
- External links: none found. Links between sheets are internal references.
- Protected sheets/workbook: no protection found.
- Lookup functions: none. The logic uses direct row references and `IF` formulas.
- Dependencies: inputs on `Inventory` feed `Reorder Logic`; no external data connection was found.

| Worksheet | Purpose | Formula cells |
|---|---|---:|
| Read Me | Scenario, privacy statement and purpose | 0 |
| Inventory | Fictional stock and demand inputs | 0 |
| Reorder Logic | Reorder calculations and recommendations | 36 |
| Known Questions | Open questions about assumptions and maintenance | 0 |

## Source
- Origin: the example supplied with the assignment materials. `README_STUDENT(1).md` identifies it as an example, and `Read Me!B8` says all names and values are fictional.
- Represented process: inventory purchasing for a small family business. The companion example analysis describes retail and service work.
- Permission to use as the student's final capstone candidate: **not confirmed**. Instructor acceptance of the example, or an eligible real source and permission, is still needed.
- Primary user in the scenario: store manager. Supporting user: purchasing assistant.
- Actual owner and user available for later feedback: **not yet identified**. No owner interview has been documented.

## Purpose
- Process: review inventory and prepare replenishment decisions.
- Question: which items have on-hand stock at or below their reorder point, and how much does the current rule recommend ordering?
- Decision: whether to reorder each SKU and what quantity to propose to the purchasing user.
- Frequency: weekly in the companion example analysis; actual operational frequency is unconfirmed.
- Workflow: update inventory inputs, review calculated thresholds and YES/NO flags, then prepare orders outside the workbook. This is the scenario workflow, not a verified observation of a real business.

## Inputs
All supplied values are fictional. The operational sources below are sources to confirm with a real user.

| Input | Meaning | Unit | Location and expected operational source |
|---|---|---|---|
| SKU and item | Identify the stocked item | Text identifiers | `Inventory!A4:B9`; product list |
| On Hand | Current available stock | Each | `Inventory!C4:C9`; stock count or inventory record |
| Weekly Use | Average consumption | Each per week | `Inventory!D4:D9`; usage records; averaging period undocumented |
| Lead Time | Time until replenishment arrives | Weeks in the header | `Inventory!E4:E9`; supplier information; consistency needs checking |
| Safety Stock | Buffer above lead-time demand | Each | `Inventory!F4:F9`; policy source undocumented |
| Unit | Item counting unit | `each` for all six rows | `Inventory!G4:G9`; product definition |

## Outputs

| Output | Meaning | Unit | Location and scenario user |
|---|---|---|---|
| Demand During Lead Time | Weekly use multiplied by lead time | Each | `Reorder Logic!B4:B9`; manager |
| Reorder Point | Lead-time demand plus buffer; row 7 uses a fixed 5 | Each | `Reorder Logic!C4:C9`; manager |
| Reorder? | YES when On Hand is less than or equal to Reorder Point | YES / NO | `Reorder Logic!E4:E9`; manager and purchasing assistant |
| Order Qty | If YES, twice the reorder point minus On Hand; otherwise zero | Each | `Reorder Logic!F4:F9`; purchasing assistant |

## Initial Concerns
- `Reorder Logic!C7` uses `=B7+5`; other rows reference the safety-stock input. Whether the exception is intentional is unknown.
- The multiplier 2 in order quantities and the source of safety stock are not justified in the workbook.
- `Inventory!E3` labels weeks, but `Known Questions!C5` answers “Mostly” to whether all lead times use weeks.
- No input-validation rules, update dates or automatic table expansion were found.
- Possible improvements: explicit input rules, documented units and policies, consistent calculations, tests and instructions for adding products.

## Candidate Decision
The provisional score is **15/20**. Discuss the source and scope with the instructor before treating this example as an approved capstone candidate. See the suitability checklist and audit notes for evidence and limitations.
