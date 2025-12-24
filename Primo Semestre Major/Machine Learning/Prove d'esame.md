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
Ma può essere messa in atto quando si ha un dataset di medi/grandi dimensioni, se invece si ha a disposizione pochi dati si può decidere di non avere un validationFF set a favore dell'applicazione della k-fold  cross validation per ottimizzare gli iper parametri.
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
Nel seguente caso abbiamo che la variabile indipendente è un vettore tale che $x\in \mathbb{R}^d$.
Dato un training set composto da $n$ pattern, per impostare il problema dobbiamo costruire $X$ , $y$ e $\beta$ nel seguente modo:
- per quanto riguarda $X$, che ha forma $X\in \mathbb{R}^{n × (d+1)}$ viene calcolata inserendo sulle righe i $n$ pattern tralasciando l'ultima colonna che viene riempita da $1$ per rappresentare l'intercetta.
- $y$ invece è un vettore che contiene $y_i$ per ogni $i\in \{1,...,n\}$   
- $\beta$, che è della forma $\mathbb{R}^{d+1}$, raccoglie i coefficienti del modello, compreso il temine noto.
Quindi otteniamo che $y=X\beta$ oppure $y_i = \sum^{d+1}_{j=1}x_{i,j}\beta_{j}$
Poiché tipicamente $n>d+1$, il sistema è **sovradeterminato** e i parametri $\beta$ vengono stimati risolvendo un problema di **minimi quadrati (Least Squares)**.
### Che cos’è Il Learning Rate nell’ambito dell’apprendimento Di Reti Neurali? Cosa Succede Se Viene Scelto Un Learning Rate Troppo Piccolo O Troppo Grande?
Il learning rate è un iperparametro che regola l'ampiezza di aggiornamento dei pesi durante la fase di training di una rete neurale tramite backpropagation e gradient descent.
Nello specifico $\eta$ rappresenta l'ampiezza del passo di discesa segue la direzione opposta al gradiente della funzione di errore, questo rende, di fatto, la scelta di questo iperparametro cruciale, infatti:
- quando si sceglie un $\eta$ troppo piccolo si ottiene che la rete convergerà più lentamente con maggiori probabilità di rimanere bloccati in un minimo locale
- invece quando lo si sceglie troppo grande otterremo delle oscillazioni indesiderate dei pesi facendo divergere il processo di training 
### Quali Sono I Più Noti Algoritmi Di Clustering?
- **Clustering partizionale**
    - **K-means**  
        È uno degli algoritmi di clustering più noti. Suddivide i dati in kkk cluster minimizzando la varianza intra-cluster, utilizzando la distanza euclidea e centroidi aggiornati iterativamente.
- **Clustering gerarchico**
    - **Hierarchical Clustering** (agglomerativo o divisivo)  
        Costruisce una gerarchia di cluster senza richiedere la scelta preventiva del numero di cluster, rappresentabile tramite dendrogramma.
- **Clustering basato sulla densità**
    - **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)**  
        Identifica cluster come regioni ad alta densità di punti ed è in grado di individuare outlier come rumore.
- **Clustering probabilistico / model-based**
    - **Gaussian Mixture Models (GMM)**  
        Assume che i dati siano generati da una combinazione di distribuzioni gaussiane e assegna i punti ai cluster in modo probabilistico.
## 23/06/2017
### Nel Classificatore SVM Cosa Sono I Support Vectors?
Sono i pattern che giacciono sul margine, tali pattern definiscono completamente la soluzione del problema indipendentemente dalla dimensione $d$ e dal numero di pattern $n$.
Il problema può essere direttamente espresso come funzione di tali pattern.
### Qual È l’idea Di Base Di Base dell’algoritmo Di Clustering EM Con Gaussian Mixture?
L’idea di base dell’algoritmo **EM (Expectation–Maximization) con Gaussian Mixture** è modellare i dati come generati da una **combinazione (mixture) di distribuzioni gaussiane**, ciascuna delle quali rappresenta un cluster.

