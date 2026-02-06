# <a href="http://bias.csr.unibo.it/maltoni/ml/SoluzioniEsami/">Prove D'esame</a> Domande Teoriche, Ripetute Con Meno Frequenza
## 07/12/2016
### Dare la Definizione Di Training, Validation E Test Set E Discutere Una Possibile Suddivisione Dei Dati Nei Tre Insiemi. #Ricapitato_N_volta
_Per training set_ si intende una partizione del dataset atta all'addestramento interno del modello, quindi all'aggiornamento dei pesi e dei coefficenti del modello.
_Per Validation set_ si intende un sottoinsieme del dataset utilizzato per l'ottimizzazione degli iperparametri del modello, usato anche per attuare tecniche come early-stopping.
Mentre per _Test set_ si intende una partizione del dataset usata solo alla fine per stimare le prestazioni finali del modello.
Per la suddivisione si tende ad usare una distribuzione standard come segue:
-  Training set 60-70%
-  Validation set 15-20%
-  Test set 15-20%

Esempio 70%|15%|15%.
Ma può essere messa in atto quando si ha un dataset di medi/grandi dimensioni, se invece si ha a disposizione pochi dati si può decidere di non avere un validation set a favore dell'applicazione della k-fold  cross validation per ottimizzare gli iper parametri.
### Nella Formulazione dell’SVM Lineare la Funzione Obiettivo Richiede Di Massimizzare Il Margine. L’ottimizzazione È Però Vincolata; in Cosa Consistono I Vincoli? Quanti Sono? #Ricapitato_1_volta
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
#### Descrivere Le Principali Criticità E Limitazioni dell’algoritmo Di Clustering K-means. #Ricapitato_1_volta
1. Necessità di fornire k a priori
	Ovvero, K-means richiede che k (numero di cluster) venga definito e fornito come dato di input, quindi richiede di sapere il numero di cluster a priori, se viene fornito un k non consono ai dati il risultato ottenuto non potrà essere ottimale.
2. Sensibilità all'inizializzazione
	K-means richiede anche i centroidi dei cluster come input, spesso vengono scelti in maniera randomica, configurazioni diverse di quest'ultimi portano a risultati diversi.
	L'algoritmo può convergere verso minimi locali, e non globali, portando risultati non ottimali.
3. Forma dei cluster
	K-means funziona in maniera corretta con cluster della stessa dimensione, sferici e convessi, con cluster di forme complesse o di dimensioni diverse si possono ottenere risultati non affidabili.
4. Limitazioni basate sulla misura della distanza intra-cluster
	L’uso tipico della distanza euclidea rende K-means poco adatto a dati non numerici o a contesti in cui tale misura non rappresenta correttamente la similarità tra i pattern.
##### Nell’ambito Di CNN, Che Cosa Si Intende per Connessioni Locali E Condivisione Di Pesi? #Ricapitato_1_volta
Per Connessioni locali si intende che ogni neurone del layer convoluzionale è collegato ad una regione locale dell'immagine e non a tutta come accade nelle reti fully connected, permettendo di ridurre il costo computazionale ed il numero di parametri, questo viene fatto inoltre per rilevare con maggiore precisione dei pattern locali come bordi o texture.

Per Condivisione di pesi si intende l'utilizzo degli stessi pesi, quali filtri o kernel, per posizioni diverse dell'input, producendo gli stessi risultati per un determinato pattern.
Nella pratica lo stesso filtro viene fatto passare su tutte le zone locali dell'immagine di input producendo una feature map, rispondendo allo stesso pattern indipendentemente dalla sua posizione nell'immagine.
## 20/1/2017
### Qual È Il Principio Su Cui Si Basa Il Classificatore SVM? Cosa Si Intende per Margine? #Ricapitato_1_volta
Il Support Vector Machine si basa sul principio di individuare l'iperpiano di separazione ottimale per, appunto, separare le classi fra loro con distanza maggiore dall'iperpiano individuato.
Il margine è la minima distanza tra i support vectors delle due classi del training set dall'iperpiano, ovvero i campioni più vicini all'iperpiano individuato delle classi.
Il massimizzare il margine è legata alla generalizzazione, di fatti se le classi del training set hanno un ampio margine, quindi sono facilmente separabili, ci si aspetta che anche quel test set lo siano.
### Perché Le Recenti Reti Neurali Deep Sono Più Efficaci Delle MLP a Tre Livelli? #Ricapitato_N_volta
Le recenti reti neurali deep sono più efficaci delle MLP a tre livelli perché la **profondità** consente di rappresentare alcune funzioni in modo **molto più efficiente**.  
Sebbene il _universal approximation theorem_ garantisca che una MLP con un solo livello hidden possa approssimare qualsiasi funzione, **l’esistenza di una soluzione non implica efficienza**: esistono funzioni che possono essere rappresentate con **complessità polinomiale usando più livelli**, ma che richiedono **complessità esponenziale** se realizzate con un livello in meno.
L'organizzazione gerarchica delle DNN porta con se diversi vantaggi:
- condividere e riusare le informazioni già estratte su più livelli
- selezionare feature più astratte, scartando eventuali informazioni inutili durante il processo
- modellare fenomeni più complessi, grazie alla gerarchia presente in esse che rispecchia in maniera più accurata sistema visivo umano.
### Fare Esempi Pratici Di Pattern Numerici, Categorici E Di Sequenze #Ricapitato_N_volta
- Numerici
	1. Misure numeriche continue di un prodotto, ad esempio la concentrazione di solfati in un vino per predirne la qualità.
	2. Valori di consumo energetico di un calorifero utilizzati per stimare i costi annuali.
- Categorici
	1. In un dataset di persone, il genere (es. uomo/donna), rappresentato come variabile categorica binaria.
	2. La regione o provincia di provenienza di un vino, rappresentata come etichetta discreta (stringa o codice).
- Sequenze
	1. Un video di sorveglianza, visto come una sequenza temporale di immagini.
	2. Una traccia musicale, rappresentata come sequenza temporale di campioni audio per la classificazione del genere.
### Nella Regressione Cosa Si Intende per Variabile Indipendente E Variabile Dipendente? #Ricapitato_1_volta
Nella regressione per variabile indipendente si intende la variabile, o insieme di variabili, di input x mentre per variabile dipendente si intende la variabile di output y, quindi quello che il modello di regressione produce.
Inoltre si può dire che la variabile indipendente x si considera sempre come priva di errori mentre la variabile dipendente y va sempre considerata come influenzata da errori.
## 17/2/2017
### Cosa Si Intende per Iperparametri? Fornire Esempi Pratici Di Iperparametri. Come Si Ottimizzano? #Ricapitato_N_volta
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
### Come Si Imposta Un Problema Di Multiple Linear Regression? Come Sono Popolati X, Y E $\beta$? #Ricapitato_1_volta
Nel seguente caso abbiamo che la variabile indipendente è un vettore tale che $x\in \mathbb{R}^d$.
Dato un training set composto da $n$ pattern, per impostare il problema dobbiamo costruire $X$ , $y$ e $\beta$ nel seguente modo:
- per quanto riguarda $X$, che ha forma $X\in \mathbb{R}^{n × (d+1)}$ viene calcolata inserendo sulle righe i $n$ pattern tralasciando l'ultima colonna che viene riempita da $1$ per rappresentare l'intercetta.
- $y$ invece è un vettore che contiene $y_i$ per ogni $i\in \{1,...,n\}$   
- $\beta$, che è della forma $\mathbb{R}^{d+1}$, raccoglie i coefficienti del modello, compreso il temine noto.
Quindi otteniamo che $y=X\beta$ oppure $y_i = \sum^{d+1}_{j=1}x_{i,j}\beta_{j}$
Poiché tipicamente $n>d+1$, il sistema è **sovradeterminato** e i parametri $\beta$ vengono stimati risolvendo un problema di **minimi quadrati (Least Squares)**.
### Che cos’è Il Learning Rate nell’ambito dell’apprendimento Di Reti Neurali? Cosa Succede Se Viene Scelto Un Learning Rate Troppo Piccolo O Troppo Grande? #Ricapitato_1_volta
Il learning rate è un iperparametro che regola l'ampiezza di aggiornamento dei pesi durante la fase di training di una rete neurale tramite backpropagation e gradient descent.
Nello specifico $\eta$ rappresenta l'ampiezza del passo di discesa segue la direzione opposta al gradiente della funzione di errore, questo rende, di fatto, la scelta di questo iperparametro cruciale, infatti:
- quando si sceglie un $\eta$ troppo piccolo si ottiene che la rete convergerà più lentamente con maggiori probabilità di rimanere bloccati in un minimo locale
- invece quando lo si sceglie troppo grande otterremo delle oscillazioni indesiderate dei pesi facendo divergere il processo di training 
### Quali Sono I Più Noti Algoritmi Di Clustering? #Ricapitato_1_volta
Tra le Famiglie degli algoritmi abbiamo:
- **Clustering basato su centroidi**
    - **K-means**  
        È uno degli algoritmi di clustering più noti. Suddivide i dati in k cluster minimizzando la varianza intra-cluster, utilizzando la distanza euclidea e centroidi aggiornati iterativamente.
    - Expectation - Maximization (Gaussian Mixture)
