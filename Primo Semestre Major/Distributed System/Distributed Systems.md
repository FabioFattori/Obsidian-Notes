# Distributed Systems
## 10/10/2025 Replication & Consistency Pdf Fino a Pag
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
![[1.png]]
![[2.png]]
![[3.png]]
Caching is a form of data replication.![[4.png]]
### Replication as a Scaling Technique
Scalability issues generally appear in the form of performance problems.
Replication and caching for performance are widely applied as scaling techniques.
Placing copies of data close to the processes using them can improve performance through reduction of access time, and thus solve scalability problems: 
	_trade-off_: keeping copies up to date may require more network bandwidth
![[5.png]]
![[6.png]]![[7.png]]
![[8.png]]![[9.png]]
#### The Problem of Consistency
instead of demanding a total consistency scenario, we might be good just with some degree of consistency and some other _acceptable_ degree of inconsistency, depending on the specific application we are dealing with.
So that engineers can fully explore the trade-off between the costs and the benefits of consistency:
	by relaxing consistency requirements according to the specific application scenario at hand this has lea to the definition of different *consistency models*  which are then amenable of different implementations, based on different protocols, and whose features may affect the effectiveness of the model.
### Data-centric Consistency Models
>more like a API way of thinking, the process and operations used are only the "API" like made possible by the system, ensuring the consistency
![[Primo Semestre Major/Distributed System/imgs/10.png]]
![[Primo Semestre Major/Distributed System/imgs/11.png]]
#### Continuous Consistency
![[Primo Semestre Major/Distributed System/imgs/12.png]]
![[13.png]]
![[14.png]]
##### Consistent Operations Ordering
![[Primo Semestre Major/Distributed System/imgs/15.png]]
###### Sequential Consistency
![[Primo Semestre Major/Distributed System/imgs/16.png]]
###### Causal Consistency
![[17.png]]

### Client-centric Consistency Models