Ogni cluster è descritto da una gaussiana caratterizzata da **media**, **covarianza** e **peso**, e l’appartenenza di un pattern a un cluster è espressa in modo **probabilistico**, non deterministico.
L’algoritmo procede in modo **iterativo**, alternando due fasi:
- **Expectation step (E-step)**: si stima, per ogni pattern, la **probabilità di appartenenza** a ciascuna gaussiana, dati i parametri correnti del modello;
- **Maximization step (M-step)**: si aggiornano i **parametri delle gaussiane** massimizzando la **verosimiglianza** dei dati pesata dalle probabilità stimate nell’E-step.
Questo processo viene ripetuto fino a convergenza, portando a una stima dei parametri che **massimizza la likelihood** del modello sui dati osservati .
### Quali Sono Le Più Comuni Funzioni Di Attivazione Utilizzate per Neuroni Artificiali? Perché È Necessario Che Siano Non-lineari E Differenziabili (esistenza derivata) ?
- Relu
- Eli
- tanh
- sigmoid
- maxout

Le funzioni di attivazioni devono essere non lineari e differenziabili perchè:
- Non lineare per permettere alla rete di eseguire un mapping complesso delle informazioni di input
- Differenziabile per permettere l'applicazione dell'algoritmo di backpropagation
### Qual È l’obiettivo Delle Tecniche Di Riduzione Di Dimensionalità?
L'obiettivo è quello di eseguire un mapping dallo spazio iniziale $\mathbb{R}^d$ ad uno spazio di dimensione inferiore tale che $\mathbb{R}^k,\quad k<d$.
Di fatto si va a scartare le informazioni non rilevanti o meno rilevanti per il problema di interesse per ottenere:
- alleviare i problemi legati alla curse of dimensionality, perchè operare in grandi spazi di dati richiede una mole di dati per il training elevata.
- una semplificazione dell'addestramento dei modelli; scartando dati futili o rumorosi può portare anche ad un miglioramento delle prestazioni del modello stesso.
Riducendo le dimensioni porta a combinare le dimensioni in maniera opportuna per ridurne la quantità.
## 17/07/2017
### Che Cosa Sono I Criteri Di Clustering? Fare Un Esempio
I criteri di clustering sono **funzioni obiettivo** che descrivono cosa si vuole ottenere da una partizione dei dati, specificando il **grado di ottimalità** di ogni soluzione ammissibile.  
Un algoritmo di clustering cerca quindi di trovare la partizione che **ottimizza** il criterio scelto.
Un esempio è la minimizzazione distanza dai centroidi (usado da K-Means):
minimizza la somma dei quadrati delle distanze dei pattern 𝐱 dai centroidi delle classi$$J_e=\sum_{i=1,...s}\sum_{x\in C_i}||x-\overline x_i||^2,\quad\overline x_i = \frac{1}{n_i}\sum_{x\in C_i}x$$
dove $C_i$ è l’i-esimo cluster, $n_i$ il numero di pattern che contiene e $\overline x_i$ il suo centroide (media).
### Come Opera Un Livello Di Pooling in Una CNN?
Un livello di **pooling** esegue un’**aggregazione locale** delle informazioni nel volume di input, producendo feature map di **dimensione spaziale inferiore**.  
L’obiettivo è quello di conferire **invarianza rispetto a piccole trasformazioni dell’input** (ad esempio traslazioni), mantenendo allo stesso tempo le informazioni più significative per la discriminazione dei pattern.

L’operazione di pooling viene applicata **indipendentemente a ciascuna feature map**, in modo tale che il **numero di feature map in uscita rimanga uguale** a quello in ingresso.  
Esempi comuni di pooling sono il **max pooling** e l’**average pooling**.
### Nell’ambito dell’apprendimento Automatico Cosa Si Intende per Generalizzazione E Overfitting?
Per generalizzazione si intende la capacità di trasferire l'elevata accuratezza raggiunta sul training set al validation set.
Si parla di overfitting quando la generalizzazione non ha luogo, ovvero quando si raggiunge un'elevata accuratezza sul training set ma alcontempo si otteggono scarsi risultati sul validation.
Spesso si ottiene overfitting con una piccola quantità di pattern nel training set, oppure quando vi è un'elevato grado di libertà del modello rispetto alla complessità del problema.
### Qual È l’obiettivo Di Una Tecnica Di Regressione?

