---
author: Nekilc
title: Other language program compile and execute by rust
date: 2023-05-16
---

- Remote
- Limit time and memory

## Design
### Node
Designed into three nodes: Dispatch node(DNode), Compile node(CNode) and Exec node(ENode).

- DNode: Select idle CNode and ENode（OneByOne）, allocate compile task to them.  
- CNode: Execute compile command from different program language. If error callback DNode, otherwise allocate program to ENode according ENode ID of task metadata.
- ENode: Execute program. Send the result to DNode through callback.

### Node Status
CNode and ENode must send the status information to the dispatch node in real time.

Status information:
- NodeID
- Status
    - CNode status:
        - Idle
        - Compiling
    - ENode status:
        - Idle
        - Running


### Task Metadata
- TaskID
- Code
- CNodeID
- ENodeID

### Result
Error:
- Compile
- Running
- Memory
- Timeout

OK:
- Program running result
- Cost time
- Cost memory

## Unix Process

- fork: Create a child process
- setrlimit: Set current process resource limit

## Demo in rust

```rust

```


# Reference

- https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man2/setrlimit.2.html