# Critical Path

## Network Schedule Calculations

### Forward Pass

| **Task** | **ES calculation** | **ES** | **EF calculation** | **EF** |
| --- | --- | --- | --- | --- |
| T1 | Start of project | 1 | 1 + 2 - 1 | 2 |
| T2 | EF(T1) + 1 = 2 + 1 | 3 | 3 + 3 - 1 | 5 |
| T3 | EF(T1) + 1 = 2 + 1 | 3 | 3 + 3 - 1 | 5 |
| T4 | max(EF T2, EF T3) + 1 = max(5, 5) + 1 | 6 | 6 + 4 - 1 | 9 |
| T5 | EF(T4) + 1 = 9 + 1 | 10 | 10 + 6 - 1 | 15 |
| T6 | EF(T4) + 1 = 9 + 1 | 10 | 10 + 4 - 1 | 13 |
| T7 | max(EF T5, EF T6) + 1 = max(15, 13) + 1 | 16 | 16 + 5 - 1 | 20 |
| T8 | EF(T7) + 1 = 20 + 1 | 21 | 21 + 3 - 1 | 23 |
| T9 | EF(T8) + 1 = 23 + 1 | 24 | 24 + 5 - 1 | 28 |
| T10 | EF(T9) + 1 = 28 + 1 | 29 | 29 + 3 - 1 | 31 |

### Backward Pass

| **Task** | **LF calculation** | **LF** | **LS calculation** | **LS** |
| --- | --- | --- | --- | --- |
| T10 | Equal to its EF | 31 | 31 - 3 + 1 | 29 |
| T9 | LS(T10) - 1 = 29 - 1 | 28 | 28 - 5 + 1 | 24 |
| T8 | LS(T9) - 1 = 24 - 1 | 23 | 23 - 3 + 1 | 21 |
| T7 | LS(T8) - 1 = 21 - 1 | 20 | 20 - 5 + 1 | 16 |
| T6 | LS(T7) - 1 = 16 - 1 | 15 | 15 - 4 + 1 | 12 |
| T5 | LS(T7) - 1 = 16 - 1 | 15 | 15 - 6 + 1 | 10 |
| T4 | min(LS T5, LS T6) - 1 = min(10, 12) - 1 | 9 | 9 - 4 + 1 | 6 |
| T3 | LS(T4) - 1 = 6 - 1 | 5 | 5 - 3 + 1 | 3 |
| T2 | LS(T4) - 1 = 6 - 1 | 5 | 5 - 3 + 1 | 3 |
| T1 | min(LS T2, LS T3) - 1 = min(3, 3) - 1 | 2 | 2 - 2 + 1 | 1 |

### Slack

| **Task** | **LS - ES** | **Slack** |
| --- | --- | --- |
| T1 | 1 - 1 | 0 |
| T2 | 3 - 3 | 0 |
| T3 | 3 - 3 | 0 |
| T4 | 6 - 6 | 0 |
| T5 | 10 - 10 | 0 |
| T6 | 12 - 10 | **2** |
| T7 | 16 - 16 | 0 |
| T8 | 21 - 21 | 0 |
| T9 | 24 - 24 | 0 |
| T10 | 29 - 29 | 0 |

## Critical Path

**Critical path 1:** T1 → T2 → T4 → T5 → T7 → T8 → T9 → T10

**Critical path 2:** T1 → T3 → T4 → T5 → T7 → T8 → T9 → T10

## Expected Project Duration

31 days

## Explanation

All the activities in these pathways have a slack time of 0, delaying any of these activities would delay the completion of the project.