L’obiettivo di una tecnica di **regressione** è stimare una funzione $f$ che approssimi la relazione tra le **variabili indipendenti** $x$ e la **variabile dipendente** $y$, a partire da un insieme di dati di training.

La funzione $f$ viene determinata minimizzando una **funzione di costo**, che misura l’errore tra i valori predetti $\hat{y} = f(x)$ e i valori reali $y$.  
Nel caso della regressione lineare, tale funzione di costo è tipicamente l’**errore quadratico medio (MSE)**.

Lo scopo finale è ottenere un modello che approssimi correttamente la relazione input–output e che sia in grado di **generalizzare** su nuovi dati.
## 22/01/2018
### Cosa Si Intende per Clustering Esclusivo E Clustering Soft (o Fuzzy). Quest’ultimo Che Vantaggi Può Avere?
- Clustering hard (esclusivo): un pattern è assegnato (in modo esclusivo) a un solo cluster.
- Clustering soft (fuzzy): i pattern appartengono a diversi cluster con un certo grado di appartenenza (es. tra 0 e 1). 
Fuzzy ha il vantaggio che è più efficace nel gestire pattern vicino al bordo di due o più clusters e outliers. L’assegnazione può diventare esclusiva scegliendo, per ogni pattern, il cluster verso cui il grado di appartenenza è massimo.
### Cosa È Possibile Apprendere Mediante Tecniche Di Reinforcement Learning? Fare Un Esempio

Mediante le tecniche di **Reinforcement Learning (RL)** è possibile apprendere una **politica di comportamento**, cioè una strategia che indica quale **azione** un agente deve compiere in ogni **stato** dell’ambiente, al fine di **massimizzare una ricompensa cumulativa** nel tempo.

Nel Reinforcement Learning l’apprendimento avviene tramite **interazione diretta con l’ambiente**: l’agente osserva lo stato corrente, seleziona un’azione, riceve una ricompensa e aggiorna la propria politica sulla base dell’esperienza accumulata. Non sono quindi disponibili etichette corrette a priori, ma solo segnali di rinforzo.

Un esempio tipico è l’apprendimento del comportamento di un **agente che gioca a un videogioco**, il quale impara progressivamente quali azioni intraprendere per massimizzare il punteggio finale, ricevendo ricompense positive o negative in base alle conseguenze delle proprie azioni.
### Definire Consa Si Intende per Apprendimento Supervisionato E Non Supervisionato
Per Learning supervisionato si intende quando le classi dei pattern del training set sono note a priori, quindi il training set è etichettato.
La situazione tipica del learning supervisionato è la classificazione o la regressione.
Il learning non supervisionato è, invece, quando il training set non è etichettato, una situazione tipica è il clustering. 
### Nelle SVM Non Lineari Cosa Si Intende per Kernel? Quali Sono I Kernel Più Utilizzati?
Nelle **SVM non lineari**, un **kernel** è una funzione che consente di calcolare il **prodotto scalare tra due pattern nello spazio delle feature** senza eseguire esplicitamente il mapping in uno spazio di dimensione più elevata.  
Formalmente, il kernel è definito come:
$$
K(x, x') = \langle \phi(x), \phi(x') \rangle
$$
dove $\phi(\cdot)$ è una funzione di mapping verso uno spazio delle feature ad alta (o infinita) dimensionalità.

