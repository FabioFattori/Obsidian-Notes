# Distributed Systems
## Recupero - 16/10/2025 Fine Primo Pdf
# Availability, Consistency and Failure
## Hiding Failure in Distributed Systems
> being able to keep on providing services in spite of failures is supposed to be one of the main benefit of distributed systems over centralised ones

Assumption: distributed systems can be designed so that if a component of the system fails, disconnects ecc..., other components can replace it, which *Hides* the failure or at least mitigate the impact (perceived) of that failure.
When a system can hide most of the failures, it is *highly available*.
### Expected Features of a Distributed System
- consistency $\rightarrow$ correct behavior when queried
- availability $\rightarrow$ the system is live
- unreliable $\rightarrow$ we know that systems can experience so many things that make them go offline.
### Tradeoff - CAP Theorem
#### Informally
According to the CAP theorem, it is only possible to simultaneously provide any two of the three following properties in distributed applications: 
- **consistency (C)** $\rightarrow$ the replicated data is always consistent with each other.
- **availability (A)** $\rightarrow$ the data is highly available to the users.
- **partition tolerance (P)** $\rightarrow$ the system can continue providing services to its users even when the network partitions.
#### Formally
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/18.png]]
##### What of the 3 Do We Pick?
>The three properties are not exactly of the same sort, both technically and conceptually consistency and availability range over a spectrum of options, whereas partition tolerance can somehow be seen more as an on/off feature. All of them are desirable, yet forfeiting partition tolerance is not really an option in real-world systems.
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/19.png]]
### Definitions
#### Availability
>_"For a distributed system to be continuously available, every request received by a non-failing node in the system must result in a response"_
#### Consistency
A consistent service is modelled as an atomic data object where:
- operations are totally ordered
- each operation occurs in a single instant of time
> _"consistency implies that all read operations over a distributed shared memory occurring after a write operation completes must return the value of either this write operation or a later one"_

A system is **consistent** if we got _correct responses_.
#### Network Partition
> _"When a Network is partitioned, all messages sent from nodes of a component (partition) to nodes of a different component are lost"_

![[Primo Semestre Major/Distributed System/imgs/22_10_2025/20.png]]
## ACID Vs BASE
The followings are two way to approach the creation of a distributed system by following each in their own way the CAP Theorem:
- ![[Primo Semestre Major/Distributed System/imgs/22_10_2025/21.png]]
- BASE $\rightarrow$ 
	- Basically Available
	- Soft State: generated at the expense of additional computation or file I/O, is exploited to improve performance; data is not durable
	- Eventually Consistency: Stale data can be temporarily tolerated as long as all copies of data eventually reach consistency after a short time
	In this approach the responses are _approximate_ but they are delivered quickly, which in some situations is more valuable than slow correct answers, which sometimes are also delivered by a system builded in this way.
	The Big Tech Companies these days are using this type of approach.
### Overall
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/22.png]]

---
# Recupero: Pdf M1
## Dependability in Distributed Systems
### Premessa
Distributed systems are, now days, playing a major role in our every day life because they are behind some of the most important aspects of each individual, from finacial to entertainment.
Their _**dependability**_ (affidabilità) increased in each of these aspects, in fact the _**cost of failure**_ is tipically <span style="color:rgb(255, 0, 0)">enormous</span>.
![[Primo Semestre Major/Distributed System/imgs/Recupero_6_11_2025/1.png]]
#### Dependability in the Dictionary
![[Primo Semestre Major/Distributed System/imgs/Recupero_6_11_2025/2.png]]
in systems engineering, too, dependability is closely related to reliability.
#### Glossario
##### Termini
- Distributed Computing $\rightarrow$ dependability refers to the ability of a distributed system to provide correct services to its users despite the many different threats (hardware failures, malicious attack, etc...).
### System Models
> A (distributed) system is designed to provide a set of services to its users.
	each service has an interface that each client could use to request the service.
