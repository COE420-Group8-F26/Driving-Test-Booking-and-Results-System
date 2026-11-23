
# Critical Path

## Network Schedule Calculations

All durations and scheduling calculations are in working days.

### Forward Pass

| **Task** | **ES calculation** | **ES** | **EF calculation** | **EF** |
| --- | --- | --- | --- | --- |
| T1 | Start of project | 1 | 1 + 6 - 1 | 6 |
| T2 | EF(T1) + 1 = 6 + 1 | 7 | 7 + 9 - 1 | 15 |
| T3 | EF(T1) + 1 = 6 + 1 | 7 | 7 + 9 - 1 | 15 |
| T4 | max(EF T2, EF T3) + 1 = max(15, 15) + 1 | 16 | 16 + 12 - 1 | 27 |
| T5 | EF(T4) + 1 = 27 + 1 | 28 | 28 + 18 - 1 | 45 |
| T6 | EF(T4) + 1 = 27 + 1 | 28 | 28 + 12 - 1 | 39 |
| T7 | max(EF T5, EF T6) + 1 = max(45, 39) + 1 | 46 | 46 + 15 - 1 | 60 |
| T8 | EF(T7) + 1 = 60 + 1 | 61 | 61 + 9 - 1 | 69 |
| T9 | EF(T8) + 1 = 69 + 1 | 70 | 70 + 15 - 1 | 84 |
| T10 | EF(T9) + 1 = 84 + 1 | 85 | 85 + 12 - 1 | 96 |

### Backward Pass

| **Task** | **LF calculation** | **LF** | **LS calculation** | **LS** |
| --- | --- | --- | --- | --- |
| T10 | Equal to its EF | 96 | 96 - 12 + 1 | 85 |
| T9 | LS(T10) - 1 = 85 - 1 | 84 | 84 - 15 + 1 | 70 |
| T8 | LS(T9) - 1 = 70 - 1 | 69 | 69 - 9 + 1 | 61 |
| T7 | LS(T8) - 1 = 61 - 1 | 60 | 60 - 15 + 1 | 46 |
| T6 | LS(T7) - 1 = 46 - 1 | 45 | 45 - 12 + 1 | 34 |
| T5 | LS(T7) - 1 = 46 - 1 | 45 | 45 - 18 + 1 | 28 |
| T4 | min(LS T5, LS T6) - 1 = min(28, 34) - 1 | 27 | 27 - 12 + 1 | 16 |
| T3 | LS(T4) - 1 = 16 - 1 | 15 | 15 - 9 + 1 | 7 |
| T2 | LS(T4) - 1 = 16 - 1 | 15 | 15 - 9 + 1 | 7 |
| T1 | min(LS T2, LS T3) - 1 = min(7, 7) - 1 | 6 | 6 - 6 + 1 | 1 |

### Slack

| **Task** | **LS - ES** | **Slack** |
| --- | --- | --- |
| T1 | 1 - 1 | 0 |
| T2 | 7 - 7 | 0 |
| T3 | 7 - 7 | 0 |
| T4 | 16 - 16 | 0 |
| T5 | 28 - 28 | 0 |
| T6 | 34 - 28 | **6** |
| T7 | 46 - 46 | 0 |
| T8 | 61 - 61 | 0 |
| T9 | 70 - 70 | 0 |
| T10 | 85 - 85 | 0 |

## Critical Path

**Critical path 1:** T1 → T2 → T4 → T5 → T7 → T8 → T9 → T10

**Critical path 2:** T1 → T3 → T4 → T5 → T7 → T8 → T9 → T10

## Expected Project Duration

96 working days (approximately 4.8 months, assuming 20 working days per month).

## Explanation

All activities on the two critical paths have zero slack, meaning that delaying any of these activities would delay the completion of the project. T6 has 6 working days of slack and can be delayed by up to 6 working days without affecting the overall project duration.
