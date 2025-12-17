# <a href="http://bias.csr.unibo.it/maltoni/ml/SoluzioniEsami/">Prove D'esame</a>
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
Il Support Vector Machine si basa sul principio di individuare l'iperpiano di separazione ottimale per, appunto, separare le classi fra loro con distanza maggiore dall'iperpiano individuato.
Il margine è la minima distanza tra i support vectors delle due classi del training set dall'iperpiano, ovvero i campioni più vicini all'iperpiano individuato delle classi.
Il massimizzare il margine è legata alla generalizzazione, di fatti se le classi del training set hanno un ampio margine, quindi sono facilmente separabili, ci si aspetta che anche quel test set lo siano.
### Perché Le Recenti Reti Neurali Deep Sono Più Efficaci Delle MLP a Tre Livelli?
Le recenti reti neurali deep sono più efficaci delle MLP a tre livelli perché la **profondità** consente di rappresentare alcune funzioni in modo **molto più efficiente**.  
Sebbene il _universal approximation theorem_ garantisca che una MLP con un solo livello hidden possa approssimare qualsiasi funzione, **l’esistenza di una soluzione non implica efficienza**: esistono funzioni che possono essere rappresentate con **complessità polinomiale usando più livelli**, ma che richiedono **complessità esponenziale** se realizzate con un livello in meno.
L'organizzazione gerarchica delle DNN porta con se diversi vantaggi:
- condividere e riusare le informazioni già estratte su più livelli
- selezionare feature più astratte, scartando eventuali informazioni inutili durante il processo
- modellare fenomeni più complessi, grazie alla gerarchia presente in esse che rispecchia in maniera più accurata sistema visivo umano.
### Fare Esempi Pratici Di Pattern Numerici, Categorici E Di Sequenze
- Numerici
	1. Misure numeriche continue di un prodotto, ad esempio la concentrazione di solfati in un vino per predirne la qualità.
	2. Valori di consumo energetico di un calorifero utilizzati per stimare i costi annuali.
- Categorici
	1. In un dataset di persone, il genere (es. uomo/donna), rappresentato come variabile categorica binaria.
	2. La regione o provincia di provenienza di un vino, rappresentata come etichetta discreta (stringa o codice).
- Sequenze
	1. Un video di sorveglianza, visto come una sequenza temporale di immagini.
	2. Una traccia musicale, rappresentata come sequenza temporale di campioni audio per la classificazione del genere.
### Nella Regressione Cosa Si Intende per Variabile Indipendente E Variabile Dipendente?
Nella regressione per variabile indipendente si intende la variabile, o insieme di variabili, di input x mentre per variabile dipendente si intende la variabile di output y, quindi quello che il modello di regressione produce.
Inoltre si può dire che la variabile indipendente x si considera sempre come priva di errori mentre la variabile dipendente y va sempre considerata come influenzata da errori.
## 17/2/2017
### Cosa Si Intende per Iperparametri? Fornire Esempi Pratici Di Iperparametri. Come Si Ottimizzano?
Per iperparametri si intendono dei valori che definiscono i dettagli archietturali del modello e della corrispondente procedura di training, tali valori non vengono appresi in autonomia dal modello sui dati, ma bensì passati ed utilizzati per la definizione del modello stesso.
Esempi:
- learning rate
- batch size 
- numero di neuroni in una rete neurale
- tipo di loss function
- tipo di activation function
- numero di cluster per quanto riguarda l'algoritmo K-means
- ecc...
Gli iperparametri vengono ottimizzati valutando diverse configurazioni tramite tecniche come **grid search** o **random search**, generalmente abbinate alla **k-fold cross-validation**, al fine di selezionare la configurazione che massimizza le prestazioni sul validation set.
### Come Si Imposta Un Problema Di Multiple Linear Regression? Come Sono Popolati X, Y E $\beta$?
Nel seguente caso abbiamo che la variabile indipendente è un vettore tale che $x\in \mathbb^d$ 


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
### Svolgimento
![[es2.png]]
## Majority Vote Rule Di Una Multiclassificatore
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/3.png]]
### Svolgimento
Qui banalmente devi scegliere la classe che viene prodotta di più dai singoli classificatori per ogni riga, il numero scritto in grassetto è quello che dovresti scrivere all'esame.
## Calcolo Del Numero Di Addizioni E Moltiplicazioni in Una MLP
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/4.png]]
### Svolgimento
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/5.png]]
## Calcolo Del Vettore Medio E Della Matrica Di Covarianza
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/6.png]]
### Svolgimento
$n$ => numero dei pattern forniti dall'esercizio
$\mu$ => vettore media dei pattern forniti, per questo esercizio in particolare bisogna fare la media del primo elemento dei singoli pattern e del secondo elemento:
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/7.png]]
per quanto riguarda la matrice basta applicare la formula, è lunga ma si fa, ricordati che la dimensione di $\sum{}{}$ è la dimensione del singolo pattern per la dimensione di $\mu$ perchè alla fine della fiera è una moltiplicazione tra matrici.
## Prima Iterazione Dell'algoritmo K-means per I Seguenti Pattern
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/8.png]]
### Svolgimento
Per quanto riguarda l'appartenenza ai centroidi bisogna calcolare la distanza euclidea di ogni punto da ciascuno dei due, la minore ci dice a quale cluster appartiene il pattern:
$$d(p_i,c_i) = \sqrt{(x_{p_i} - x_{c_i})^2 + (y_{p_i} - y_{c_i})^2}$$
quindi esempio con il primo:
$$d(p_1,c_1) = \sqrt{(7,7 - 0,1)^2 + (4,0 - 5,1)^2} = 7,68$$
$$d(p_1,c_2) = \sqrt{(7,7 - 3,8)^2 + (4,0 - 2,8)^2} = 4,08$$
Quindi dato che $d(p_1,c_2) < d(p_1,c_1)$   $p_1 \in Cluster\\\ 1$ .
>Questo va fatto per ogni pattern

Una volta fatto per tutti i pattern, e quindi si ottengono quali pattern appartengono a quali cluster di deve fare la media per calcolare le coordinate del nuovo centroide, quindi per questo esercizio specifico avremo che:
$Cluster \\\ 1 = \{p_2,p_3\}$
$Cluster \\\ 2 = \{p_1,p_4,p_5,p_6\}$ 
quindi per i nuovi centroidi dovremo fare questo:
$x_{c_1} = \frac{x_{p_2} + x_{p_3}}{2}$
$y_{c_1} = \frac{y_{p_2} + y_{p_3}}{2}$
è una media bel, se non ti fidi controlla questo risultato che sono i nuovi centroidi trovati dal prof come soluzione dell'esercizio:
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/9.png]]
