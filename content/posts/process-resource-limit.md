---
author: Nekilc
title: Process resource limit
date: 2023-05-16
---

int setrlimit(int resource, const struct rlimit *rlp);

     RLIMIT_CORE     The largest size (in bytes) core file that may be cre-ated. created.
                     ated.

     RLIMIT_CPU      The maximum amount of cpu time (in seconds) to be used by
                     each process.

     RLIMIT_DATA     The maximum size (in bytes) of the data segment for a
                     process; this defines how far a program may extend its
                     break with the sbrk(2) system call.

     RLIMIT_FSIZE    The largest size (in bytes) file that may be created.

     RLIMIT_MEMLOCK  The maximum size (in bytes) which a process may lock into
                     memory using the mlock(2) function.

     RLIMIT_NOFILE   The maximum number of open files for this process.

     RLIMIT_NPROC    The maximum number of simultaneous processes for this
                     user id.

     RLIMIT_RSS      The maximum size (in bytes) to which a process's resident
                     set size may grow.  This imposes a limit on the amount of
                     physical memory to be given to a process; if memory is
                     tight, the system will prefer to take memory from pro-cesses processes
                     cesses that are exceeding their declared resident set
                     size.

     RLIMIT_STACK    The maximum size (in bytes) of the stack segment for a
                     process; this defines how far a program's stack segment
                     may be extended.  Stack extension is performed automati-cally automatically
                     cally by the system.