- **Clustering gerarchico**
- **Clustering basato sulla densità**
    - **DBSCAN**  
        Identifica cluster come regioni ad alta densità di punti ed è in grado di individuare outlier come rumore.
## 23/06/2017
### Nel Classificatore SVM Cosa Sono I Support Vectors?
Sono i pattern che giacciono sul margine, tali pattern definiscono completamente la soluzione del problema indipendentemente dalla dimensione $d$ e dal numero di pattern $n$.
Il problema può essere direttamente espresso come funzione di tali pattern.
### Qual È l’idea Di Base Di Base dell’algoritmo Di Clustering EM Con Gaussian Mixture? #Ricapitato_1_volta
L’idea di base dell’algoritmo **EM (Expectation–Maximization) con Gaussian Mixture** è modellare i dati come generati da una **combinazione (mixture) di distribuzioni gaussiane**, ciascuna delle quali rappresenta un cluster.

Ogni cluster è descritto da una gaussiana caratterizzata da **media**, **covarianza** e **peso**, e l’appartenenza di un pattern a un cluster è espressa in modo **probabilistico**, non deterministico.
L’algoritmo procede in modo **iterativo**, alternando due fasi:
- **Expectation step (E-step)**: si stima, per ogni pattern, la **probabilità di appartenenza** a ciascuna gaussiana, dati i parametri correnti del modello;
- **Maximization step (M-step)**: si aggiornano i **parametri delle gaussiane** massimizzando la **verosimiglianza** dei dati pesata dalle probabilità stimate nell’E-step.
Questo processo viene ripetuto fino a convergenza, portando a una stima dei parametri che **massimizza la likelihood** del modello sui dati osservati .
### Quali Sono Le Più Comuni Funzioni Di Attivazione Utilizzate per Neuroni Artificiali? Perché È Necessario Che Siano Non-lineari E Differenziabili (esistenza derivata)? #Ricapitato_1_volta
- Relu
- Eli
- tanh
- sigmoid
- maxout

Le funzioni di attivazioni devono essere non lineari e differenziabili perchè:
- Non lineare per permettere alla rete di eseguire un mapping complesso delle informazioni di input
- Differenziabile per permettere l'applicazione dell'algoritmo di backpropagation
### Qual È l’obiettivo Delle Tecniche Di Riduzione Di Dimensionalità? #Ricapitato_1_volta
L'obiettivo è quello di eseguire un mapping dallo spazio iniziale $\mathbb{R}^d$ ad uno spazio di dimensione inferiore tale che $\mathbb{R}^k,\quad k<d$.
Di fatto si va a scartare le informazioni non rilevanti o meno rilevanti per il problema di interesse per ottenere:
- alleviare i problemi legati alla curse of dimensionality, perchè operare in grandi spazi di dati richiede una mole di dati per il training elevata.
- una semplificazione dell'addestramento dei modelli; scartando dati futili o rumorosi può portare anche ad un miglioramento delle prestazioni del modello stesso.
Riducendo le dimensioni porta a combinare le dimensioni in maniera opportuna per ridurne la quantità.
## 17/07/2017
### Che Cosa Sono I Criteri Di Clustering? Fare Un Esempio #Ricapitato_1_volta
I criteri di clustering sono **funzioni obiettivo** che descrivono cosa si vuole ottenere da una partizione dei dati, specificando il **grado di ottimalità** di ogni soluzione ammissibile.  
Un algoritmo di clustering cerca quindi di trovare la partizione che **ottimizza** il criterio scelto.
Un esempio è la minimizzazione distanza dai centroidi (usado da K-Means):
minimizza la somma dei quadrati delle distanze dei pattern 𝐱 dai centroidi delle classi$$J_e=\sum_{i=1,...s}\sum_{x\in C_i}||x-\overline x_i||^2,\quad\overline x_i = \frac{1}{n_i}\sum_{x\in C_i}x$$
dove $C_i$ è l’i-esimo cluster, $n_i$ il numero di pattern che contiene e $\overline x_i$ il suo centroide (media).
### Come Opera Un Livello Di Pooling in Una CNN? #Ricapitato_1_volta
Un livello di **pooling** esegue un’**aggregazione locale** delle informazioni nel volume di input, producendo feature map di **dimensione spaziale inferiore**.  
L’obiettivo è quello di conferire **invarianza rispetto a piccole trasformazioni dell’input** (ad esempio traslazioni), mantenendo allo stesso tempo le informazioni più significative per la discriminazione dei pattern.

L’operazione di pooling viene applicata **indipendentemente a ciascuna feature map**, in modo tale che il **numero di feature map in uscita rimanga uguale** a quello in ingresso.  
Esempi comuni di pooling sono il **max pooling** e l’**average pooling**.
### Nell’ambito dell’apprendimento Automatico Cosa Si Intende per Generalizzazione E Overfitting? #Ricapitato_N_volta
Per generalizzazione si intende la capacità di trasferire l'elevata accuratezza raggiunta sul training set al validation set.
Si parla di overfitting quando la generalizzazione non ha luogo, ovvero quando si raggiunge un'elevata accuratezza sul training set ma alcontempo si otteggono scarsi risultati sul validation.
Spesso si ottiene overfitting con una piccola quantità di pattern nel training set, oppure quando vi è un'elevato grado di libertà del modello rispetto alla complessità del problema.
### Qual È l’obiettivo Di Una Tecnica Di Regressione? #Ricapitato_N_volta

L’obiettivo di una tecnica di **regressione** è stimare una funzione $f$ che approssimi la relazione tra le **variabili indipendenti** $x$ e la **variabile dipendente** $y$, a partire da un insieme di dati di training.

La funzione $f$ viene determinata minimizzando una **funzione di costo**, che misura l’errore tra i valori predetti $\hat{y} = f(x)$ e i valori reali $y$.  
Nel caso della regressione lineare, tale funzione di costo è tipicamente l’**errore quadratico medio (MSE)**.

Lo scopo finale è ottenere un modello che approssimi correttamente la relazione input–output e che sia in grado di **generalizzare** su nuovi dati.
## 22/01/2018
### Cosa Si Intende per Clustering Esclusivo E Clustering Soft (o Fuzzy). Quest’ultimo Che Vantaggi Può Avere? #Ricapitato_N_volta
- Clustering hard (esclusivo): un pattern è assegnato (in modo esclusivo) a un solo cluster.
- Clustering soft (fuzzy): i pattern appartengono a diversi cluster con un certo grado di appartenenza (es. tra 0 e 1). 
Fuzzy ha il vantaggio che è più efficace nel gestire pattern vicino al bordo di due o più clusters e outliers. L’assegnazione può diventare esclusiva scegliendo, per ogni pattern, il cluster verso cui il grado di appartenenza è massimo.
### Cosa È Possibile Apprendere Mediante Tecniche Di Reinforcement Learning? Fare Un Esempio #Ricapitato_1_volta
Mediante le tecniche di **Reinforcement Learning (RL)** è possibile apprendere una **politica di comportamento**, cioè una strategia che indica quale **azione** un agente deve compiere in ogni **stato** dell’ambiente, al fine di **massimizzare una ricompensa cumulativa** nel tempo.

Nel Reinforcement Learning l’apprendimento avviene tramite **interazione diretta con l’ambiente**: l’agente osserva lo stato corrente, seleziona un’azione, riceve una ricompensa e aggiorna la propria politica sulla base dell’esperienza accumulata. Non sono quindi disponibili etichette corrette a priori, ma solo segnali di rinforzo.

