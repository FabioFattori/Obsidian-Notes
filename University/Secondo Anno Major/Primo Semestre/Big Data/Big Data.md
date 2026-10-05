# Big Data
> Mio fratello in cristo ha fatto un botto di roba, va veloce mio frate.
> Fai tutti i PDF fino al 4 (NoSQL) inizia ora il pdf 5 fino a pagina 16 compresa.
## MapReduce
![[Pasted image 20261005132716.png]]
![[Pasted image 20261005132836.png]]
![[Drawing 2026-10-05 13.31.38.excalidraw|1500]]
### MapReduce with Combiners
> Un combiner è una funzione che pre-aggrega i dati prima di fare l'aggregazione fra macchine diverse (pre-aggregazione fatta su una singola macchina)

![[Pasted image 20261005133443.png]]
![[Pasted image 20261005133612.png]]
Un altro vantaggio è il fatto che, dato che i dati intermedi vengono salvati su disco della macchina, si risparmia dello spazio.
#### Problemi
##### Non Associatività
![[Pasted image 20261005133909.png]]
![[Pasted image 20261005133919.png]]
##### Non Commutatività
![[Pasted image 20261005134011.png]]
![[Pasted image 20261005134020.png]]
#### Partioning Map Output
![[Pasted image 20261005134111.png]]
![[Pasted image 20261005134318.png]]
![[Pasted image 20261005134609.png]]
> Uno sbilancio tra il numero di chiavi presenti nei DB può accadere 

### Number of Reduce Tasks
![[Pasted image 20261005134931.png]]