L’uso del kernel permette di applicare algoritmi lineari in spazi non lineari tramite il cosiddetto **kernel trick**, rendendo computazionalmente fattibile la risoluzione del problema.
Sono funzioni kernel:
- RBF di ampiezza $\alpha$  
- Polinomio di grado $q$
## 15/02/2018
### Cosa Si Intende Con SVM Lineari? Cosa Sono Le Superfici Di Separazione Nel Caso d=2 E d=3?
Le **SVM lineari** sono classificatori che cercano una **funzione di decisione lineare** nello spazio delle feature, con l’obiettivo di separare le classi tramite un **iperpiano** che massimizza il **margine** tra i campioni delle diverse classi.
Nel caso lineare, la funzione di decisione ha la forma:
$$
f(x) = w^T x + b
$$
dove $w$ è il vettore dei pesi e $b$ è il termine di bias.  
La classificazione dipende dal segno di $f(x)$.
La **superficie di separazione** è definita dall’equazione:
$$
w^T x + b = 0
$$
ed è un oggetto geometrico la cui forma dipende dalla dimensionalità $d$ dello spazio delle feature.
#### Superficie Di Separazione per D = 2
Quando $d = 2$, lo spazio delle feature è bidimensionale e la superficie di separazione è una **retta** nel piano.  
La retta divide il piano in due semipiani, ciascuno associato a una classe.
#### Superficie Di Separazione per D = 3
Quando $d = 3$, lo spazio delle feature è tridimensionale e la superficie di separazione è un **piano**.  
Anche in questo caso, il piano divide lo spazio in due regioni, una per ciascuna classe.
### Rispetto a K-means, Quali Maggiori Flessibilità Consente l’approccio Di Clustering EM Con Gaussian Mixture?
Rispetto a **K-means**, l’approccio di clustering **EM con Gaussian Mixture** consente una maggiore flessibilità perché non assume cluster sferici di uguale dimensione e introduce una **modellazione probabilistica** dei dati.
In particolare, EM con Gaussian Mixture:
- permette di modellare cluster con **forme ellittiche**, grazie all’uso di **matrici di covarianza** complete;
- consente cluster con **dimensioni e orientamenti diversi**, mentre K-means assume varianza uguale in tutte le direzioni;
- fornisce un’**assegnazione soft** dei pattern ai cluster, esprimendo l’appartenenza in termini di **probabilità**, invece di un’assegnazione hard come in K-means;
- modella esplicitamente la distribuzione dei dati come una **combinazione di gaussiane**, anziché basarsi solo sulla inimizzazione della distanza dai centroidi.

Queste caratteristiche rendono il clustering EM con Gaussian Mixture più adatto a descrivere strutture complesse nei dati rispetto a K-means.


### Indicare Le Differenze Tra Reti Neurali Feedforward E Le Reti Neurali Ricorrenti, Disegnando Un Esempio Di Entrambe
- Feedforward: 
	nelle reti feedforward le connessioni collegano i neuroni di un livello con i neuroni di un livello successivo. Non sono consentite connessioni all’indietro o connessioni verso lo stesso livello.
- Ricorrenti: 
	nelle reti ricorrenti sono ammesse anche connessioni che vanno da un livello $i$ ad un livello $i-1$, questo per 

---
# Esercizi
## Classificatore Di Bayes Multinormale, Calcolare per Il Punto X #Ricapitato_1_volta

