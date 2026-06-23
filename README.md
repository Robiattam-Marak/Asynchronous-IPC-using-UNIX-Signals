# Asynchronous IPC using UNIX Signals

## Overview

This project implements a signal-driven process management system in C/C++ that demonstrates asynchronous inter-process communication (IPC) using POSIX signals. The system consists of a manager process responsible for creating, monitoring, suspending, resuming, and terminating child processes through signal-based communication.

The project explores fundamental operating-system concepts such as process creation, signal handling, process groups, job control, and asynchronous event-driven communication in UNIX environments.

---

## Key Features

### Asynchronous Signal-Based IPC

* Communication between processes using POSIX signals.
* Event-driven process control without shared memory or sockets.
* Asynchronous notification and state management.

### Process Lifecycle Management

* Dynamically create child processes.
* Monitor execution status of running jobs.
* Suspend and resume jobs using UNIX signals.
* Safely terminate selected processes.

### Job Control System

* Foreground process execution.
* Signal forwarding from terminal to active jobs.
* Process status tracking and management.

### Process Group Isolation

* Independent process groups using `setpgid()`.
* Proper signal delivery to target jobs.
* Separation between manager and worker processes.

### Resource Cleanup

* Prevent zombie and orphan processes.
* Graceful shutdown of all active jobs.
* Automatic process table maintenance.

---

## System Architecture

```text
Manager Process
      |
      +----> Job A
      |
      +----> Job B
      |
      +----> Job C
```

The manager acts as a controller process while each child job executes independently and communicates through UNIX signals.

---

## Supported Commands

| Command | Description                |
| ------- | -------------------------- |
| r       | Launch a new job           |
| p       | Display process table      |
| c       | Resume a suspended job     |
| k       | Kill a suspended job       |
| h       | Display help menu          |
| q       | Exit and clean up all jobs |

---

## Signal Usage

| Signal  | Purpose                    |
| ------- | -------------------------- |
| SIGINT  | Interrupt active job       |
| SIGTSTP | Suspend active job         |
| SIGCONT | Resume suspended job       |
| SIGKILL | Forcefully terminate job   |
| SIGCHLD | Detect child state changes |

---

## Technologies Used

* C / C++
* POSIX Signals
* Linux System Programming
* UNIX Process Management
* Process Groups
* Job Control Mechanisms

---

## Concepts Demonstrated

* Inter-Process Communication (IPC)
* Asynchronous Event Handling
* Signal-Based Synchronization
* Process Creation (`fork`)
* Signal Delivery (`kill`)
* Process Groups (`setpgid`)
* Child Monitoring (`waitpid`)
* UNIX Job Control

---

## Build Instructions

```bash
gcc -Wall -o job job.c
g++ -Wall -o manager manager.cpp
```

## Run

```bash
./manager
```

---

## Example Workflow

1. Start the manager process.
2. Create one or more jobs.
3. Suspend running jobs using `Ctrl + Z`.
4. Resume jobs using the manager interface.
5. Monitor job states through the process table.
6. Terminate jobs or exit cleanly.

---

## Applications

* Operating Systems coursework
* UNIX shell implementation
* Process supervision systems
* Signal handling demonstrations
* Systems programming education

---

## Future Improvements

* Non-blocking process monitoring
* Priority-based scheduling
* Background job execution
* Resource utilization tracking
* Event logging and auditing
* Interactive shell integration

---

## Learning Outcomes

This project provides practical experience with UNIX process management, asynchronous inter-process communication, POSIX signal handling, process synchronization, and operating-system level job control.
