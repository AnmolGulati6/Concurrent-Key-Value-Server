# Concurrent Key-Value Server

## Description
This project implements a concurrent Key-Value (KV) Store as a server in a client-server model. The server and client processes are multithreaded, utilizing shared memory for interprocess communication. A concurrent Ring Buffer and a shared Request-status Board in the shared memory facilitate request processing.

## Objectives
- Implement a thread-safe concurrent KV Store
- Implement a thread-safe Ring Buffer
- Understand interprocess communication through shared memory region
- Optimize synchronizing mechanisms for performance

## Project Details
### Client
The client submits PUT/GET requests to the server through the Ring Buffer.

### Server
The server contains a KV Store, serving requests fetched from the Ring Buffer. Upon completing a request, it updates completion status and response in the Request-status Board. 

### Ring Buffer
Facilitates communication between client and server. Supports concurrent PUT/GET requests.

### Request-status Board
Shared memory region for storing completion status and response of requests. Owned by client threads.

### KV Store
Implemented as a hashtable. Supports PUT and GET operations. Thread-safe implementation required.

## Starter Code and Implementation Details
- `common.h`: Contains type definitions and hash function.
- `ring_buffer.h`: Defines Ring Buffer operations.
- `client.c`: Implements multi-threaded client application.
- `Makefile`: Builds client and server.

### To Implement
- `ring_buffer.c`: Implement Ring Buffer operations.
- `kv_store.c`: Implement KV Store and server application.

## Best Practices
Consider using atomic operations for updating indices in the Ring Buffer and KV Store.

## Usage
- **Client**: `./client -h` for command line arguments.
- **Server**: `./server -n [num_threads] -s [hashtable_size]`

## Dependencies
- POSIX threads
- gcc

## License
This project is licensed under the [MIT License](LICENSE).
