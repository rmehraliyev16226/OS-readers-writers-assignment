# Readers–Writers Problem with Load Balancing

## Overview

This project implements a simulation of the **Readers–Writers synchronization problem** with two additional requirements:

1. **Writer Priority** – Writers are given priority over readers when they intend to access the shared resource.
2. **Load Balancing** – Readers are distributed across multiple file replicas to balance access load.

The system simulates multiple **reader threads** and one **writer thread** accessing **three replicas of the same file**. Synchronization ensures safe coordination between readers and the writer.

---

# Features

- Concurrent reader threads
- A writer thread with priority over readers
- Load-balanced reading across three file replicas
- Thread-safe synchronization using **locks and condition variables**
- Detailed logging of all operations

---

# System Behavior

## Readers

- Multiple reader threads spawn at random intervals.
- Each reader reads from **one of the three file replicas**.
- Readers are distributed to the replica with the **fewest active readers**.

## Writer

- A single writer thread periodically attempts to write.
- The writer waits until **all readers finish** before writing.
- The writer updates **all three replicas simultaneously**.

---

## Synchronization Rules

The system guarantees:

- Multiple readers can read **simultaneously**
- Readers **cannot read while the writer is writing**
- Writers receive **priority when they request access**

---

# Files Generated

When the program runs, it creates an **`output` directory** containing:

```
output/
 ├── replica_1.txt
 ├── replica_2.txt
 ├── replica_3.txt
 └── log.txt
```

### Description

| File | Purpose |
|-----|------|
| `replica_1.txt` | First file replica |
| `replica_2.txt` | Second file replica |
| `replica_3.txt` | Third file replica |
| `log.txt` | Detailed log of all reader and writer operations |

Replica files store the **current version of the data**, while the log file records **every read and write event**.

---

# Requirements

- Python **3.8 or later**

Standard libraries used:

```
threading
time
random
os
```

No external dependencies are required.

---

# How to Run the Program

### 1️⃣ Open a terminal and go to the project directory

```bash
cd OS_Assignment
```

### 2️⃣ Run the program

```bash
python reader_writer.py
```

or

```bash
python3 reader_writer.py
```

### 3️⃣ Check the output

After execution, open the `output` folder:

```
output/
 ├── replica_1.txt
 ├── replica_2.txt
 ├── replica_3.txt
 └── log.txt
```

---

# Example Log Events

Example events recorded in the log:

```
[READER-ENTER] reader=3 replica=replica_2.txt
[READER-EXIT ] reader=3 replica=replica_2.txt

[WRITER-WAIT ] writer=1 wants to write version=1
[WRITER-START] writer=1 starts writing
[WRITER-END  ] writer=1 finished writing
```

### Event Meaning

| Event | Description |
|------|-------------|
| `READER-ENTER` | Reader starts reading |
| `READER-EXIT` | Reader finishes reading |
| `WRITER-WAIT` | Writer is waiting for readers |
| `WRITER-START` | Writer begins writing |
| `WRITER-END` | Writer finishes updating replicas |

These logs help visualize **thread synchronization** during execution.

---

# Author

**Student:** Ravan Mehraliyev  
**Course:** Principles of Operating Systems (CSCI-3510-20319)  
**Assignment:** Readers–Writers Synchronization with Load Balancing
