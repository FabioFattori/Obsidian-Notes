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
### Multi-Core CPU Architecture - Core Types
![[Pasted image 20261013123311.png]]
## Flynn's Taxonomy (Categorization sYstem)
> Computer systems are categorized according to the number of instruction stream and data stream on whose they can operate with. 

There are 4 possibilities:
### Single Instruction, Single Data (SISD)
Von-Neumann model, single processor computers 
### Single Instruction, Multiple Data (SIMD)
Single instraction stream concurrently broadcasted to multiple processors, each with its own data stream.
Fine grained parallelism, vector processors
### Multiple Instruction, Single Data (MISD)
No well known system fit this Category, lol.
### Multiple Instruction, Multiple Data (MIMD)
Each processor has it's own stream of instructions operating on its own data.
This category can also be subdivided based on the memory organization:
- **Shared Memory**
	all processes (processors) share a single address space and communicate each other by writing and reading shared variables
	- Symmetric Multi-processing Architecture (**SMP**)
		All processors share a connection to a common memory and access all location memories at equal speed
	- Non-Uniform Memory Access (**NUMA**)
		The memory is shared, some blocks of memory may be physically more closely associated with some processors than others. 
- **Distributed Memory**
	each process (processor) has its own address space and communicate with other process by message passing (sending and receiving messages)
	- Massively Parallel Processors (**MPP**)
		![[Pasted image 20261013213528.png]]
	- **Clusters**
		Distributed-memory systems composed of off-the-shelf computers connected by off-the-shelfs network
	- **Grid**
		Systems that use distributed, heterogeneous resources connected by LAN and/or by WAN, without a common point of administration
## Why Concurrent Programming => PERFORMANCE
![[Pasted image 20261013214005.png]]
### Amdahl's Law
![[Pasted image 20261013214106.png]]
![[Pasted image 20261013214147.png]]
- We can improve performances by adding processors only for those parts that can run in parallel, not for sequential parts => strong impact on performances of sequential parts

> But sequential parts are often needed for correctness
## Efficiency
![[Pasted image 20261013214703.png]]
### Memory Bottleneck
![[Pasted image 20261013214750.png]]
# Concurrent Programming as a Paradigm
![[Pasted image 20261013222713.png]]
![[Pasted image 20261013222647.png]]
## Process Interaction
![[Pasted image 20261013222746.png]]
### Cooperation
> Refers to interactions which are both expected and wanted, they are part of the semantics of the concurrent program

Two kinds:
- ***Communication***
	![[Pasted image 20261013223007.png]]
- ***Synchronisation***
	![[Pasted image 20261013223022.png]]
### Contention/Competition
> Refers to interactions which are expected and necessary, but not wanted.
> Typically concerns the need of coordinating the access by multiple processes to shared resources.

Two basic class of problems:
- ***Mutual Exclusion***
	>ruling the access to shared resources by distinct processes
- ***Critical Sections***
	> ruling the concurrent execution of blocks of actions by distinct processes

#### Mutual Exclusion VS Synchronisation
> ***synchronisation*** defines a timing relationship among processes.
> 	Maintaining time-relationships which includes actions happening at the same time or happening at the same relative rate or simply some action having to occur before another (precedence relationships).

> ***mutual-exclusion*** defines a restriction on access to shared data.
> Mutual-exclusion is meaningless if no shared data is involved

![[Pasted image 20261013223525.png]]
### Interferences
![[Pasted image 20261013223643.png]]
#### Race Conditions
![[Pasted image 20261013223737.png]]
### Critical Situations
> Interferences and errors in concurrent programs can lead to critical situations for the concurrent system in the overall

such as:
#### Deadlock
![[Pasted image 20261013223912.png]]
#### Starvation (Or uNfairness)
![[Pasted image 20261013223924.png]]
#### Livelock
![[Pasted image 20261013223941.png]]
### Concurrent Languages And Concurrent Machines
> A ***concurrent language*** is a programming language that enables programmers to write down programs as set of instructions to be executed concurrently

> A ***concurrent machine*** is a machine that can run the concurrent language, so is a machine (which can be abstract) designed to handle the execution of multiple sequential processes, by exploiting multiple processors (physical or virtual)

#### Concurrent Machines
![[Pasted image 20261013224531.png]]
#### Basic Mechanisms
![[Pasted image 20261013224623.png]]
##### Concurrent Programming Languages - Design Approaches
![[Pasted image 20261013224723.png]]
# From Programs to Models and back
> A model is a rigorous description / representation of program (system) structure and behaviour at a proper level of abstraction, including relevant information, abstracting from non-relevant aspects.

The Model can be visualized in a diagrammatical way for program design, formal models for program analysis and verification.
![[Pasted image 20261014094437.png]]
## A Model for Concurrent Program Execution
![[Pasted image 20261014094933.png]]
### State Diagram
![[Pasted image 20261014095052.png]]
### N Scenarios
> $n$ Scenarios is a number of possible outcomes of a concurrent program:
	![[Pasted image 20261014095222.png]]
![[Pasted image 20261014095439.png]]
### Non-Atomic Structures
![[Pasted image 20261014095548.png]]
![[Pasted image 20261014101636.png]]
![[Pasted image 20261014101722.png]]
### Arbitrary Interleaving
> This means that we ignore time in our analysis of concurrent programs.
> So we focus only on:
> - partial orders related to action sequences
> - atomicity of the individual action 
> We also seek robustness with respect to both hardware and software changes.

![[Pasted image 20261014102255.png]]
#### Correctness of Programs
![[Pasted image 20261014102353.png]]
> The ***correctness*** of concurrent programs is defined in terms of properties of computations.
> A ***property*** is a condition that must be verified in every possible scenario.