![[Primo Semestre Major/Machine Learning/imgs/Esercizi/1.png]]
### Svolgimento
$d$ => numero di classi. 
$p(x | w_i)$ => densità di probabilità condizionale di $w_i$ 
$p(x) = p(x|w_0)*p(w_0) + ... \\\ per \\\ ogni \\\ i \in \{0,...,d\}$ => densità di probabilità assoluta
$p(w_i|x) = \frac{p(x|w_i) * p(w_i)}{p(x)}$ => densità a posteri di $w_i$
Per trovare l'indice basta che prendi la i della densità a posteri maggiore.
![[es1.png]]
![[1-sol.png]]
## Calcolo Dei Pesi Di Una NN Durante Il front Propagation #Ricapitato_1_volta
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
## Tabella Multiclassificatore Con Somma, Prodotto, Massimo E Minimo
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/10.png]]
### Svolgimento
Questo è abbastanza semplice, basta prendere i dati dei singoli classificatore e applicare le singole strategie per riempire la tabella e poi prendi il massimo per determinare l'out delle singole strategie.
Le cifre in grassetto sono da calcolare per questo esercizio specifico:
![[es10.png]]
## Calcolo Del Numero Di Connessioni E Dei Pesi Di Un Livello Di Una CNN
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/11.png]]
Ogni neurone del livello di output (96 × 55 × 55) è connesso con tanti neuroni del livello di input pari alla dimensione del filtro (3 × 11 × 11). Pertanto il numero totale di connessioni è (96 × 55 × 55) ∙ (3 × 11 × 11) = 105 415 200. Il numero totale di pesi, invece, risulta molto più piccolo giacché in una CNN i pesi di ciascun filtro sono condivisi da tutti i neuroni contenuti in una stessa feature map. Visto che il numero di feature map è uguale a 96, ed il numero di input per ciascun filtro è pari a (3 × 11 × 11), il numero totale di pesi (senza considerare il bias) è (3 × 11 × 11) × 96 = 34 848.
## Classificatore Di Bayes Multinormale, Calcolare per Il Punto X VARIANTE
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/12.png]]
### Svolgimento
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/13.png]]
## Calcolo Del Numero Di Addizioni E Moltiplicazioni in Un NN VARIANTE Del MLP
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/14.png]]
### Svolgimento
![[es14.png]]
## Calcolo Del Numero Di Connessioni E Dei Pesi Di Un Livello Di Una CNN VARIANTE Con Anche Un MLP
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/15.png]]
### Svolgimento
![[es15.png]]
## Calcolo Del Numero Di Run E Della Partizione Del Training Set E Validation Set Durante L'algoritmo K-fold Cross-Validation
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/16.png]]
### Svolgimento
![[es16.png]]
## Tabella Borda Count Di Un Multiclassificatore
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/17.png]]
### Svolgimento
Qui è importante la classifica che il testo fa, quindi:
- prima posizione => vale 10
- seconda posizione => vale 7
- terza posizione => vale 5
- quarta posizione => vale 2
Avendo bene chiara questa classifica bisogna guardare la tabella fornita dall'esercizio, esempio:
- prendiamo come esempio la classe 4 per il primo pattern:
	$C_1$ la classifica come prima, quindi 10, $C_2$ come seconda quindi 7 e $C_3$ come seconda quindi sempre 7, allora nella tabella da completare sotto la classe 4 scriviamo la somma di questi valori quindi 24.
Questo procedimento lo dobbiamo fare per tutte le classi e per tutti i pattern ottenendo la seguente tabella:

|       | 1   | 2   | 3   | 4   |
| ----- | --- | --- | --- | --- |
| $p_1$ | 20  | 22  | 6   | 24  |
| $p_2$ | 27  | 22  | 17  | 6   |
| $p_3$ | 6   | 22  | 27  | 17  |
Ottenuta questa tabella bisogna dire la classe predetta, quindi basta prendere i massimi valori delle classi per ogni pattern, quindi:
- $p_1$ => 4 classe con 24
- $p_2$ => 1 classe con 27
- $p_3$ => 3 classe con 27
## Calcolo Del Numero Di Pesi Di Una MLP CON BAYAS (simile Ma Diverso Dal Calcolo Che È Stato Fatto Nell'esercizio precedente)
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/18.png]]
### Svolgimento
il calcolo è praticamente uguale a quello fatto qua [[#Calcolo Del Numero Di Addizioni E Moltiplicazioni in Un NN VARIANTE Del MLP]] ma è diverso perchè c'è il bayas quindi bisogna fare questo:
$(6+1)*8 + (8+1)*5 = 101$ che è il numero di pesi, la formula è uguale ma c'è quel $+1$ aggiunto al numero di neuroni del layer $i$ che va poi moltiplicato con il layer $i+1$ che rappresenta il bayas.
Motivazione? in una MLP il numero di pesi è pari al numero di connessioni intra layer, con l'aggiunta del +1 per il bayas.
## Capire la Classe Predetta Da K-NN Dato Un Grafo E Dei Valori Di K
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/19.png]]
### Svolgimento
![[es19.png]]
## Formulare Il Problema Di Multiple Linear Regressor Definendo X Ed Y
![[es20.png]]
### Svolgimento
Come spiegato anche nella domanda di teoria, la pratica si fa nell'esatto modo:
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/20.png]]