Un esempio tipico è l’apprendimento del comportamento di un **agente che gioca a un videogioco**, il quale impara progressivamente quali azioni intraprendere per massimizzare il punteggio finale, ricevendo ricompense positive o negative in base alle conseguenze delle proprie azioni.
### Definire Consa Si Intende per Apprendimento Supervisionato E Non Supervisionato. #Ricapitato_N_volta
Per Learning supervisionato si intende quando le classi dei pattern del training set sono note a priori, quindi il training set è etichettato.
La situazione tipica del learning supervisionato è la classificazione o la regressione.
Il learning non supervisionato è, invece, quando il training set non è etichettato, una situazione tipica è il clustering. 
### Nelle SVM Non Lineari Cosa Si Intende per Kernel? Quali Sono I Kernel Più Utilizzati? #Ricapitato_1_volta
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
### Cosa Si Intende Con SVM Lineari? Cosa Sono Le Superfici Di Separazione Nel Caso d=2 E d=3? #Ricapitato_1_volta
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
### Rispetto a K-means, Quali Maggiori Flessibilità Consente l’approccio Di Clustering EM Con Gaussian Mixture? #Ricapitato_N_volta
Rispetto a **K-means**, l’approccio di clustering **EM con Gaussian Mixture** consente una maggiore flessibilità perché non assume cluster sferici di uguale dimensione e introduce una **modellazione probabilistica** dei dati.
In particolare, EM con Gaussian Mixture:
- permette di modellare cluster con **forme ellittiche**, grazie all’uso di **matrici di covarianza** complete;
- consente cluster con **dimensioni e orientamenti diversi**, mentre K-means assume varianza uguale in tutte le direzioni;
- fornisce un’**assegnazione soft** dei pattern ai cluster, esprimendo l’appartenenza in termini di **probabilità**, invece di un’assegnazione hard come in K-means;
- modella esplicitamente la distribuzione dei dati come una **combinazione di gaussiane**, anziché basarsi solo sulla minimizzazione della distanza dai centroidi.

Queste caratteristiche rendono il clustering EM con Gaussian Mixture più adatto a descrivere strutture complesse nei dati rispetto a K-means.
### Cosa Si Intende per K-fold Cross-validation? #Ricapitato_1_volta_con_variante\[Quali Sono I Vantaggi Rispetto a Un Semplice Split a due Dei Dati Di training?\]
La **K-fold cross-validation** è una tecnica di **valutazione delle prestazioni di un modello** che consiste nel suddividere il dataset disponibile in **K sottoinsiemi (fold)** di dimensione approssimativamente uguale.
Il procedimento è il seguente:
- il modello viene addestrato **K volte**;
- a ogni iterazione, **K−1 fold** vengono utilizzati come **training set** e il fold rimanente come **validation set**;
- il processo viene ripetuto fino a quando **ogni fold è stato usato una volta come validation set**.
Le prestazioni finali del modello sono ottenute come **media delle prestazioni** calcolate sui K esperimenti.
La K-fold cross-validation permette di ottenere una **stima più affidabile della capacità di generalizzazione** del modello rispetto a una singola suddivisione training/validation, soprattutto quando il dataset disponibile è limitato.
### Indicare Le Differenze Tra Reti Neurali Feedforward E Le Reti Neurali Ricorrenti, Disegnando Un Esempio Di Entrambe #Ricapitato_1_volta
- Feedforward: 
	nelle reti feedforward le connessioni collegano i neuroni di un livello con i neuroni di un livello successivo. Non sono consentite connessioni all’indietro o connessioni verso lo stesso livello.
- Ricorrenti: 
	nelle reti ricorrenti sono previste connessioni di feedback (in genere verso neuroni dello stesso livello, ma anche all’indietro). Questo complica notevolmente il flusso delle informazioni e l’addestramento, richiedendo di considerare il comportamento in più istanti temporali.Come si imposta un problema di multiple linear regression? Come sono popolati
	Questo tipo di reti presenzia un effetto memoria, molto utile quando il tipo di dato è del genere delle sequenze.
#### Disegno
[[reti feed and ricorrenti]]
## 22/06/18
### Indicare Le Principali “stagioni” Nello Sviluppo dell’intelligenza Artificiale E Machine Learning #Ricapitato_N_volta
### Definire I Problemi Di Classificazione E Regressione Evidenziandone Le Differenze E Fornendo per Ciascuno Esempi Reali Della Loro Applicazione. #Ricapitato_1_volta
Nel Machine Learning supervisionato si distinguono principalmente due tipologie di problemi: **classificazione** e **regressione**, che differiscono per la natura della variabile di output da predire.
#### Problema Di Classificazione
Un problema di **classificazione** consiste nel determinare, a partire da un vettore di input $x$, la **classe discreta** $y$ a cui il pattern appartiene, scelta da un insieme finito di etichette.

Formalmente, l’obiettivo è apprendere una funzione:
$$
f: \mathbb{R}^d \rightarrow \{c_1, c_2, \dots, c_K\}
$$
##### Esempi Applicativi
- classificazione di email in *spam* o *non spam*;
- riconoscimento di cifre scritte a mano;
- diagnosi medica (malato / sano);
- riconoscimento di oggetti o persone in immagini.
#### Problema Di Regressione
Un problema di **regressione** ha come obiettivo la stima di una **variabile continua** $y \in \mathbb{R}$ a partire da un insieme di variabili indipendenti $x$.

Formalmente, si apprende una funzione:
$$
f: \mathbb{R}^d \rightarrow \mathbb{R}
$$
La funzione viene stimata minimizzando una funzione di errore, tipicamente l’**errore quadratico medio**.
##### Esempi Applicativi
- previsione del prezzo di un immobile;
- stima del consumo energetico;
- previsione della temperatura;
- previsione di vendite o domanda futura.
#### Differenze Principali Tra Classificazione E Regressione
- **Tipo di output**:
  - classificazione → valori discreti (etichette);
  - regressione → valori continui.
- **Obiettivo**:
  - classificazione → assegnare un pattern a una classe;
  - regressione → stimare una relazione quantitativa tra input e output.
- **Misure di errore**:
  - classificazione → accuratezza, errore di classificazione;
  - regressione → errore quadratico medio, errore assoluto medio.
Entrambi i problemi rientrano nell’apprendimento supervisionato, ma si differenziano per la natura dell’informazione che il modello è chiamato a predire.
### Come Si Calcola l’attivazione (net) Di Un Neurone Artificiale? #Ricapitato_1_volta
L’attivazione (o **net input**) di un neurone artificiale è calcolata come la **somma pesata degli input**, a cui si aggiunge un termine di **bias**.
La formula è:
$$
net = \sum_{i=1}^{n} w_i x_i + b
$$
dove:
- $x_i$ sono gli **input** provenienti dai neuroni dello strato precedente;
- $w_i$ sono i **pesi sinaptici** associati a ciascun input;
- $b$ è il **bias**, che permette di traslare la funzione di decisione.
Il valore $net$ rappresenta l’ingresso della **funzione di attivazione**, che produce l’output del neurone.
### Indicare Le Differenze Tra Le Tecniche Di Riduzione Di Dimensionalità PCA E LDA? #Ricapitato_N_volta
La **PCA (Principal Component Analysis)** e la **LDA (Linear Discriminant Analysis)** sono entrambe tecniche di riduzione di dimensionalità, ma si basano su **obiettivi e criteri differenti**.
#### Differenze Principali
- **Tipo di apprendimento**:
  - PCA → non supervisionata;
  - LDA → supervisionata.
- **Obiettivo**:
  - PCA → preservare la massima varianza dei dati;
  - LDA → massimizzare la separabilità tra le classi.
- **Uso delle classi**:
  - PCA → non utilizza le etichette;
  - LDA → utilizza le etichette.
- **Dimensione dello spazio ridotto**:
  - PCA → scelta liberamente;
  - LDA → al più $K - 1$, con $K$ numero di classi.
La PCA è indicata quando non si dispone di informazioni sulle classi o si vuole una rappresentazione compatta dei dati, mentre la LDA è preferibile quando l’obiettivo è migliorare la **discriminazione tra classi**.
## 16/07/2018
### Quali Sono Le Condizioni Necessarie Affinché Le Tecniche Di Deep Learning Siano Più Efficaci Di Altri Approcci Di Machine Learning? #Ricapitato_1_volta

Le tecniche di **Deep Learning** risultano più efficaci rispetto ad altri approcci di Machine Learning quando sono soddisfatte alcune **condizioni fondamentali**, legate ai dati, al modello e alle risorse computazionali.
#### Grande Disponibilità Di Dati
Le reti neurali profonde richiedono **grandi quantità di dati** per poter apprendere efficacemente un elevato numero di parametri.
In presenza di dataset piccoli, modelli più semplici tendono a generalizzare meglio.
#### Elevata Complessità Del Problema
Il Deep Learning è particolarmente efficace quando il problema presenta:
- **strutture complesse e non lineari**;
- **rappresentazioni gerarchiche** dei dati (ad esempio immagini, audio, testo).
In questi casi, la profondità della rete consente di apprendere automaticamente **feature sempre più astratte**.
#### Adeguata Potenza Computazionale
L’addestramento di reti profonde è computazionalmente costoso e richiede:
- hardware adeguato (es. GPU);
- tempi di addestramento sufficienti.
Senza risorse computazionali adeguate, il Deep Learning non risulta praticabile.
#### Architetture E Tecniche Di Addestramento Adeguate
L’efficacia del Deep Learning dipende anche dall’uso di:
- architetture appropriate al problema;
- tecniche che facilitano l’addestramento di reti profonde e migliorano la generalizzazione.

