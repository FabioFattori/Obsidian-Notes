### 10/10/2025 Replication & Consistency
Why Replication of Data? 
- increasing the reliability of systems
- improving performance
- scaling in numbers and geographical area
#### Data replication for Reliability
If a file system has been replicated, system operation may continue after one replica crashes by simply switching to one of the other replicas.
Maintaining multiple copies allows for better protection against corrupted data :
	Example:
	if we have three copies of a file, and perform every read and write operation on each copy, we could hide a single failing write operation by considering as correct the value returned by at least two copies.
