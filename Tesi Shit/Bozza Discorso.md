### Prima Slide - Titolo 
Buongiorno a tutti, sono Fabio Fattori e oggi vi presento il mio lavoro di tesi: 'AmbrogioAI – un classificatore automatico di outfit'.
### Seconda Slide - cambio da prima a seconda mentre dico la frase sopra
Questo progetto nasce dall’idea di unire due mondi che sembrano lontani: la computer vision, che permette alle macchine di ‘vedere’ e interpretare immagini, e la moda, che esprime la personalità e l’identità di chi la indossa. L'obiettivo è proprio quello di applicare tecniche visive automatiche per leggere e classificare ciò che, fino a poco tempo fa, era considerato troppo soggettivo: lo stile.
### Terza Slide - cambio appena finisco la frase
Il tema non è nuovo: diversi studi hanno esplorato il rapporto tra moda e intelligenza artificiale. Ad esempio, Fashion++, sviluppato da Meta, cerca di migliorare un outfit suggerendo piccole modifiche, come l’aggiunta di un accessorio.
Altre soluzioni si concentrano sul commercio: l’Item Retrieval, per esempio, consente di identificare capi presenti in un’immagine e suggerirne di simili acquistabili online. Questi sistemi si basano su tecniche come il fashion parsing, che segmenta visivamente l’outfit per riconoscere e classificare i singoli indumenti.
### Quarta Slide - cambio appena finisco la frase
Il progetto che vi presento oggi parte da una domanda semplice ma ambiziosa: è possibile classificare lo stile di un outfit?
Cioè: possiamo dire a un utente se ciò che indossa è elegante, sportivo o casual, e quindi se è adatto a un certo contesto — che sia una serata di gala, un’uscita con amici, o una partita di calcetto?
E soprattutto: si può realizzare un sistema che lo faccia in modo automatico e accessibile all’utente finale?
### Quinta Slide - cambio appena finisco la frase
Per risolvere tale problema è necessario realizzare una architettura appropriata, a livello di costo computazionale è attualmente impensabile rilasciare l'AI nel dispositivo consegnato all'utente, quindi sarà necessario realizzare un server che rende disponibili delle API che consentano ad un client l'interazioni con il modello.
Quello che possiamo vedere sulla sinistra è il workflow delle chiamate Api dal dispositivo in loco, in questo caso un Raspberry Pi 4 con una telecamera, fino al mio computer fisso di casa il quale, all'avvio del server, apre un tunnel bidirezionale verso cloudflare permettendo al Front di accedere alle Api.
### Sesta Slide
Avendo chiara in mente l'architettura, possiamo passare alla formazione del dataset con cui allenare l'AI.
Per prima bisogna identificare cosa vuol dire per la moda i termini casual, elegante e sportivo:
Per Casual si intende un abbigliamento da tutti i giorni, in realtà è un termine molto ambio che dentro di se contiene diverse sottocategorie come lo streetweare, quindi polo, jeans, magliette e felpe compongono un abbigliamento di questa categoria.
Il fashion identifica come elegante una persona non in base all'abbigliamento ma al suo portamento ed espressioni, quindi usando il buon senso possiamo definire come elegante una persona vestita con camicia, cravatta, un completo e simili; mentre per quanto riguarda lo sportivo si fa riferimento ad abiti tecnici e traspiranti ideati per fare sport, come shorts, scarpe da ginnastica, scarpini, magliette a maniche corte ecc.

Per la sua formazione ho provato diverse tecniche, per prima cosa ho raccolto a mano 