In sintesi, il Deep Learning è più efficace quando si dispone di **molti dati**, **problemi complessi**, **potenza di calcolo sufficiente** e **modelli profondi ben progettati**. In assenza di queste condizioni, approcci di Machine Learning più semplici possono risultare preferibili.
### La Formula Di Distanza Di Un Pattern dall’iperpiano SVM Dipende Da Tutti I Pattern Di Training? #Ricapitato_1_volta
La **formula della distanza di un pattern dall’iperpiano** risultante dal training di una **SVM** dipende **solo da una parte dei pattern del training set**, e non da tutti.
In particolare, dipende esclusivamente dai **support vector**.
Infatti, l’iperpiano di separazione ottimale è determinato unicamente da quei pattern che:
- giacciono sul margine;
- oppure violano il margine nel caso di **soft margin**.

Tutti gli altri pattern del training set, che si trovano a distanza maggiore dal margine, **non influenzano la posizione dell’iperpiano** e non compaiono nella formula della funzione di decisione.
Questo avviene perché, nella formulazione duale della SVM, solo i support vector hanno **moltiplicatori di Lagrange non nulli**; di conseguenza, solo essi contribuiscono alla definizione del vettore dei pesi e quindi al calcolo della distanza dall’iperpiano.
In conclusione, la distanza di un pattern dall’iperpiano SVM dipende **solo dai support vector**, rendendo la SVM un modello sparso.
### Qual È la Funzione Obiettivo in Formato Matriciale Della Multiple Linear Regression? #Ricapitato_N_volta
Nella **Multiple Linear Regression**, l’obiettivo è stimare il vettore dei parametri $\beta$ in modo da minimizzare l’errore tra i valori osservati $y$ e quelli predetti dal modello lineare.
Dato:
- $X \in \mathbb{R}^{n \times (d+1)}$ la **matrice dei dati** (con la colonna di 1 per l’intercetta),
- $y \in \mathbb{R}^{n}$ il **vettore delle osservazioni**,
- $\beta \in \mathbb{R}^{d+1}$ il **vettore dei parametri**,

il modello è:
$$
\hat{y} = X\beta
$$
La **funzione obiettivo** (criterio dei minimi quadrati) in forma matriciale è:
$$
J(\beta) = \| y - X\beta \|^2
$$
ovvero, in forma esplicita:
$$
J(\beta) = (y - X\beta)^T (y - X\beta)
$$

