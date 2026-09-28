# White-Box Test Suite: check_task()

Testers (pair): <name 1>, <name 2>
Date: <date>
File under test: `whitebox_target.py`, function `check_task(priority, hours)`

## 1. Control flow

List every decision point (every `if`) in the order it appears. A decision
with `and` / `or` still counts as one decision point for this lab.

| # | Line (approx.) | Condition | True branch leads to | False branch leads to |
|---|---|---|---|---|
| D1 | 2 | `priority is None or hours is None` | "Missing required field." | D2 |
| D2 | 4 | `not isinstance(priority, int)` | "Priority must be a whole number." | D3 |
| D3 | 7 | `priority < 1 or priority > 6` | "Priority must be between 1 and 5." | D4 |
| D4 | 10 | `hours <= 0` | "Estimated hours must be positive." | D5 |
| D5 | 13 | `priority >= 4 and hours > 20` | "High priority tasks cannot exceed 20 hours." | "Valid." |

## 2. Coverage target

- **Statement coverage**: every line of code executes at least once across your test suite.
- **Decision (branch) coverage**: every decision point takes both True and False at least once across your test suite.

Decision coverage is stronger. If you hit every branch, you also hit every
statement, so design for branch coverage first.




## 3. Test cases

Type: **Positive** = follows the intended success path. **Negative** =
should be rejected.
"Covers" = which decision(s) this case exercises, and whether it takes the
True or False branch, e.g. `D3-True`.

| ID | Type | priority | hours | Covers | Expected | Actual (per code) | Bug? |
|---|---|---|---|---|---|---|---|
| TC-1 | Positive | 3 | 5 | D1F,D2F,D3F,D4F,D5F | Valid | Valid | No |
| TC-2 | Negative | None | 5 | D1T | Reject: missing field | Reject: missing field | No |
| TC-3 | | | | | | | |

Add rows until every decision point has appeared as both True and False at
least once. Check off the table in section 1 as you go.

## 4. How to trace (no interpreter)

For each test case: start at the top of the function, evaluate each `if` in
order using your test data, follow the branch it takes, and stop at the
first `return` you reach. Write that return value as your Actual Result.
Compare it with your Expected Result (based on the business rule, not the
code) and mark Status as Pass or Fail.

## 5. Defects found

Where Actual and Expected disagree, that is a candidate defect. File it as
a GitHub issue using the bug report template, then list it here.

| Issue link | Linked test case | Short title | Severity | Priority |
|---|---|---|---|---|
| | | | | |
