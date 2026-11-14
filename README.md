# Project Management Formula Library

A small Python library for common project-management calculations, including earned value management (EVM) metrics and schedule float.

The source package is included in [`project_management.zip`](project_management.zip).

## Use the formulas

After extracting the package and making its folder available on your Python path, import the functions:

```python
from project_management import (
    cost_performance_index,
    cost_variance,
    estimate_at_completion,
    estimate_to_complete,
    schedule_performance_index,
    schedule_variance,
    total_float,
)

earned_value = 80_000
actual_cost = 100_000
planned_value = 90_000
budget_at_completion = 120_000

cpi = cost_performance_index(earned_value, actual_cost)
print(cost_variance(earned_value, actual_cost))  # -20000
print(schedule_variance(earned_value, planned_value))  # -10000
print(cpi)  # 0.8
print(schedule_performance_index(earned_value, planned_value))  # 0.888...

eac = estimate_at_completion(budget_at_completion, cpi)
print(eac)  # 150000
print(estimate_to_complete(eac, actual_cost))  # 50000
```

## Available calculations

| Function | Calculation | Inputs |
| --- | --- | --- |
| `cost_variance(ev, ac)` | EV − AC | Earned value, actual cost |
| `schedule_variance(ev, pv)` | EV − PV | Earned value, planned value |
| `cost_performance_index(ev, ac)` | EV ÷ AC | Earned value, actual cost |
| `schedule_performance_index(ev, pv)` | EV ÷ PV | Earned value, planned value |
| `total_float(ls, es)` | LS − ES | Late start, early start |
| `free_float(ef, es)` | EF − ES | Early finish, early start |
| `estimate_at_completion(bac, cpi)` | BAC ÷ CPI | Budget at completion, cost performance index |
| `estimate_to_complete(eac, ac)` | EAC − AC | Estimate at completion, actual cost |

The CPI and SPI results are ratios: values above 1 indicate performance ahead of the corresponding cost or schedule measure; values below 1 indicate performance behind it. CPI, SPI, and EAC calculations reject a zero denominator with `ValueError`.

## Source

The implementation and package metadata are in `project_management.zip`.
