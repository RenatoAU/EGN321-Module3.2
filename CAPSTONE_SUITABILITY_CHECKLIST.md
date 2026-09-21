# Capstone Suitability Checklist

Candidate: `INVENTORY_REORDER_SANITIZED_EXAMPLE.xlsx`

Scores: 0 = no / weak; 1 = partial; 2 = yes / strong. This assessment applies to the supplied example with its actual source disclosed.

| Criterion | Score | Reason |
|---|---:|---|
| Real user depends on the workbook | 0 | The materials describe fictional roles. No actual user has been identified. |
| Workbook performs meaningful logic | 2 | Thirty-six formulas connect stock, usage, lead time, thresholds and order decisions. |
| Wrong results could matter | 1 | Stockouts and excess purchases matter in the scenario; real operational consequences have not been established. |
| There is something worth improving | 2 | Specific concerns include a fixed safety-stock value, undocumented policy and missing validation. |
| Inputs and outputs can be identified | 2 | Six inventory records feed identifiable thresholds, flags and quantities. |
| Logic can be explained within this course | 2 | Multiplication, addition, comparison and conditional calculations are manageable. |
| Workbook can be safely sanitized | 2 | This copy already uses fictional data; inspection found no sensitive content. |
| A Python replacement could add value | 2 | Clear input rules, calculation functions and documented policies could improve repeatability. |
| Tests / validation would improve trust | 2 | Input changes, equality boundaries, invalid inputs and new-SKU handling are useful future checks. |
| Another user could eventually test the replacement | 0 | No real reviewer or handoff recipient has been confirmed. |

## Score
**Total: 15 / 20**

Suggested interpretation: 12–15 is probably workable; discuss scope with the instructor. A numerical score does not replace the requirement for an accepted source, permission and a real user or an expressly approved alternative.

## Decision
- [ ] Proceed
- [ ] Proceed with narrower scope
- [x] Ask instructor before proceeding
- [ ] Select another workbook

## Why
The calculations are suitable for a small capstone, but this classroom example does not by itself establish the required real-world connection. Confirm whether the instructor accepts it. If it is accepted, identify someone who can discuss the workflow and test the later tool, or follow the instructor's approved alternative. Otherwise select a real workbook, sanitize a copy and repeat the audit for that file.

## Proposed Direction
Keep the initial scope to one inventory list, input validation, reorder calculations and a clear recommendation report. Later work could add meaningful tests and short user instructions. Defer forecasting models, supplier integration, databases and a graphical interface unless a real user's requirements justify them. The safety-stock exception and purchasing rules must be resolved before defining correct behavior.
