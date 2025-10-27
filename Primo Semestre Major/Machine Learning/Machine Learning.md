# Machine Learning
## 17/09/2025 - Primo Pdf Fino a Pag 19
Machine Learning => ragionamento di tipo induttivo dato che parte da degli esempi (dati) per portare un risultato
### Ragionamenti
- Deduttivo: 
	In questo ragionamento la verità delle premesse (caso generico) garantisce la verità della conclusione (caso particolare).
	Questo tipo di ragionamento è il fondamento della gran parte delle dimostrazioni e teoremi della matematica.
- Induttivo:
	Ragionamento per "analogia", ovvero trarre conclusioni su qualcosa in base alle sue somiglianze con qualcos'altro.
	Questo ragionamento permette agli umani di essere creativi, usare metafore e astrarre i concetti.
	Esempi nell'AI => Prompt to Image, comporre musica ecc.
- Abduttivo:
	Ragionamento probabilistico, come gli altri, ma che ha di diverso che invece di generalizzare ci si muove in maniera laterale ipotizzando quindi che un'implicazione valga anche al contrario:
	![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/2.jpeg]]
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/3.jpeg]]
### AI E Machine Learning
Termini ombrello che ricoprono diverse discipline:
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/1.jpeg]]
### Machine Learning
Un modello di Machine Learning (apprendimento automatico) durante la fase di training apprende a partire da esempi. Successivamente è in grado di generalizzare e gestire nuovi dati nello stesso dominio applicativo.![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/4.jpeg]]
### AI E Brute Force
- Brute force (ricerca esaustiva): in alcuni domini applicativi un calcolatore può andare a calcolare e valutare tutte le possibili soluzioni.
  Nella maggior parte dei casi però non sono gestibili a livello computazionale.
Talvolta si utilizza il termine **Weak AI** per descrivere sistemi capaci di risolvere problemi complessi senza però capacità di ragionamento e comprensione.
### Benchmarks Prestazioni LLM
BIG-bench (Beyond the Imitation Game) è un benchmark recente introdotto da ricercatori di 132 istituzioni internazionali per misurare le prestazioni di LLM.
Include più di 200 task che gli umani non hanno problemi a risolvere ma dove l’AI non raggiunge (ancora) prestazioni comparabili.

----
## 10/10/2025 - Recupero Fino a Pagina 27
### Stagioni AI
- 1940 - 1974  Nascita e Anni D'oro
	- primi calcolatori elettronici
	- teoria della computazione di Turing e Test di Turing
	- Teoria dell'informazione di Shannon
	- Neuroni artificali
	- Nascita ufficiale e conio del nome Intelligenza Artificiale
	- Primi risultati nell'ambito del symbolic reasoning, del problem solving e del natual language processing 
- 1974 - 1980 Primo Inverno
	La scarsa capacità computazionale, esplosione combinatoria ,non trattabilità e piccoli dataset hanno portato a risultati non all'altezza delle aspettative e di conseguenza ad una drastica riduzione dei fondi.
- 1980 - 1987 Nuova Primavera
	- Nascita dei sistemi esperti: conoscenza + regole logiche.
	- Nuova linfa alle reti neurali dall’algoritmo Backpropagation .
	- Finanziamento governo Giapponese per la Quinta Generazione di Calcolatori: i calcolatori «intelligenti».
- 1987 - 1993 Secondo Inverno 
	- Flop «Quinta generazione». Nuovo stop finanziamenti.
	- Hardware specializzato non più competitivo con PC, calo business.
	- Risultati concreti dei sistemi esperti solo in campi specifici.
	- Reti neurali non scalano a problemi complessi.
- 1993 - 2011 Tempi Moderni
	- Hardware sempre più potente.
	- Bayesian Networks, Intelligent Agents.
	- Classificatori robusti (SVM), Multi-classificatori (Random Forest, Adaboost)
	- Hidden Markov Models (HMM).
	- Maturità tecniche di feature extraction (hand-crafted) in diversi domini, (es. SIFT, Dictionaries & Bag of Words).
	- Deep Blue, Watson, Darpa Grand Challenge (guida automatica). 
	- Successi in numerose discipline: visione, sistemi biometrici, riconoscimento del parlato, robotica, guida automatica, diagnosi mediche, data mining, motori di ricerca, videogames.
