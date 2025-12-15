# Prove D'esame
## 07/12/2016
### Dare la Definizione Di Training, Validation E Test Set E Discutere Una Possibile Suddivisione Dei Dati Nei Tre Insiemi
_Per training set_ si intende una partizione del dataset atta all'addestramento interno del modello, quindi all'aggiornamento dei pesi e dei coefficenti del modello.
_Per Validation set_ si intende un sottoinsieme del dataset utilizzato per l'ottimizzazione degli iperparametri del modello, usato anche per attuare tecniche come early-stopping.
Mentre per _Test set_ si intende una partizione del dataset usata solo alla fine per stimare le prestazioni finali del modello.
Per la suddivisione si tende ad usare una distribuzione standard come segue:
-  Training set 60-70%
-  Validation set 15-20%
-  Test set 15-20%

Esempio 70%|15%|15%.
Ma può essere messa in atto quando si ha un dataset di medi/grandi dimensioni, se invece si ha a disposizione pochi dati si può decidere di non avere un validation set a favore dell'applicazione della k-fold  cross validation per ottimizzare gli iper parametri.
### Nella Formulazione dell’SVM Lineare la Funzione Obiettivo Richiede Di Massimizzare Il Margine. L’ottimizzazione È Però Vincolata; in Cosa Consistono I Vicoli? Quanti Sono?

Hard Margin
Dato un dataset dove $x_i$ è l'i-esimo dato e $y_i \in \{-1,+1\}$ si richiede che tutti i dati siano classificati correttamente e fuori dal margine, quindi:
$$y_i(w*x_i+b)-1 \geq 0\\\ per \\\ i=1...n$$
la quale richiede:
- che tutti i dati siano dal lato corretto dell'iperpiano
- la distanza dall'iperpiano sia $\geq 1$ 
Questo per ogni dato, quindi per questa modalità sono $n$ vincoli.

Soft Margin
Vengono introdotte delle slack variables per consentire violazioni:
$$y_i(w*x_i+b) \geq 1 - \xi_i \\\ per \\\ i=1…n$$
Questo vincolo permette:
- $\xi_i = 0$ punto correttamente classificato e fuori dal margine
- $0<\xi_i\leq1$ punto dentro al margine
- $\xi_i>1$ punto misclassificato

Come in Hard Margin, per questa formula abbiamo $n$ vincoli, in più vengono aggiunti altri $n$ vincoli di non negatività per le slack variables, per un totale di $2n$ vincoli.
#### Descrivere Le Principali Criticità E Limitazioni dell’algoritmo Di Clustering K-means
1. Necessità di fornire k a priori
	Ovvero, K-means richiede che k (numero di cluster) venga definito e fornito come dato di input, quindi richiede di sapere il numero di cluster a priori, se viene fornito un k non consono ai dati il risultato ottenuto non potrà essere ottimale.
2. Sensibilità all'inizializzazione
	K-means richiede anche i centroidi dei cluster come input, spesso vengono scelti in maniera randomica, configurazioni diverse di quest'ultimi portano a risultati diversi.
	L'algoritmo può convergere verso minimi locali, e non globali, portando risultati non ottimali.
3. Forma dei cluster
	K-means funziona in maniera corretta con cluster della stessa dimensione, sferici e convessi, con cluster di forme complesse o di dimensioni diverse si possono ottenere risultati non affidabili.
4. Limitazioni basate sulla misura della distanza intra-cluster
	L’uso tipico della distanza euclidea rende K-means poco adatto a dati non numerici o a contesti in cui tale misura non rappresenta correttamente la similarità tra i pattern.
##### Nell’ambito Di CNN, Che Cosa Si Intende per Connessioni Locali E Condivisione Di Pesi?
Per Connessioni locali si intende che ogni neurone del layer convoluzionale è collegato ad una regione locale dell'immagine e non a tutta come accade nelle reti fully connected, permettendo di ridurre il costo computazionale ed il numero di parametri, questo viene fatto inoltre per rilevare con maggiore precisione dei pattern locali come bordi o texture.

Per Condivisione di pesi si intende l'utilizzo degli stessi pesi, quali filtri o kernel, per posizioni diverse dell'input, producendo gli stessi risultati per un determinato pattern.
Nella pratica lo stesso filtro viene fatto passare su tutte le zone locali dell'immagine di input producendo una feature map, rispondendo allo stesso pattern indipendentemente dalla sua posizione nell'immagine.
## 20/1/2017
### Qual È Il Principio Su Cui Si Basa Il Classificatore SVM? Cosa Si Intende per Margine?


---
# Esercizi
## Classificatore Di Bayes Multinormale, Calcolare per Il Punto X![[Primo Semestre Major/Machine Learning/imgs/Esercizi/1.png]]
### Svolgimento
$d$ => numero di classi. 
$p(x | w_i)$ => densità di probabilità condizionale di $w_i$ 
$p(x) = p(x|w_0)*p(w_0) + ... \\\ per \\\ ogni \\\ i \in \{0,...,d\}$ => densità di probabilità assoluta
$p(w_i|x) = \frac{p(x|w_i) * p(w_i)}{p(x)}$ => densità a posteri di $w_i$
Per trovare l'indice basta che prendi la i della densità a posteri maggiore.
![[es1.png]]
![[1-sol.png]]
## Calcolo Dei Pesi Di Una NN
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/2.png]]
![[es2.png]]
## Majority Vote Rule Di Una Multiclassificatore
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/3.png]]
Qui banalmente devi scegliere la classe che viene prodotta di più dai singoli classificatori per ogni riga, il numero scritto in grassetto è quello che dovresti scrivere all'esame.
