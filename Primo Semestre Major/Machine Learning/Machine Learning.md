## 17/09/2025 - primo pdf fino a pag 19
Machine Learning => ragionamento di tipo induttivo dato che parte da degli esempi (dati) per portare un risultato
#### Ragionamenti:
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
#### AI e Machine Learning
Termini ombrello che ricoprono diverse discipline:
![[Primo Semestre Major/Machine Learning/imgs/1.jpeg]]
#### Machine Learning
Un modello di Machine Learning (apprendimento automatico) durante la fase di training apprende a partire da esempi. Successivamente è in grado di generalizzare e gestire nuovi dati nello stesso dominio applicativo.![[Primo Semestre Major/Machine Learning/imgs/4.jpeg]]
#### AI e Brute force
- Brute force (ricerca esaustiva): in alcuni domini applicativi un calcolatore può andare a calcolare e valutare tutte le possibili soluzioni.
  Nella maggior parte dei casi però non sono gestibili a livello computazionale.
Talvolta si utilizza il termine **Weak AI** per descrivere sistemi capaci di risolvere problemi complessi senza però capacità di ragionamento e comprensione.
#### Benchmarks Prestazioni LLM
BIG-bench (Beyond the Imitation Game) è un benchmark recente introdotto da ricercatori di 132 istituzioni internazionali per misurare le prestazioni di LLM.
Include più di 200 task che gli umani non hanno problemi a risolvere ma dove l’AI non raggiunge (ancora) prestazioni comparabili.

----
### Stagioni AI
- 1940 - 1974  nascita e anni d'oro
	- primi calcolatori elettronici
	- teoria della computazione di Turing e Test di Turing
	- Teoria dell'informazione di Shannon
	- Neuroni artificali
	- Nascita ufficiale e conio del nome Intelligenza Artificiale
	- Primi risultati nell'ambito del symbolic reasoning, del problem solving e del natual language processing 
- 1974 - 1980 primo inverno
	La scarsa capacità computazionale, esplosione combinatoria ,non trattabilità e piccoli dataset hanno portato a risultati non all'altezza delle aspettative e di conseguenza ad una drastica riduzione dei fondi.
- 1980 - 1987 nuova primavera
	- Nascita dei sistemi esperti: conoscenza + regole logiche.
	- Nuova linfa alle reti neurali dall’algoritmo Backpropagation .
	- Finanziamento governo Giapponese per la Quinta Generazione di Calcolatori: i calcolatori «intelligenti».
- 1987 - 1993 Secondo Inverno 
	- Flop «Quinta generazione». Nuovo stop finanziamenti.
	- Hardware specializzato non più competitivo con PC, calo business.
	- Risultati concreti dei sistemi esperti solo in campi specifici.
	- Reti neurali non scalano a problemi complessi.