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
	![[Primo Semestre Major/Machine Learning/imgs/2.jpeg]]
![[Primo Semestre Major/Machine Learning/imgs/3.jpeg]]
### AI E Machine Learning
Termini ombrello che ricoprono diverse discipline:
![[Primo Semestre Major/Machine Learning/imgs/1.jpeg]]
### Machine Learning
Un modello di Machine Learning (apprendimento automatico) durante la fase di training apprende a partire da esempi. Successivamente è in grado di generalizzare e gestire nuovi dati nello stesso dominio applicativo.![[Primo Semestre Major/Machine Learning/imgs/4.jpeg]]
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
![[Primo Semestre Major/Machine Learning/imgs/5.png]]
Da ricordare l'ultima formula.
Si vuole ”migliorare" (rendere più pulita la funzione) quindi:
###### Parzen Window
![[Primo Semestre Major/Machine Learning/imgs/6.png]]
#### Classificatore Nearest Neighbor (NN)
![[Primo Semestre Major/Machine Learning/imgs/7.png]]
#### k-Nearest-Neighbor (k-NN)
![[Primo Semestre Major/Machine Learning/imgs/8.png]]
continua fino a pag 33.
#### NN E Prototipi Di Classi
![[Primo Semestre Major/Machine Learning/imgs/9.png]]
Sta roba funziona bene o male in base ai dai che abbiamo, è una semplificazione stretta, perchè si da per scontato che i gruppi di dati siano fatti in maniera circolare, cosa che non corrisponde molto spesso alla realtà.
#### METRIC LEARNING NON SI FA
### Similarità Coseno E Distanza Coseno
Variante della distanza euclidea.
![[Primo Semestre Major/Machine Learning/imgs/10.png]]
La distanza coseno non è una metrica dato che non rispetta la diseguaglianza triangolare.
# 20/10/2025 Inizio Quarto Pdf, Nello Specifico Da SVM
## Support Vector Machines (SVM)
Invece di stimare le densità di probabilità delle classi ovvero determinare le superfici decisionali tra le classi (<span style="color:rgb(255, 0, 0)">classification boundaries</span>).
![[Primo Semestre Major/Machine Learning/imgs/11.png]]
## Idea Alla Base (separazione E margine)
Date due classi di pattern multidimensionali linearmente separabili, tra tutti i possibili iperpiani di separazione, SVM determina quello in grado di separare le classi con il **maggior margine possibile**.
>_Il margine_ è la distanza minima di punti delle due classi nel training set dall’ iperpiano individuato.

![[Primo Semestre Major/Machine Learning/imgs/12.png]]
La massimizzazione del margine è legata alla <span style="color:rgb(255, 0, 0)">generalizzazione</span>. Se i pattern del training set sono classificati con ampio margine si può «sperare» che anche pattern del test set vicini al confine tra le classi siano gestiti correttamente.
### SVM Lineari: Pattern Separabili
Fatto un pò alla buona la parte matematica, l'importante è capire cosa succede e bona.
![[Primo Semestre Major/Machine Learning/imgs/13.png]]
![[Primo Semestre Major/Machine Learning/imgs/14.png]]
![[Primo Semestre Major/Machine Learning/imgs/15.png]]
![[Primo Semestre Major/Machine Learning/imgs/16.png]]![[Primo Semestre Major/Machine Learning/imgs/17.png]]
### SVM lineari: Pattern non Separabili
![[Primo Semestre Major/Machine Learning/imgs/18.png]]
![[Primo Semestre Major/Machine Learning/imgs/19.png]]
## SVM non lineari
![[Primo Semestre Major/Machine Learning/imgs/20.png]]
