# SmartELFLoader

A demand-paged ELF 32-bit executable loader implemented in C using virtual memory management, signal handling, and on-demand memory allocation.

## Overview

SmartELFLoader loads and executes compatible 32-bit ELF executables using lazy loading. Instead of loading program segments entirely upfront, it maps memory pages only when they are accessed during execution. By handling memory access faults dynamically, the loader fetches the required data from the executable, applies appropriate memory permissions, and allows execution to continue.

The project explores how executable loading works at a low level, demonstrating the interaction between ELF file structures, virtual memory, page faults, and operating system system calls.

## Features

- **ELF Parsing:** Reads and validates ELF headers and program headers to identify loadable segments.
- **Lazy Loading:** Loads executable pages on demand instead of loading entire segments upfront.
- **Page Fault Handling:** Uses a custom `SIGSEGV` handler to detect memory faults and trigger page loading.
- **Dynamic Memory Allocation:** Allocates 4 KB memory pages using `mmap()` when required.
- **Memory Protection:** Applies segment permissions such as read, write, and execute using `mprotect()`.
- **File-Backed Loading:** Uses `pread()` to load the required executable data into allocated pages.
- **Memory Statistics:** Tracks total page faults, page allocations, and internal fragmentation.
- **Resource Cleanup:** Releases allocated ELF headers and open file descriptors after execution.

## Build and Run

Build the project:

```bash
make clean && make
```

Run the loader with a compatible 32-bit ELF executable:

```bash
./loader test/fib
```

After execution, the loader reports the total page faults, page allocations, and internal fragmentation.

## Concepts Demonstrated

ELF file format, executable loading, demand paging, virtual memory management, page fault handling, memory protection, Unix system calls, and resource management.
