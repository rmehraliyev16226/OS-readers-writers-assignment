# Readers--Writers Problem with Load Balancing

## Overview

This project implements a simulation of the Readers--Writers
synchronization problem with two additional requirements:

1.  Writer Priority -- Writers are given priority over readers when they
    intend to access the shared resource.
2.  Load Balancing -- Readers are distributed across multiple file
    replicas to balance access load.

The system simulates multiple reader threads and one writer thread
accessing three replicas of the same file. Synchronization ensures safe
coordination between readers and the writer.

---

## Features

- Concurrent reader threads
- A writer thread with priority over readers
- Load-balanced reading across three file replicas
- Thread-safe synchronization using locks and condition variables
- Detailed logging of all operations

---

## System Behavior

### Readers

- Multiple reader threads spawn at random intervals.
- Each reader reads from one of the three file replicas.
- Readers are distributed to the replica with the fewest active
  readers.

### Writer

- A single writer thread periodically attempts to write.
- The writer waits until all readers finish before writing.
- The writer updates all three replicas simultaneously.

### Synchronization

The system ensures: - Multiple readers can read simultaneously. -
Readers cannot read while the writer is writing. - The writer gets
priority once it intends to write.

---

## Files Generated

When the program runs, it creates an output directory containing:

replica_1.txt\
replica_2.txt\
replica_3.txt\
log.txt

Replica files store the current version of the data.\
The log file records all reader and writer operations.

---

## Requirements

Python 3.8 or later

Standard libraries used: - threading - time - random - os

---

## How to Run the Program

Step 1: Open a terminal and go to the project directory

cd OS_Assignment

Step 2: Run the program

python reader_writer.py

or

python3 reader_writer.py

Step 3: After execution, check the output folder for:

replica_1.txt\
replica_2.txt\
replica_3.txt\
log.txt

---

## Example Log Events

READER-ENTER -- a reader begins reading a replica\
READER-EXIT -- a reader finishes reading\
WRITER-WAIT -- the writer requests access\
WRITER-START -- the writer begins writing\
WRITER-END -- the writer finishes updating replicas

These events help visualize synchronization between readers and the
writer.

---

## Author

Student: Ravan Mehraliyev
Course: Princpls of Operating Systems (CSCI-3510 - 20319) - Assigment 1
Assignment: Readers--Writers Synchronization with Load Balancing