---
### PDF Da Recuperare
Fino ad approccio parametrici (fine):
- 1_ML
- 2_ML
- 3_ML fino a pagina 20 - sembra aver skippato roba, o comunque aver sorvolato cose
--- 
#### Approcci Non Parametrici E Stima Della Densità
- Curse of Dimensionality 
##### Stima Della Densità
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/5.png]]
Da ricordare l'ultima formula.
Si vuole ”migliorare" (rendere più pulita la funzione) quindi:
###### Parzen Window
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/6.png]]
#### Classificatore Nearest Neighbor (NN)
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/7.png]]
#### k-Nearest-Neighbor (k-NN)
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/8.png]]
continua fino a pag 33.
#### NN E Prototipi Di Classi
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/9.png]]
Sta roba funziona bene o male in base ai dai che abbiamo, è una semplificazione stretta, perchè si da per scontato che i gruppi di dati siano fatti in maniera circolare, cosa che non corrisponde molto spesso alla realtà.
#### METRIC LEARNING NON SI FA
### Similarità Coseno E Distanza Coseno
Variante della distanza euclidea.
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/10.png]]
La distanza coseno non è una metrica dato che non rispetta la diseguaglianza triangolare.
# 20/10/2025 Inizio Quarto Pdf, Nello Specifico Da SVM
## Support Vector Machines (SVM)
Invece di stimare le densità di probabilità delle classi ovvero determinare le superfici decisionali tra le classi (<span style="color:rgb(255, 0, 0)">classification boundaries</span>).
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/11.png]]
## Idea Alla Base (separazione E margine)
Date due classi di pattern multidimensionali linearmente separabili, tra tutti i possibili iperpiani di separazione, SVM determina quello in grado di separare le classi con il **maggior margine possibile**.
>_Il margine_ è la distanza minima di punti delle due classi nel training set dall’ iperpiano individuato.

![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/12.png]]
La massimizzazione del margine è legata alla <span style="color:rgb(255, 0, 0)">generalizzazione</span>. Se i pattern del training set sono classificati con ampio margine si può «sperare» che anche pattern del test set vicini al confine tra le classi siano gestiti correttamente.
### SVM Lineari: Pattern Separabili
Fatto un pò alla buona la parte matematica, l'importante è capire cosa succede e bona.
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/13.png]]
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/14.png]]
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/15.png]]
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/16.png]]![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/17.png]]
### SVM Lineari: Pattern Non Separabili
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/18.png]]
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/19.png]]
## SVM Non Lineari
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/20.png]]
### SVM Non Lineari: Kernel Functions
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/21.png]]
$\sigma$ fa le veci di un regolarizzatore, permettendo delle gaussiane più piccole (come l'$h$ di Parzen).
## SVM: Estensione Multiclasse
![[Primo Semestre Major/Machine Learning/imgs/22_10_2025/22.png]]
### SVM in Pratica
_**Quando usare SVM:**_
SVM offre una buona reliability su _**dati numerici omogenei**_, ma è meno performante di modelli basati su alberi decisionali, come il RandomForest, su dati _**tabulari eterogenei**_.
_**Lineare o non?**_
- _**Il lineare**_ è la scelta preferita quando si è in uno spazio a dimensionalità molto elevata grazie al fatto che i pattern sono tipicamente molto sparsi e anche semplici iperpiani lineari riescono a separare le classi in maniera corretta.
- _**Il non lineare**_ si tende ad usare quando la dimensionalità è bassa, e la scelta preferita è SVM non lineare con kernel RBF.
- Quando la dimensione è media si provano entrambi e si prende il migliore.
### Multi-Classificatori
Approccio per il quale si usano diversi classificatori in parallelo, in cascata oppure in modo gerarchi, in maniera tale da avere una serie di decisioni dei singoli modelli, fuse poi in un'unica decisione.
Nella pratica è stato dimostrato come investire tempo nell’ottimizzazione «spinta» di un singolo classificatore è in genere meno conveniente rispetto all’affiancamento dello stesso ad altri classificatori.
#### Warning
L'affiancamento è efficace però solo quando i modelli affiancati sono indipendenti fra loro, ovvero _**non commetto gli stessi errori**_.
![[Primo Semestre Major/Machine Learning/imgs/1.png]]
> La combinazione può essere eseguti a livello di decisione o a livello di confidenza.

### Fusione a Livello Di Decisione
Ogni singolo modello restituisce in output la sua decisione, che corrisponde alla classe predetta, tutte le decisioni possono essere fra loro combinate in diversi modi:
- _**Majority vote rule**_ $\rightarrow$ Più semplice modo di combinare decisioni, perchè si raccolgono tutte le decisioni e "vince" la classe più votata.
- _**Borda Count**_ $\rightarrow$ Ogni classificatore restituisce tutte le probabilità che assegna alle classi (ranking), le quali vengono sommate a tutte le altre restituite dagli altri modelli, in maniera da ottenere una vera e propria classifica, della quale viene presa la classe con la probabilità più alta.
### One-Against-One
> L’approccio One-Against-One, consente di risolvere un problema di classificazione multi-classe, attraverso classificatori binari.

### Fusione a Livello Di Confidenza
![[Primo Semestre Major/Machine Learning/imgs/2.png]]
![[Primo Semestre Major/Machine Learning/imgs/3.png]]
![[Primo Semestre Major/Machine Learning/imgs/4.png]]
## Classificatori Basati Su Alberi Decisionali
### Random Forest
Basato sulla tecnica di Bagging, quindi viene sotto campionato il training set:
![[Primo Semestre Major/Machine Learning/imgs/5.png]]
![[Primo Semestre Major/Machine Learning/imgs/6.png]]
