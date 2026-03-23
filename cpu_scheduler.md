---
title: CPU Scheduler
layout: home
nav_order: 4
---

# CPU Scheduling Simulator

**Repository:** [https://github.com/walshyaw/CPU-Scheduler](https://github.com/walshyaw/CPU-Scheduler)

This project simulates four CPU scheduling algorithms (FCFS, Priority, SRTF, and Round Robin) written in C++. It reads process data from an input file and outputs per-time-unit PCB traces, Gantt charts, and average scheduling metrics for each algorithm. The simulator covers both non-preemptive and preemptive scheduling strategies for side-by-side comparison.

---

## How to Compile

```bash
g++ src/*.cpp -o scheduler
```

---

## How to Run

```bash
./scheduler
```

The program reads from `input.txt` and writes output to:

- `output_fcfs.txt`
- `output_srtf.txt`
- `output_priority.txt`
- `output_rr.txt`

Each output file contains a full per-time-unit PCB trace, a Gantt chart, and average scheduling metrics (wait time, turnaround time, response time).

---

## Input Format

The input file (`input.txt`) follows this format:

```
PID    Arrival    Burst    Priority
P1     0          5        2
P2     1          3        1
P3     2          1        3
P4     3          2        2
```

---

## Project Structure

```
project1_Walsh_1867402/
├── Part_A/
│   └── manual_analysis.pdf
└── Part_B/
    ├── src/
    │   ├── main.cpp
    │   ├── pcb.h / pcb.cpp
    │   ├── queue.h / queue.cpp
    │   ├── loadInput.h / loadInput.cpp
    │   ├── fcfs.h / fcfs.cpp
    │   ├── priority.h / priority.cpp
    │   ├── srtf.h / srtf.cpp
    │   ├── rr.h / rr.cpp
    │   └── outputGantt.h / outputGantt.cpp
    ├── input.txt
    ├── output_fcfs.txt
    ├── output_srtf.txt
    ├── output_priority.txt
    ├── output_rr.txt
    ├── README.md
    └── AI_USAGE.txt
```

---

## Algorithms Implemented

| Algorithm | Type | Selection Criterion |
|-----------|------|---------------------|
| FCFS | Non-preemptive | Arrival order |
| Priority | Non-preemptive | Lowest priority number (highest priority) |
| SRTF | Preemptive (event-based) | Shortest remaining time |
| Round Robin | Preemptive (time-based) | FIFO with time quantum |

---

## Statistics Computed

For each algorithm, the following are calculated per process and averaged:

- **Waiting Time:** `completion_time - arrival_time - burst_time`
- **Turnaround Time:** `completion_time - arrival_time`
- **Response Time:** `start_time - arrival_time`