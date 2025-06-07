# 🧠 CPU Scheduling Algorithms in C++

An educational simulation of various **CPU Scheduling Algorithms** implemented in C++ including support for analysis (`stats`) and visualization (`trace`). This project is ideal for operating systems coursework, OS simulators, and process scheduling studies.

---

## 📋 Algorithms Implemented

This simulator supports the following CPU scheduling algorithms:

| ID | Algorithm                               | Type            | Preemptive | Notes                               |
|----|-----------------------------------------|------------------|------------|-------------------------------------|
| 1  | **FCFS** (First Come First Serve)       | Non-Preemptive   | ❌         | Simple FIFO scheduling              |
| 2  | **RR-q** (Round Robin with quantum q)   | Preemptive       | ✅         | Fair CPU time-sharing               |
| 3  | **SPN** (Shortest Process Next)         | Non-Preemptive   | ❌         | Shortest burst process first        |
| 4  | **SRT** (Shortest Remaining Time)       | Preemptive       | ✅         | Preemptive version of SPN           |
| 5  | **HRRN** (Highest Response Ratio Next)  | Non-Preemptive   | ❌         | Reduces starvation                  |
| 6  | **FB-1** (Feedback, quantum = 1)        | Preemptive       | ✅         | Multilevel queue, all q = 1         |
| 7  | **FB-2i** (Feedback, quantum = 2^i)     | Preemptive       | ✅         | Multilevel queue with increasing q  |
| 8  | **Aging-q** (Aging, quantum = q)        | Preemptive       | ✅         | Prevents starvation by boosting     |

---

## 📥 Input Format

The simulator reads input from standard input or a file with the following structure:

```

<mode>
<algorithm list>
<last time unit>
<number of processes>
<process1>
<process2>
...
```

### Example:

```
stats
2-4
20
5
A,0,3
B,2,6
C,4,4
D,6,5
E,8,2
```

### Field Details:

* **Line 1**: `"trace"` or `"stats"` – whether to visualize or just show summary statistics.
* **Line 2**: List of scheduling algorithms (e.g., `1`, `2-4`, `5,3,6`)
* **Line 3**: Last time unit to simulate (e.g., `20`)
* **Line 4**: Number of processes (e.g., `5`)
* **Line 5 onward**: `ProcessName,ArrivalTime,BurstTime` (or `Priority` for Aging)

---

## 🧱 Project Structure

```
project-root/
├── main.cpp        # Core logic and algorithms
├── parser.h        # Input parser and shared data structures
├── makefile        # Build instructions
└── testcase/
    └── input.txt   # Example input file
```

---

## ⚙️ How to Build and Run

### ✅ Prerequisites

* **g++ Compiler** – Install via [MinGW](https://osdn.net/projects/mingw/releases/)
* **make** or **mingw32-make** – Available in MinGW or MSYS
* Add `C:\MinGW\bin` to your **System PATH**

### 🧑‍💻 Steps (on Windows using VS Code)

1. **Open the folder in VS Code**

2. **Ensure structure:**

   ```
   main.cpp
   parser.h
   makefile
   testcase/
     └── input.txt
   ```

3. **Build using terminal:**

   ```bash
   mingw32-make
   ```

4. **Run with input file:**

   ```bash
   scheduler.exe < testcase/input.txt
   ```

   Or in PowerShell:

   ```powershell
   Get-Content .\testcase\input.txt | .\scheduler.exe
   ```

---

## 🧪 Sample Test Inputs

### 🟢 FCFS:

```
stats
1
20
3
A,0,5
B,2,3
C,4,2
```

### 🔁 Round Robin (q = 2):

```
trace
2-2
15
3
P1,0,4
P2,1,5
P3,2,2
```

### 🧓 Aging (quantum = 1):

```
trace
8-1
30
3
X,0,3
Y,5,1
Z,10,2
```

---

## 📊 Output Formats

### ▶️ Trace Mode:

```
0 1 2 3 4 5 6 7 8 9 ...
--------------------------
A     |*|*|*| | |...
B     | |.|.|*|*|...
...
```

### 📈 Stats Mode:

```
FCFS
Process    |  A  |  B  |  C  |
Arrival    |  0  |  2  |  4  |
Service    |  5  |  3  |  2  | Mean
Finish     |  5  |  8  | 10  |-----
Turnaround |  5  |  6  |  6  | 5.67
NormTurn   | 1.00| 2.00| 3.00| 2.00
```

---

## 💡 Features

* Multiple CPU scheduling algorithms in one simulator
* Supports both **trace** (timeline) and **stats** (summary) modes
* Flexible support for quantum-based algorithms
* Aging logic to prevent starvation
* Well-structured and modular C++ code

---

## 🙌 Contributors

* **Harshita Lalwani** – Core developer, algorithm implementation, testing & documentation.

---