##### Safety Properties
![[Pasted image 20261014102611.png]]
##### Liveness (Or Progress) Properties
![[Pasted image 20261014102646.png]]
###### Fairness
> A liveness property which holds that something good happens infinitely often.

So programs can have different liveness behavior depending on precisely how their instructions are interleaved.
###### Scheduling Policies
> how instructions are interleaved is a result of a scheduling policy.

![[Pasted image 20261014102939.png]]
###### Unconditionally Fair Scenario
> a scenario is (unconditionally) fair if at any state in the scenario a statement that is continually enabled eventually appears in the scenario.

### Critical Section Problem
![[Pasted image 20261014103740.png]]
> ![[Pasted image 20261014103856.png]]

Any proposed solution must satisfy also the progress property for the CS:
> once a process starts to execute the statements of its critical section, it must eventually finish.

The NCS need not to progress when the policy demands that the CS cannot be executed.
#### CS Solutions: Algorithms VS Mechanisms
CS problems can easily be solved by basic mechanisms provided by the concurrent machine such as ***lock and semaphores***.
Another way is by using algorithms using solely basic atomic statements.
#### Dekker's Algorithm
> The problem can be solved with a simple variation of the 4th algorithm, requiring that ***the right to insist*** on entering - instead of the right to enter - is explicitly passed between the processes by means of the variable turn.

![[Pasted image 20261014105436.png]]
#### Peterson's Algorithm
![[Pasted image 20261014105522.png]]
### Introducing More Atomic Statements
![[Pasted image 20261014110103.png]]
### Locks
![[Pasted image 20261014110239.png]]
#### Atomic Statement: Synchronized
![[Pasted image 20261014110359.png]]
#### Bakery Algorithm
![[Pasted image 20261014110509.png]]
## About Correctness: Verification VS Testing
![[Pasted image 20261014110653.png]]
### Tests: Liveness and Safety
![[Pasted image 20261014110757.png]]
#### Problems of Testing
> Typically checking only a subset of the scenarios.
> "heisenbugs" phenomenon => test code can introduce timing or synchronisation artefacts that can mask bugs.

![[Pasted image 20261014111019.png]]
#### Formal Methods
![[Pasted image 20261014111147.png]]
##### CORRECTNESS PROPERTIES IN PROPOSITION CALCULUS
![[Drawing 2026-10-14 11.37.13.excalidraw|1500|2000]]
![[Pasted image 20261014113241.png]]
#### Temporal Logic
> Processes and systems change their state over the time, and then also the interpretation of formulae about their state can change over the time

![[Pasted image 20261014114201.png]]
##### LTL: Temporal Operators
![[Pasted image 20261014114417.png]]
###### Basic Properties
![[Pasted image 20261014114434.png]]
![[Pasted image 20261014114552.png]]
#### Specifying Safety Properties
![[Pasted image 20261014114651.png]]
#### Specifying Liveness Properties
![[Pasted image 20261014114718.png]]
#### Next Operator
![[Pasted image 20261014114816.png]]
#### Binary Operators
![[Pasted image 20261014115642.png]]
![[Pasted image 20261014115655.png]]
#### Overtaking
![[Pasted image 20261014115817.png]]
##### K-Boundend Overtaking Property
> from the time a process p attempts to enter its critical section, another process can enter at most k times before p does.
### Verification Tecniques: Model Checking
![[Pasted image 20261014133640.png]]
#### State-Space Explosion Problem
![[Pasted image 20261014133830.png]]
##### Spin & Promela
- Spin
	> Widely used model-checker, extremely efficient, used in modelling and designing concurrent and distribuited systems in general
- Promela
	> is the language used in Spin to write concurrent programs modelling, it has a limited number of constructs intended to be used to build models of concurrent systems.
##### JPF
Is a special JVM executing programs theoretically along all possible scenarios (execution paths), checking for property violations.
### Verification Techniques: Inductive Proof of Invariants
![[Pasted image 20261014134442.png]]
#### Safety and Liveness Property Verification
> A ***<span style="color:rgb(255, 0, 0)">Safety</span> <span style="color:rgb(255, 0, 0)">property</span>*** must be true at all states.
> It is sufficient to find a state not verifying the property to complete the verification.

> A ***<span style="color:rgb(255, 0, 0)">Liveness property</span>*** claims that a state satisfying a property will inevitably occur.
> it is not sufficient to check states one by one, it is necessary to check all possible scenarios.
> it requires more complex theory and software techniques.

#### TLA/TLA+ (Temporal Logic of Actions)
A formal specification language, based on simple discrete math (set theory and predicates).
Used to specify and verify complex real-world systems.
##### TLA+ Spec
![[Pasted image 20261014135014.png]]
# Modulo 1.3
## Synchronization Mechanisms
> semafori e monitor (così come altri meccanismi) inseriti perchè gli algoritmi realizzati esclusivamente con istruzioni macchina sono possibili, ma di livello troppo basso e difficili da programmare correttamente.

### Semafori
> $$S = S(S.V,S.L)$$
> $S.V$ è un intero maggiore o uguale a zero; 
> $S.L$ è l’insieme degli identificativi dei processi bloccati.
> L’inizializzazione è $S = (k, \{\})$, con $k >= 0$. 

![[Pasted image 20261014165012.png|1500]]
#### Invarianti
Se $k$ è il valore iniziale, $\#signal(S)$ il numero di signal eseguiti e $\#wait(S)$ il numero di wait completati con successo, valgono:
$S.V >= 0$ e $S.V = k + \#signal(S) - \#wait(S)$.
Un wait bloccato non è ancora considerato completato.
#### Varianti
![[Pasted image 20261014165536.png]]
#### Sezione Critica Con I Semafori
> un semaforo weak non garantisce generalmente assenza di starvation.

#### Producers-Consumer E Bounded Buffer