Questa funzione misura la **somma dei quadrati degli errori** tra i valori reali e quelli stimati dal modello, e viene minimizzata per ottenere la stima dei parametri $\beta$.
### Indicare la Formula Di Bayes per la Probabilità a Posteriori, Definendo I Termini #Ricapitato_1_volta
Guarda [[#Classificatore Di Bayes Multinormale, Calcolare per Il Punto X Ricapitato1volta]]
### Descrivere a Grandi Linee Un Classificatore Random Forest #Ricapitato_1_volta
Un **Random Forest** è un classificatore basato su un **insieme (ensemble) di alberi di decisione**.  
L’idea di base è combinare le decisioni di più modelli deboli (alberi) per ottenere un classificatore più robusto e accurato.

Il funzionamento, a grandi linee, è il seguente:
- vengono addestrati molti **alberi di decisione** su diversi sottoinsiemi del training set, ottenuti tramite **campionamento bootstrap**;
- a ogni nodo di ciascun albero, la scelta della feature su cui effettuare lo split avviene considerando solo un **sottoinsieme casuale delle feature**;
- la classificazione finale è ottenuta tramite **voto di maggioranza** delle predizioni dei singoli alberi.

Questo approccio riduce la **varianza** del modello rispetto a un singolo albero e limita il rischio di overfitting.
### Descrivere a Grandi Linee l’approccio Di Classificazione AdaBoost. #Ricapitato_1_volta
**AdaBoost (Adaptive Boosting)** è un metodo di **boosting**, che costruisce un classificatore forte combinando iterativamente più **classificatori deboli**
Il procedimento è il seguente:
- inizialmente tutti i pattern del training set hanno lo stesso peso;
- a ogni iterazione viene addestrato un classificatore debole sui dati pesati;
- i pattern **mal classificati** ricevono un peso maggiore, mentre quelli correttamente classificati ricevono un peso minore;
- ogni classificatore viene pesato in base alla sua accuratezza.

La decisione finale è ottenuta tramite una **combinazione pesata** delle decisioni dei classificatori deboli.  
AdaBoost si concentra progressivamente sui pattern più difficili da classificare.
### Descrivere a Grandi Linee l’algoritmo Di Clustering K-means. #Ricapitato_1_volta
L’algoritmo di **K-means** è una tecnica di **clustering non supervisionato** che ha come obiettivo la suddivisione di un insieme di pattern in **K cluster**, minimizzando la distanza intra-cluster.
L’algoritmo procede in modo iterativo secondo i seguenti passi:
1. **Inizializzazione**  
   Si sceglie il numero di cluster $K$ e si inizializzano i centroidi dei cluster, solitamente in modo casuale.
2. **Assegnazione dei pattern**  
   Ogni pattern viene assegnato al cluster il cui centroide è il più vicino, secondo una misura di distanza (tipicamente la distanza euclidea).
3. **Aggiornamento dei centroidi**  
   Per ciascun cluster si ricalcola il centroide come la **media dei pattern** assegnati al cluster.
4. **Iterazione fino a convergenza**  
   I passi di assegnazione e aggiornamento vengono ripetuti fino a quando le assegnazioni dei pattern o i centroidi non cambiano più.

L’algoritmo converge a un **minimo locale** della funzione obiettivo, che è la somma dei quadrati delle distanze dei pattern dai rispettivi centroidi.
### Come È Definita la Funzione Di Attivazione Relu? Perché Consente Di Addestrare Reti Neurali Profonde Limitando Il Problema Del Vanishing Gradient? #Ricapitato_1_volta
La funzione di attivazione **ReLU (Rectified Linear Unit)** è definita come:
$$
\text{ReLU}(x) = \max(0, x)
$$

Questa funzione restituisce:
- 0 per valori negativi dell’input;
- il valore dell’input stesso per valori positivi.

La ReLU consente di addestrare reti neurali profonde limitando il problema del **vanishing gradient** perché:
- per input positivi, la derivata è **costante e non nulla**;
- il gradiente non tende a zero durante la backpropagation, a differenza di funzioni sigmoidi o tangente iperbolica;
- ciò permette una propagazione più efficace del gradiente negli strati profondi della rete.
Di conseguenza, l’uso della ReLU rende l’addestramento delle **Deep Neural Networks** più stabile ed efficiente.
### Che Cosa Si Intende per Clustering? Fare Esempi Di Applicazioni. #Ricapitato_1_volta
Il **clustering** è una tecnica di **apprendimento non supervisionato** che ha come obiettivo la suddivisione di un insieme di pattern in **gruppi (cluster)**, in modo tale che i pattern appartenenti allo stesso cluster siano **più simili tra loro** rispetto a quelli appartenenti a cluster diversi, secondo una opportuna misura di similarità o distanza.

Nel clustering non sono disponibili etichette di classe a priori: la struttura dei gruppi viene individuata direttamente a partire dai dati.
Alcuni esempi di applicazioni del clustering sono:
- **Segmentazione di clienti** in ambito marketing, per individuare gruppi di utenti con comportamenti di acquisto simili;
- **Analisi di immagini**, ad esempio per la segmentazione di regioni con caratteristiche simili;
- **Raggruppamento di documenti** o pagine web in base al contenuto;
- **Bioinformatica**, per raggruppare geni o campioni biologici con profili simili;
- **Riconoscimento di pattern** e analisi esplorativa dei dati, per individuare strutture nascoste nei dataset.

Il clustering è spesso utilizzato come strumento di **analisi esplorativa**, utile per comprendere la struttura interna dei dati prima di applicare modelli supervisionati.
### Nell’ambito dell’apprendimento Automatico Quali Sono Le Principali Cause Di Overfitting? #Ricapitato_1_volta
L’**overfitting** si verifica quando un modello apprende in modo eccessivamente accurato i dati di training, includendo anche il **rumore**, e perde quindi capacità di **generalizzazione** su dati non visti.
Le principali cause di overfitting sono:
- **Modello troppo complesso** rispetto alla quantità di dati disponibili (elevato numero di parametri);
- **Numero insufficiente di pattern nel training set**, che non rappresenta adeguatamente il problema;
- **Eccessiva adattabilità del modello**, che porta a memorizzare i dati invece di apprendere la relazione sottostante;
- **Assenza o insufficiente regolarizzazione**, che non penalizza modelli troppo complessi.

In queste condizioni il modello ottiene buone prestazioni sul training set ma scarse prestazioni sul validation o test set.
### Nel Caso Di Pattern Non-linearmente Separabili, Nella Formulazione Di SVM Lineare come Si Approccia Il Problema? #Ricapitato_1_volta
Nel caso in cui i pattern **non siano linearmente separabili**, nella formulazione di **SVM lineare** si introduce il concetto di **soft margin**.
In particolare:
- si ammette che alcuni pattern possano violare il margine o essere classificati erroneamente;
- vengono introdotte delle **variabili di slack** che misurano il grado di violazione dei vincoli;
- viene aggiunto un parametro di **regolarizzazione** che bilancia la massimizzazione del margine e la penalizzazione degli errori di classificazione.

Questo approccio permette di ottenere una soluzione anche in presenza di dati non perfettamente separabili, mantenendo una buona capacità di generalizzazione.
### Cosa Si Intende per Multi-classificatore? Quando Un Multi-classificatore È Efficace?
Un **multi-classificatore** è un sistema di classificazione che combina le decisioni di **più classificatori** (detti classificatori base o deboli) per ottenere una decisione finale più affidabile rispetto a quella di un singolo modello.
L’idea di base è che classificatori diversi possano commettere errori diversi; combinando le loro decisioni è possibile **ridurre l’errore complessivo** e migliorare la robustezza del sistema.
Un multi-classificatore è efficace quando:
- i classificatori base sono **sufficientemente accurati**, anche se non perfetti;
- i classificatori commettono **errori non fortemente correlati** tra loro;
- la regola di combinazione (ad esempio voto di maggioranza o combinazione pesata) è adeguata al problema.

In queste condizioni, il multi-classificatore riesce a ottenere prestazioni migliori rispetto ai singoli classificatori che lo compongono.
### Fare Esempi Pratici Di Ragionamento Induttivo E Deduttivo. #Ricapitato_1_volta
Il **ragionamento induttivo** consiste nel ricavare **regole generali** o modelli a partire da **osservazioni particolari**.  
È il principio alla base del **Machine Learning**, in cui un modello apprende dai dati esempi.
Alcuni esempi pratici possono essere:
- osservando molti esempi di email etichettate come *spam* o *non spam*, un algoritmo apprende una regola generale per classificare nuove email;
- analizzando dati storici sul prezzo delle case (superficie, posizione, numero di stanze), un modello di regressione apprende una funzione per stimare il prezzo di nuove abitazioni;
- osservando esempi di immagini etichettate, una rete neurale apprende a riconoscere oggetti.

Il **ragionamento deduttivo** parte invece da **regole generali note** e le applica a casi specifici per trarre conclusioni.
Esempi pratici:
- dato un insieme di regole logiche, un sistema esperto deduce se un paziente è malato sulla base dei sintomi osservati;
- conoscendo una legge matematica o fisica, si deduce il risultato di un esperimento;
- in un sistema basato su regole *if–then*, si applicano le regole per ottenere una decisione.

In questo caso, la conoscenza è **esplicitamente codificata** e il sistema si limita ad applicarla.
### Nella Regressione Lineare (sia Rispetto Ai Parametri Sia Rispetto Alla Variabile indipendente) I Dati Con Cosa Sono Approssimati Nel Caso 2D E 3D? #Ricapitato_1_volta
Nella **regressione lineare**, i dati vengono approssimati tramite **modelli lineari**, la cui forma dipende dalla dimensionalità dello spazio dei dati.

- **Caso 2D** (una variabile indipendente):
  - i dati sono approssimati da una **retta**;
  - il modello ha la forma:    $$
    y = w_0 + w_1 x
    $$
- **Caso 3D** (due variabili indipendenti):
  - i dati sono approssimati da un **piano**;
  - il modello ha la forma:$$
    y = w_0 + w_1 x_1 + w_2 x_2$$
In generale, all’aumentare della dimensionalità, la regressione lineare approssima i dati con un **iperpiano** nello spazio delle feature.
### Quali Sono Le Più Note Tecniche Di Riduzione Di Dimensionalità? Quali I Loro Tipici Utilizzi? #Ricapitato_1_volta
Le tecniche di **riduzione di dimensionalità** hanno l’obiettivo di rappresentare i dati in uno spazio di dimensione inferiore preservando l’informazione rilevante.
Le più note sono:
- **PCA (Principal Component Analysis)**  
  - tecnica non supervisionata;
  - utilizzata per:
    - compressione dei dati;
    - riduzione del rumore;
    - visualizzazione dei dati in 2D o 3D;
    - pre-processing per altri algoritmi di ML.
- **LDA (Linear Discriminant Analysis)**  
  - tecnica supervisionata;
  - utilizzata per:
    - migliorare la separabilità tra classi;
    - riduzione di dimensionalità a fini di classificazione.

Queste tecniche sono spesso impiegate per contrastare la **curse of dimensionality** e semplificare l’addestramento dei modelli.
### Nell’ambito Di Classificazione Con SVM Cosa Si Intende per Pattern Linearmente Separabili E Non Linearmente Separabili? Fare Esempio Grafico Dei due Casi. #Ricapitato_1_volta
Nel contesto delle **Support Vector Machine (SVM)**:
- **Pattern linearmente separabili**  
  Sono pattern per i quali esiste almeno un **iperpiano** che separa perfettamente le classi senza errori.
![[Pasted image 20251229182011.png]]
- **Pattern non linearmente separabili**  
  Sono pattern per i quali **non esiste** una retta (o iperpiano) che separi perfettamente le classi.
![[Pasted image 20251229182030.png]]
In questi casi, le SVM affrontano il problema introducendo il **soft margin** o utilizzando il **kernel trick** per ottenere una separazione nello spazio delle feature trasformato.
### Cosa Si Intende per Convergenza Di Un Algoritmo Di Apprendimento Iterativo? Accuratezza E Loss come Si Comportano Durante Le Iterazioni in Caso Di Convergenza. Disegnare Un Semplice Grafico
Per **convergenza** di un algoritmo di apprendimento iterativo si intende la condizione in cui, al procedere delle iterazioni di addestramento, i **parametri del modello** (pesi) e il valore della **funzione obiettivo (loss)** smettono di variare in modo significativo.
In altre parole, l’algoritmo ha raggiunto una soluzione stabile (tipicamente un minimo locale o globale della funzione di errore) e ulteriori iterazioni **non portano miglioramenti rilevanti**.
La loss e l'accuratezza hanno il seguente comportamento durante la convergenza:
- la **loss**:
  - diminuisce progressivamente;
  - tende a stabilizzarsi attorno a un valore minimo;
- l’**accuratezza**:
  - aumenta con le iterazioni;
  - tende a stabilizzarsi su un valore massimo.

Quando loss e accuratezza diventano quasi costanti, l’algoritmo può essere considerato convergente.
![[Pasted image 20251229182235.png]]
### Nell’ambito Dei Multi-classificatori Quali Sono Le Più Comuni Tecniche Di Fusione a Livello Di Decisione E Di Confidenza? #Ricapitato_1_volta
Nei **multi-classificatori**, la fusione delle informazioni può avvenire a **livello di decisione** oppure a **livello di confidenza**, a seconda del tipo di output prodotto dai classificatori base.
#### Fusione a Livello Di Decisione
In questo caso ciascun classificatore fornisce una **decisione discreta** (classe assegnata) e la combinazione avviene direttamente sulle etichette.
Le tecniche più comuni sono:
- **Voto di maggioranza**: la classe finale è quella più frequentemente predetta dai classificatori;
- **Voto pesato**: a ciascun classificatore viene assegnato un peso proporzionale alla sua affidabilità, e la decisione finale tiene conto di tali pesi.
Queste tecniche sono semplici e non richiedono informazioni aggiuntive oltre alla classe predetta.
#### Fusione a Livello Di Confidenza
In questo caso ciascun classificatore fornisce, oltre alla decisione, un **valore di confidenza** (ad esempio una probabilità o uno score).
Le tecniche più comuni sono:
- **Media delle confidenze**;
- **Somma delle confidenze**;
- **Massimo delle confidenze**.

La classe finale è quella che massimizza la confidenza combinata.  
Questo approccio è generalmente più informativo rispetto alla fusione a livello di decisione, poiché sfrutta anche il grado di certezza dei singoli classificatori.
### Nell’ambito Di CNN, Che Cosa Si Intende Con Transfer Learning? Quali Sono Le Tecniche Di Transfer Learning Utilizzabili? #Ricapitato_1_volta
Nel contesto delle **Convolutional Neural Networks (CNN)**, il **transfer learning** consiste nel riutilizzare una rete neurale già addestrata su un grande dataset per risolvere un **nuovo problema**, generalmente con una quantità limitata di dati.
L’idea di base è che i primi strati della rete apprendono **feature generiche**, riutilizzabili anche in domini differenti.
Le principali tecniche di transfer learning nelle CNN sono:
- **Feature extraction**  
  La rete pre-addestrata viene utilizzata come **estrattore di feature**:  
  - i pesi dei layer convoluzionali vengono mantenuti fissi;
  - solo il classificatore finale viene addestrato sul nuovo dataset.
- **Fine-tuning**  
  Oltre al classificatore finale, vengono riaddestrati anche alcuni **strati interni** della rete:
  - tipicamente gli strati più profondi;
  - consente un migliore adattamento al nuovo task.
### Come Può Essere Scelto Nella Pratica Il Numero Di Cluster in Un Algoritmo Di Clustering come K-means? #Ricapitato_1_volta
Nella pratica, il numero di cluster $K$ nell’algoritmo **K-means** non è noto a priori e viene scelto tramite criteri empirici.
Le strategie più comuni sono:
- **Analisi della funzione obiettivo**: si osserva l’andamento della somma delle distanze intra-cluster al variare di $K$ e si sceglie un valore oltre il quale il miglioramento diventa marginale;
- **Metodo del gomito (elbow method)**: si individua il punto in cui la riduzione dell’errore rallenta significativamente;
- **Conoscenza del dominio applicativo**: informazioni a priori sul problema possono suggerire un numero plausibile di cluster.

In generale, la scelta di $K$ rappresenta un compromesso tra accuratezza della rappresentazione e semplicità del modello.
### Cosa Si Intende per Funzione Obiettivo E Loss Function? #Ricapitato_1_volta
La **funzione obiettivo** è la funzione matematica che un algoritmo di apprendimento cerca di **ottimizzare** (minimizzare o massimizzare) durante il training. Essa formalizza ciò che si desidera ottenere dal modello.
La **loss function** è una funzione che misura l’**errore** commesso dal modello su un singolo pattern o su un insieme di pattern, confrontando l’output predetto con quello desiderato.
In molti casi, la funzione obiettivo è definita come la **somma o la media delle loss function** sui dati di training.
### Cosa Si Intende per Risoluzione Dei Problemi Con Approccio “forza bruta”. Si Tratta Di Intelligenza Artificiale?
L’approccio **a forza bruta** consiste nel risolvere un problema esplorando **tutte le possibili soluzioni**, selezionando quella che soddisfa i vincoli o ottimizza un certo criterio.
Questo approccio:
- non utilizza modelli, apprendimento o rappresentazioni della conoscenza;
- è spesso computazionalmente inefficiente per problemi complessi.

In generale, la forza bruta **non è considerata intelligenza artificiale**, poiché manca di capacità di apprendimento, adattamento o generalizzazione.  
Tuttavia, può essere utilizzata come metodo di riferimento o come parte di sistemi più complessi.
### Qual È la Differenza Sostanziale dell’approccio “On-line” Rispetto a “SGD Con mini-batch“ per Il Training Di Reti Neurali? #Ricapitato_1_volta
La differenza principale riguarda la **quantità di dati utilizzata per ogni aggiornamento dei pesi**.
- **Approccio On-line**:
  - i pesi vengono aggiornati **dopo ogni singolo pattern**;
  - l’aggiornamento è molto frequente e rumoroso;
  - adatto a contesti con flussi di dati continui.
- **SGD con mini-batch**:
  - i pesi vengono aggiornati dopo aver elaborato un **piccolo sottoinsieme di pattern** (mini-batch);
  - rappresenta un compromesso tra stabilità e velocità;
  - è l’approccio più utilizzato nella pratica per l’addestramento delle reti neurali.

In sintesi, l’approccio on-line usa batch di dimensione 1, mentre il mini-batch usa batch di dimensione maggiore, ottenendo aggiornamenti più stabili.
Per l’addestramento di una rete neurale che cosa si intende con vettore di output desiderato? Come può essere
definito? Come si può calcolare l’errore da retro-propagare a partire dal vettore desiderato e dal valore calcolato
dalla rete per un pattern? Oltre alla spiegazione riportare un esempio### La Posizione E Forma dell’ellissoide Di Una Distribuzione Multinormale come È Influenzata Da 𝜇 E Ʃ?
Il **vettore di media μ** determina la **posizione** dell’ellissoide:
  - μ rappresenta il **centro** della distribuzione;
  - traslando μ, l’intero ellissoide si sposta nello spazio.
La **matrice di covarianza Σ** determina la **forma, dimensione e orientamento** dell’ellissoide:
  - gli **autovalori** di Σ controllano l’estensione dell’ellissoide lungo ciascuna direzione;
  - gli **autovettori** di Σ determinano l’orientamento dell’ellissoide;
  - covarianze nulle producono ellissoidi allineati agli assi, covarianze non nulle producono ellissoidi inclinati.
### Nell’ambito Dei Multi-classificatori come Si Può Ottenere Indipendenza Tra I Singoli Classificatori Utilizzati?
Nei **multi-classificatori**, l’efficacia dipende dalla **diversità** (o bassa correlazione degli errori) tra i classificatori base.
L’indipendenza può essere ottenuta tramite:
- **uso di diversi sottoinsiemi di dati** di training (es. campionamento bootstrap);
- **uso di diversi sottoinsiemi di feature**;
- **uso di modelli o parametri differenti** per i classificatori base;
- **inizializzazioni diverse** dei modelli.

Queste strategie portano i classificatori a commettere errori diversi, migliorando le prestazioni della combinazione.
### Nell’ambito Delle Reti Neurali, Quali Sono Le Principali Differenze Di CNN Rispetto a MLP?
Le **Convolutional Neural Networks (CNN)** si differenziano dalle **Multi-Layer Perceptron (MLP)** principalmente per la struttura delle connessioni e il modo in cui trattano i dati.
Le principali differenze sono:
1. **Connessioni locali**:
  - nelle CNN ogni neurone è connesso solo a una regione locale dell’input;
  - nelle MLP le connessioni sono completamente dense.
2. **Condivisione dei pesi**:
  - le CNN utilizzano gli stessi filtri su diverse regioni dell’input;
  - le MLP hanno pesi distinti per ogni connessione.
3. **Riduzione del numero di parametri**:
  - le CNN hanno molti meno parametri rispetto alle MLP;
4. **Invarianza a traslazioni**:
  - le CNN sono più robuste a traslazioni locali dell’input.

Per questi motivi, le CNN sono particolarmente adatte a dati con **struttura spaziale**, come le immagini.
### In Classificazione Cosa Si Intende per Superficie Decisionale O Di Separazione? Riportare Anche Un Esempio Grafico. #Ricapitato_1_volta
In un problema di **classificazione**, la **superficie decisionale** (o superficie di separazione) è l’insieme dei punti dello spazio delle feature per i quali il classificatore è **indifferente tra due o più classi**.  
Essa divide lo spazio delle feature in **regioni di decisione**, ciascuna associata a una classe.
- In **2D** la superficie decisionale è una **retta**;
- In **3D** è un **piano**;
- In dimensioni superiori è un **iperpiano** (o, in generale, una superficie non lineare).
![undefined](https://upload.wikimedia.org/wikipedia/commons/9/97/Linear_Decision_Boundary.png)
### Qual È l’idea Di Base dell’algoritmo Backpropagation per l’addestramento Di Reti Neurali?
L’algoritmo di **backpropagation** è una procedura iterativa utilizzata per addestrare le **reti neurali** tramite **discesa del gradiente**.
L’idea di base è:
- calcolare l’errore tra l’output prodotto dalla rete e l’output desiderato;
- propagare tale errore **all’indietro**, dallo strato di output verso gli strati interni;
- aggiornare i pesi della rete in modo proporzionale al **gradiente della funzione di errore** rispetto ai pesi.

In questo modo, a ogni iterazione, i pesi vengono modificati per **ridurre la loss**, portando progressivamente il modello verso una soluzione ottimale.
### Quali Sono I Parametri Di Una Distribuzione Multinormale?
Una **distribuzione multinormale** è completamente definita da due parametri:
- il **vettore di media** $\mu$:
  - determina la posizione (centro) della distribuzione;
- la **matrice di covarianza** $\Sigma$:
  - descrive la dispersione dei dati;
  - determina forma, dimensione e orientamento dell’ellissoide associato alla distribuzione.

Questi due parametri sono sufficienti a descrivere completamente la distribuzione di probabilità.
### Quali Sono Le Limitazioni Di Q Learning per Risolvere Problemi Complessi? Le Tecniche Di Deep Learning Possono Essere Di Aiuto in Questo Caso? Come?
Il **Q-learning** classico presenta importanti limitazioni quando applicato a problemi complessi:
- richiede una **tabella Q** che cresce rapidamente con il numero di stati e azioni;
- diventa impraticabile in spazi di stato **grandi o continui**;
- soffre fortemente della **curse of dimensionality**;
- la memorizzazione e l’aggiornamento della Q-table risultano computazionalmente costosi.

Le **tecniche di Deep Learning** possono essere di aiuto sostituendo la Q-table con una **rete neurale profonda** che approssima la funzione $Q(s,a)$.  
In questo modo:
- non è più necessario memorizzare esplicitamente tutti gli stati;
- la rete generalizza tra stati simili;
- è possibile affrontare problemi con spazi di stato complessi.

Questo approccio prende il nome di **Deep Q-Learning**.
### Nell’ambito Dei Multi-classificatori Che Cosa È E come Funziona Il Borda Count?
Il **Borda count** è una tecnica di **fusione a livello di decisione** utilizzata nei multi-classificatori quando ciascun classificatore produce una **classifica delle classi**.
Il funzionamento è il seguente:
- ogni classificatore assegna un **ranking** alle classi;
- a ciascuna posizione nel ranking viene associato un **punteggio**;
- i punteggi assegnati dalle diverse classifiche vengono **sommati** per ogni classe;Nell’ambito delle reti neurali che cosa si intende per problema del vanishing gradient? Come può essere
risolto?
- la classe con il punteggio totale più alto viene scelta come decisione finale.

Il Borda count sfrutta quindi l’informazione contenuta nell’ordinamento delle classi, non solo nella classe vincente. [[# Tabella Borda Count Di Un Multiclassificatore]] 
### Come Opera Un Livello Di Convoluzione Di Una CNN?
Un **livello di convoluzione** di una **CNN** applica un insieme di **filtri (kernel)** locali al volume di input.
In particolare:
- ogni filtro scorre sull’input effettuando un’operazione di **convoluzione**;
- i pesi del filtro sono **condivisi** su tutte le posizioni;
- ogni filtro produce una **feature map**;
- il numero di feature map in uscita è pari al numero di filtri.

Questo meccanismo consente di:
- estrarre **feature locali**;
- ridurre il numero di parametri;
- mantenere l’informazione spaziale dell’input.
### La Densità Locale Di Pattern Con Quali Metodi (parametrici E non-parametrici) Può Essere Stimata? Fare Un Esempio
La **densità locale di pattern** può essere stimata tramite:
#### Metodi Parametrici
Assumono una forma funzionale nota della distribuzione.
- Esempio: **distribuzione gaussiana (multinormale)**, caratterizzata da media $\mu$ e covarianza $\Sigma$.
#### Metodi Non-parametrici
Non assumono una forma prefissata della distribuzione.
- Esempio: **stima di densità di Parzen**, in cui la densità viene stimata sommando contributi locali dei pattern tramite una finestra o kernel.

Questi metodi sono utilizzati, ad esempio, nel clustering basato su **modelli probabilistici**.
### Come Si Misurano Le Prestazioni Di Un Classificatore?
Le prestazioni di un **classificatore** vengono misurate confrontando le **etichette predette** con le **etichette reali** sui dati di test o di validazione.
Gli strumenti principali sono:
- **Matrice di confusione**, che riassume:
  - veri positivi,
  - veri negativi,
  - falsi positivi,
  - falsi negativi.

A partire dalla matrice di confusione si definiscono indicatori di prestazione, tra cui:
- **accuratezza**, che misura la frazione di pattern correttamente classificati;
- **tasso di errore**, complementare all’accuratezza.

Queste misure permettono di valutare la **capacità di generalizzazione** del classificatore.
### Dal Punto Di Vista Pratico nell’approccio Di Parzen Che Differenza c’è Se Si Usa Una Funzione Finestra Ipercubo Piuttosto Che Multinormale?
Nell’approccio di **stima di densità di Parzen**, la differenza tra le due finestre riguarda il modo in cui i pattern contribuiscono alla densità locale.
- **Finestra ipercubo**:
  - assegna un contributo **costante** ai pattern che cadono all’interno della finestra;
  - i pattern fuori dalla finestra non contribuiscono;
  - è computazionalmente semplice ma produce stime **meno regolari**.
- **Finestra multinormale (gaussiana)**:
  - assegna un contributo **decrescente con la distanza** dal punto considerato;
  - tutti i pattern contribuiscono, anche se con peso diverso;
  - produce stime di densità **più lisce e regolari**.

Dal punto di vista pratico, la finestra multinormale fornisce una stima più stabile e realistica, a costo di un maggiore carico computazionale.
### Quanti Sono I Parametri Indipendenti Di Una Distribuzione Multinormale Nel Caso 3-dimensionale? Motivare la Risposta
Una **distribuzione multinormale** è definita da:
- un **vettore di media** $\mu$;
- una **matrice di covarianza** $\Sigma$.

Nel caso **3-dimensionale**:
- il vettore di media $\mu$ ha **3 parametri**;
- la matrice di covarianza $\Sigma$ è una matrice $3 \times 3$ simmetrica:
  - contiene 3 varianze sulla diagonale;
  - contiene 3 covarianze indipendenti fuori diagonale.

Il numero totale di parametri indipendenti è quindi:
$$
3 \;(\mu) + 6 \;(\Sigma) = 9
$$
La simmetria della matrice di covarianza riduce il numero di parametri indipendenti rispetto ai 9 elementi totali della matrice.
### Quando Una Rete Neurale Si Definisce Deep (profonda)?
Una **rete neurale** si definisce **deep (profonda)** quando è composta da **più di uno strato nascosto** tra lo strato di input e lo strato di output.  
La presenza di **più livelli di neuroni** consente alla rete di apprendere **rappresentazioni gerarchiche** dei dati:  
- gli strati più vicini all’input estraggono feature più semplici;
- gli strati più profondi estraggono feature via via più astratte.

Questa profondità distingue il **Deep Learning** dalle reti neurali tradizionali con un solo hidden layer.
### Che Cosa Denota la Matrice Ʃ Nella Definizione Della Distribuzione Multinormale?
scritto qui:
[[#Quali Sono I Parametri Di Una Distribuzione Multinormale?]]
### Nel Classificatore Di Bayes Cosa Si Intende per Densità Di Probabilità Condizionale E Probabilità a Priori
Nel **classificatore di Bayes**:
- la **densità di probabilità condizionale** $p(x \mid \omega_i)$ rappresenta la probabilità di osservare il pattern $x$ **assumendo che esso appartenga alla classe $\omega_i$**;
- la **probabilità a priori** $P(\omega_i)$ rappresenta la probabilità che un pattern appartenga alla classe $\omega_i$ **prima di osservare i dati**.

Il classificatore di Bayes combina queste quantità per stimare la probabilità a posteriori e assegnare il pattern alla classe più probabile.
### Per l’addestramento Di Una Rete Neurale Che Cosa Si Intende Con Vettore Di Output Desiderato? Come Può Essere Definito? Come Si Può Calcolare l’errore Da Retro-propagare a Partire Dal Vettore Desiderato E Dal Valore Calcolato Dalla Rete per Un Pattern? Oltre Alla Spiegazione Riportare Un Esempio
Il **vettore di output desiderato** rappresenta l’output corretto che la rete dovrebbe produrre per un determinato pattern di input durante la fase di training.
#### Definizione
- È un vettore $d$ che contiene i valori target associati al pattern;
- Nei problemi di classificazione è spesso definito tramite **codifica one-hot**.
#### Calcolo dell’errore
L’errore viene calcolato confrontando:
- il vettore di output desiderato $d$;
- il vettore di output prodotto dalla rete $y$.

Un errore tipico è dato dalla **differenza** tra output desiderato e output calcolato:
$$
e = d - y
$$
Questo errore viene poi utilizzato dalla **backpropagation** per aggiornare i pesi della rete.
#### Esempio
Problema di classificazione a **3 classi**:
- pattern appartenente alla classe 2  
- vettore desiderato:
$$
d = [0,\;1,\;0]
$$
- output della rete:
$$
y = [0.1,\;0.7,\;0.2]
$$
- errore:
$$
e = d - y = [-0.1,\;0.3,\;-0.2]
$$
Questo vettore di errore viene propagato all’indietro per correggere i pesi della rete.
### Cosa Si Intende per Approccio Parametrico E Non-parametrico nell’ambito Della Classificazione? Fare Un Esempio Di Classificatore Parametrico E Non Parametrico
Nell’ambito della **classificazione**, un approccio può essere **parametrico** o **non-parametrico** a seconda delle assunzioni fatte sul modello dei dati.
- **Approccio parametrico**  
  Assume che i dati seguano una **distribuzione di forma nota**, descritta da un numero finito di parametri.  
  Il modello viene appreso stimando tali parametri a partire dai dati.
  **Esempio**:  
  - **Classificatore di Bayes** con densità **multinormali**, descritte da vettore di media $\mu$ e matrice di covarianza $\Sigma$.
- **Approccio non-parametrico**  
  Non assume una forma funzionale prefissata per la distribuzione dei dati.  
  La complessità del modello cresce con il numero di pattern disponibili.
  **Esempio**:  
  - **Classificatore basato su Parzen**, che stima la densità tramite finestre centrate sui pattern del training set.
### Nell’ambito Delle Reti Neurali Che Cosa Si Intende per Problema Del Vanishing Gradient? Come Può Essere Risolto?
Il **problema del vanishing gradient** si verifica durante l’addestramento di **reti neurali profonde**, quando il gradiente dell’errore, propagandosi all’indietro attraverso molti strati, tende a diventare **molto piccolo**.
Di conseguenza:
- i pesi degli strati più profondi vengono aggiornati in modo trascurabile;
- l’addestramento diventa molto lento o si blocca.

Il problema può essere mitigato utilizzando:
- **funzioni di attivazione come ReLU**, che non saturano per valori positivi;
- architetture profonde progettate per facilitare la propagazione del gradiente.
### Come Può Essere Matematicamente Definita la Loss Function (su Un Singolo pattern) per l’addestramento Di Una Rete Neurale?
La **loss function** su un singolo pattern misura l’errore tra:
- il **vettore di output desiderato** $d$;
- l’**output prodotto dalla rete** $y$.

Una definizione tipica è l’**errore quadratico**:
$$
L(d, y) = \frac{1}{2} \sum_{j} (d_j - y_j)^2
$$
Questa funzione quantifica lo scostamento tra output desiderato e output calcolato ed è utilizzata dalla **backpropagation** per aggiornare i pesi della rete.
### Con Quali Tecniche Si Può Estendere SVM Da 2 a Più Classi?
Le **Support Vector Machine (SVM)** sono nate per problemi di **classificazione binaria**, ma possono essere estese al caso **multi-classe** tramite strategie di decomposizione del problema.
Le tecniche più comuni sono:
- **One-vs-All (OvA)**  
  - si addestrano $K$ classificatori binari, uno per ciascuna classe;
  - ogni classificatore separa una classe da tutte le altre;
  - la classe finale è quella associata al classificatore con output più alto.
- **One-vs-One (OvO)**  
  - si addestrano classificatori binari per ogni coppia di classi;
  - nel caso di $K$ classi si ottengono $\frac{K(K-1)}{2}$ classificatori;
  - la decisione finale è ottenuta tramite **voto di maggioranza**.

Questi approcci permettono di utilizzare SVM binarie anche in contesti multi-classe.
### Che Cosa Codifica la Funzione Q nell’ambito dell’approccio Q-learning? Quali Sono Gli Input Che Ne Determinano Il Valore?
Nell’ambito del **Q-learning**, la **funzione Q** codifica la **qualità** (o valore atteso) dell’esecuzione di una certa azione in uno stato.
Formalmente, la funzione:
$$
Q(s,a)
$$
rappresenta la **ricompensa cumulativa attesa** che un agente può ottenere:
- partendo dallo **stato** $s$,
- eseguendo l’**azione** $a$,
- e seguendo successivamente una politica ottimale.

Gli **input** che determinano il valore della funzione Q sono quindi:
- lo **stato** dell’ambiente $s$;
- l’**azione** $a$ eseguita dall’agente.

La funzione Q guida la scelta dell’azione che massimizza la ricompensa nel processo di apprendimento per rinforzo.
---
# Esercizi (si Ripetono Svariate Volte, Sono Bene O Male Sempre questi)
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
## Majority Vote Rule Di Una Multiclassificatore #Ricapitato_1_volta
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/3.png]]
### Svolgimento
Qui banalmente devi scegliere la classe che viene prodotta di più dai singoli classificatori per ogni riga, il numero scritto in grassetto è quello che dovresti scrivere all'esame.
## Calcolo Del Numero Di Addizioni E Moltiplicazioni in Una MLP #Ricapitato_1_volta_senza_bias
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/4.png]]
### Svolgimento
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/5.png]]
## Calcolo Del Vettore Medio E Della Matrica Di Covarianza #Ricapitato_1_volta
backpropaga
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/6.png]]
### Svolgimento
$n$ => numero dei pattern forniti dall'esercizio
$\mu$ => vettore media dei pattern forniti, per questo esercizio in particolare bisogna fare la media del primo elemento dei singoli pattern e del secondo elemento:
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/7.png]]
per quanto riguarda la matrice basta applicare la formula, è lunga ma si fa, ricordati che la dimensione di $\sum{}{}$ è la dimensione del singolo pattern per la dimensione di $\mu$ perchè alla fine della fiera è una moltiplicazione tra matrici.
## Prima Iterazione Dell'algoritmo K-means per I Seguenti Pattern #Ricapitato_1_volta
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
## Tabella Multiclassificatore Con Somma, Prodotto, Massimo E Minimo #Ricapitato_1_volta
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/10.png]]
backpropaga### Svolgimento
Questo è abbastanza semplice, basta prendere i dati dei singoli classificatore e applicare le singole strategie per riempire la tabella e poi prendi il massimo per determinare l'out delle singole strategie.
Le cifre in grassetto sono da calcolare per questo esercizio specifico:
![[es10.png]]
## Calcolo Del Numero Di Connessioni E Dei Pesi Di Un Livello Di Una CNN #Ricapitato_1_volta_con_variante_del_bias
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/11.png]]
Ogni neurone del livello di output (96 × 55 × 55) è connesso con tanti neuroni del livello di input pari alla dimensione del filtro (3 × 11 × 11). Pertanto il numero totale di connessioni è (96 × 55 × 55) ∙ (3 × 11 × 11) = 105 415 200. Il numero totale di pesi, invece, risulta molto più piccolo giacché in una CNN i pesi di ciascun filtro sono condivisi da tutti i neuroni contenuti in una stessa feature map. Visto che il numero di feature map è uguale a 96, ed il numero di input per ciascun filtro è pari a (3 × 11 × 11), il numero totale di pesi (senza considerare il bias) è (3 × 11 × 11) × 96 = 34 848.
### Variante Bias
Calcolo delle connessioni rimane uguale.
il calcolo dei pesi diventa => ((3 × 11 × 11)+1) × 96 = 34944
## Classificatore Di Bayes Multinormale, Calcolare per Il Punto X VARIANTE #Ricapitato_1_volta
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
## Capire la Classe Predetta Da K-NN Dato Un Grafo E Dei Valori Di K #Ricapitato_1_volta
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/19.png]]
### Svolgimento
![[es19.png]]
## Formulare Il Problema Di Multiple Linear Regressor Definendo X Ed Y
![[es20.png]]
### Svolgimento
Come spiegato anche nella domanda di teoria, la pratica si fa nell'esatto modo:
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/20.png]]
## PCA E LDA
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/21.png]]
### Svolgimento
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/22.png]]
## Calcolo Delle Dimensioni Delle Feature Map Prodotte Da Una CNN
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/23.png]]
### Svolgimento
![[es23.png]]
## Numero Di _run_ E Numero Di Pattern Di Training E Validation Di K-fold Cross Validation
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/24.png]]
### Svolgimento
![[es24.png]]Cosa si intende per K-fold cross-validation? Quali sono i vantaggi rispetto a un semplice split a due dei
dati di training?
## Numero Di Neuroni E Pesi Addestrabili in Una Rete Ricorrente Nella Sua Versione Unfolded #Ricapitato_1_volta
![[Primo Semestre Major/Machine Learning/imgs/Esercizi/25.png]]
### Svolgimento
![[es25.png]]
## Calcolo Del Volume Di Output Di Una CNN Data Una Immagine #Ricapitato_1_volta
![[Pasted image 20251229005205.png]]
### Svolgimento
![[Pasted image 20251229005233.png]]
## Crazy Exercise, Chiede Tipo Tutto Porco #Ricapitato_1_volta
![[Pasted image 20251229005703.png]]
### Svolgimento
![[Pasted image 20251229005720.png]]
## Calcolo Del Numero Di Volte in Cui SGD Vede Un Pattern Ed Il Numero Di Volte in Cui Aggiorna Un Peso #Ricapitato_1_volta
![[Pasted image 20251229010156.png]]
### Svolgimento
![[Pasted image 20251229010211.png]]
## Determinare Il MAE Sul Test Set
![[Pasted image 20251229010304.png]]
### Svolgimento
![[Pasted image 20251229010325.png]]
## Confusion Matrix E Accuracy Di Un Modello
![[Pasted image 20251229010629.png]]
### Svolgimento
![[Pasted image 20251229010639.png]]
## Numero Complessivo Di Addestramenti Da Effettuare Di Una Grid search Combinata a K-fold Cross-validation #Ricapitato_1_volta
![[Pasted image 20251230183010.png]]
### Svolgimento
![[Pasted image 20251230183025.png]]