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
> Uno sbilancio tra il numero di chiavi presenti nei DB può accadere.
> Questa situazione prende il nome di **[Skewness](https://search.brave.com/search?q=skewness&source=desktop&conversation=09a5cf475c0e10f01ad11b0a5d530cc409bd)**.

### Number of Reduce Tasks
![[Pasted image 20261005134931.png]]
> La more reasonable solution funziona meglio proprio quando c'è la skewness.

QUINDI come lo scelgo sto numero? a cazzo di cane bel, vai a tentoni e vedi la situa, in ogni caso vale quello che viene detto sopra dopo il titolo arancione.
### Final Picture
![[Pasted image 20261005140147.png]]
### MapReduce Algorithms
![[Pasted image 20261005141640.png]]
#### Filtering Algorithms
![[Pasted image 20261005141651.png]]
![[Pasted image 20261005141831.png]]
#### Summarization Algorithms
![[Pasted image 20261005141711.png]]
![[Pasted image 20261005141823.png]]
#### Join
![[Pasted image 20261005141744.png]]![[Pasted image 20261005141758.png]]
##### Sort
![[Pasted image 20261005141813.png]]
### Two Stage MapReduce
![[Pasted image 20261005142317.png]]
![[Pasted image 20261005142325.png]]
## Yarn - Yet Another Resource Negotiator
![[Pasted image 20261005142414.png]]
### Main Deamons 
![[Pasted image 20261005142609.png]]
![[Pasted image 20261005142800.png]]
> L'RM non gestisce effettivamente un'applicazione ma bensì la gestisce l'AMP 