- Functional Specification $\rightarrow$ defines what a service should do.
#### System State
At each moment, a system is in a given _**state**_.
	What is the given state of a DS is a complicate thing to know.
	The state is determinated collectively by the state of the processes and threads in the system.
- External/Observable State $\rightarrow$ Part of the state might become either implicitly or explicitly visible through user interaction.
- Internal State $\rightarrow$ All the remaining states which the users cannot see.
> Generally speaking, the state of a system at time t is represented by the (minimum amount of) information that, along with the knowledge about the dynamics of a (deterministic) system, allows an observer to completely describe the future system behavior—from time t on

States are used for _**recovery**_ after a failure, in fact a system can be recovered to the "place" where it was before a failure if its state was captured before it's failure (example: the state is serialized and stored to a stable storage.)
#### System Boundary
> physical and logical line that separates the system from it's surrounding environment.

- _System's Components_ $\rightarrow$ inside the boundary
	For component the definition depends on which level of abstraction we are using to describe system, let's say:
	1. at one given level of abstraction, we could observe a system (with its components) interacting with other systems.
	2. at another given level of abstraction, the same system could be instead described as a component of a larger system.
- _System's Environment_ $\rightarrow$ outside the boundary.
	For environment we intend all other systems that our system interact with, in general, all the other system's that affect in any way our system.
### Threat Models
Definition of <span style="color:rgb(255, 0, 0); font-weight: bold">failure</span>:
> When a system is not compliant with its functional specification.

A failure it's caused by it's state, or part of it, having wrong values(example: errors in it's state).
We assumes that errors are caused by <span style="color:rgb(255, 0, 0); font-weight: bold">faults</span>.
_Threats_ to dependability are described as different sorts of faults.
![[Primo Semestre Major/Distributed System/imgs/Recupero_6_11_2025/3.png]]
#### Dormant Fault
A fault is dormant when it could not be immediately tested and found (example: a bug in the software not causing problems until the corresponding code is executed).
When the specific condition is met, the fault will be activated causing an error in the component and when that component the error will be propagated through the system.
When that error reaches the user interface, which will deviate the service given to that users a _service <span style="color:rgb(255, 0, 0); font-weight: bold">failure</span>_ occurs.
#### Chain of Threats
Given the typical recursive nature of system composition, the failure of one system can cause a fault in a larger system as follows:
![[Primo Semestre Major/Distributed System/imgs/Recupero_6_11_2025/4.png]]
Such relationship between fault, error and failure is referred to as _**chain of threats**_.



---
## 10/10/2025 Replication & Consistency M3 Pdf Fino a Pag 34
Why Replication of Data? 
- increasing the reliability of systems
- improving performance
- scaling in numbers and geographical area
### Data Replication for Reliability
If a file system has been replicated, system operation may continue after one replica crashes by simply switching to one of the other replicas.
Maintaining multiple copies allows for better protection against corrupted data :
	Example:
	if we have three copies of a file, and perform every read and write operation on each copy, we could hide a single failing write operation by considering as correct the value returned by at least two copies.
Replication for performance is important when a distributed system needs to scale in terms of (i) size or (ii) the geographical area covered
	Example: 
	Scaling regarding size occurs when an increasing number of processes needs to access data managed by a single server performance can be improved by (i) replicating the server, and (ii) subsequently dividing workload among the processes accessing the data.
	When scaling over a geographical area, time to access data decreases by placing a copy of data near to the process using them
	-  → performance as perceived by that process increases 
	- ! keeping all replicas up to date may consume more network bandwidth 
	- ? do we have a benefit overall?
at a first glance, benefits of (data) replication 
- reliability 
- fault tolerance 
- accessibility 
- performance 
- scalability
#### Problems
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/1.png]]
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/2.png]]
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/3.png]]
Caching is a form of data replication.![[Primo Semestre Major/Distributed System/imgs/22_10_2025/4.png]]
### Replication as a Scaling Technique
Scalability issues generally appear in the form of performance problems.
Replication and caching for performance are widely applied as scaling techniques.
Placing copies of data close to the processes using them can improve performance through reduction of access time, and thus solve scalability problems: 
	_trade-off_: keeping copies up to date may require more network bandwidth
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/5.png]]
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/6.png]]![[Primo Semestre Major/Distributed System/imgs/22_10_2025/7.png]]
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/8.png]]![[Primo Semestre Major/Distributed System/imgs/22_10_2025/9.png]]
#### The Problem of Consistency
instead of demanding a total consistency scenario, we might be good just with some degree of consistency and some other _acceptable_ degree of inconsistency, depending on the specific application we are dealing with.
So that engineers can fully explore the trade-off between the costs and the benefits of consistency:
	by relaxing consistency requirements according to the specific application scenario at hand this has lea to the definition of different *consistency models*  which are then amenable of different implementations, based on different protocols, and whose features may affect the effectiveness of the model.
