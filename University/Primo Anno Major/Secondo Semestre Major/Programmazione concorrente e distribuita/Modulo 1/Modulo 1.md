# Modulo 1
## General Definition of Concurrency
> In computer science, concurrency is a property of systems in which several computational processes are executing at the same time, and potentially interacting with each other.

### Common Aspects
- Systems with multiple activities or processes whose execution overlaps in time
- activities can have some kind of dependencies, therefore can interact
## Concurrent Programming
> Building programs in which multiple computational activities overlap in time and tipically interact in some way.
### Concurrent Program
> Finite set of sequential programs that can execute in parallel.
> The execution of a concurrent program is called concurrent computation or elaboration.

- A sequential program specifies sequential execution of a list of statements
- The execution of a sequential program is called **process**
- a concurrent program specifies two or more sequential programs that may be executed concurrently as parallel processes
### Terminology
![[Pasted image 20261013122146.png]]
## Concurrency Paradigms/Architectures
- Multi-threaded programming
	- shared state
	- need of a synchronisation mechanism such as semaphores, monitors ecc...
- Message-based programming
	- no shared state
	- interaction by means of message exchange
- Event-driven programming
	- An action generates an event which will be dispatched, so the execution of the program is dictated by the events themselfs 
- Asynchronous programming 
	- A synchronous program with some asynchronous actions and requests, which will be handled by future mechanisms and/or callbacks
	- never blocking dogma
- Reactive programming
	- the flow of the program is designed around data flows and the propagation of change
#### Multi-Core CPU architecture and 