# Non-Preemptive Job Scheduling - Minimizing Total Waiting Time

## Problem Description

This project tackles a non-preemptive scheduling problem where, at each decision point, the job combination minimizing the **total waiting time** must be selected.  
The objective is to guarantee:

- No deadlines missed (unless explicitly allowed for τ5).
- Minimum overall delay across all jobs.

This is **NOT EDF** (Earliest Deadline First) scheduling. Instead, it is a **global optimization** at each instant.

## Task Set

The tasks are characterized by (Computation Time, Period):

| Task | C | T |
|:----|--:|--:|
| τ1  | 2 | 10 |
| τ2  | 3 | 10 |
| τ3  | 2 | 20 |
| τ4  | 2 | 20 |
| τ5  | 2 | 40 |
| τ6  | 2 | 40 |
| τ7  | 3 | 80 |

## Methodology

At every scheduling decision:
- Identify all jobs ready for execution.
- Simulate all possible execution orders.
- Select the order that minimizes total waiting time, while ensuring deadlines are respected.

If no job is ready, the processor idles until the next arrival.

Two versions are produced:
- **Strict** (no deadline missed)
- **Relaxed** (τ5 allowed to miss deadline)

## Results

Generated Gantt charts:
- **Strict** scheduling: `figures/gantt_strict.png`
- **Relaxed** scheduling (τ5 may miss): `figures/gantt_task5_late.png`

## Assumptions

- Non-preemptive execution.
- Perfect knowledge of future job arrivals.
- The scheduling process is exhaustive and combinatorial.

## Complexity

At each decision point with \( n \) ready jobs, \( n! \) permutations are evaluated.  
Thus, the worst-case complexity is **O(n! per scheduling point)**.

## How to Run

1. Install requirements:
    ```
    pip install -r requirements.txt
    ```

2. Run the simulation:
    ```
    python code/scheduling.py
    ```

3. Output Gantt charts are saved under `/figures/`.

## Author

Raphaël Laupies