### Data-centric Consistency Models
>more like a API way of thinking, the process and operations used are only the "API" like made possible by the system, ensuring the consistency
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/10.png]]
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/11.png]]
#### Continuous Consistency
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/12.png]]
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/13.png]]
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/14.png]]
##### Consistent Operations Ordering
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/15.png]]
###### Sequential Consistency
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/16.png]]
###### Causal Consistency
![[Primo Semestre Major/Distributed System/imgs/22_10_2025/17.png]]
### Client-centric Consistency Models

#TODO tutti i pdf da scorso capitolo fino a pagina 67 del pdf C4

---
### Eventual Consistency
> Prima o poi, in tempo finito, il sistema diventerà consistente:
> Dove "Prima o poi" corrisponde a una unità di tempo ragionevole

![[Primo Semestre Major/Distributed System/imgs/31_10_2025/1.png]]
### Byzantine Faults
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/2.png]]
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/3.png]]![[Primo Semestre Major/Distributed System/imgs/31_10_2025/4.png]]
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/5.png]]
### Consenso
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/6.png]]
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/7.png]]
# Blockchain Main Elements
## Disclaimer
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/8.png]]
# Blockchain Overview
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/9.png]]
## Architettura Di Un BCT
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/10.png]]
### User Identifiers
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/11.png]]
#TODO da pagina 82 fai fino a pagina 98 
## Transazioni E Block Workflow
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/12.png]]
### Block's Life
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/13.png]]![[Primo Semestre Major/Distributed System/imgs/31_10_2025/14.png]]![[Primo Semestre Major/Distributed System/imgs/31_10_2025/15.png]]
## Consenso E Mining
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/16.png]]
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/17.png]]
## Protocollo PBFT
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/18.png]]
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/19.png]]
### Proof-of-Work (PoW), Ovvero Mining
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/20.png]]![[Primo Semestre Major/Distributed System/imgs/31_10_2025/21.png]]
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/22.png]]
![[Primo Semestre Major/Distributed System/imgs/31_10_2025/23.png]]![[Primo Semestre Major/Distributed System/imgs/31_10_2025/24.png]]
#NOTE sto capitolo leggilo bene e bona perchè sto stronzo lo ha speed runnato senza soffermarsi più di tanto fino a pagina 128.
# 3/11/2025 Continuo Pdf C4
![[Primo Semestre Major/Distributed System/imgs/3_11_2025/1.png]]
## Smart Contracts
sono un modo per estendere una applicazione che ha a che fare con le blockchains, presenti in un determinato livello di astrazione.
![[Primo Semestre Major/Distributed System/imgs/3_11_2025/2.png]]
### Features
![[Primo Semestre Major/Distributed System/imgs/3_11_2025/3.png]]
![[Primo Semestre Major/Distributed System/imgs/3_11_2025/4.png]]
### Operations
![[Primo Semestre Major/Distributed System/imgs/3_11_2025/5.png]]
### Deployment
![[Primo Semestre Major/Distributed System/imgs/3_11_2025/6.png]]
### Invocation
![[Primo Semestre Major/Distributed System/imgs/3_11_2025/7.png]]
#NOTE  frate finisce il pdf ma lo zio non sta dicendo niente di che.
Inizio pdf M4 fino a pagina 