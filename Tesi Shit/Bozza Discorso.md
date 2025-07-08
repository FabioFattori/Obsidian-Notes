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
Per affrontare il problema, ho progettato un’architettura adatta anche a contesti con risorse limitate. L’idea è che il modello non venga eseguito sul dispositivo dell’utente, perché troppo pesante a livello computazionale, ma su un server esterno.
Il backend espone una serie di API che permettono al client di comunicare col modello. Nello schema a sinistra vedete il flusso: un Raspberry Pi con una camera scatta la foto e la invia tramite internet al mio server di casa, che apre un tunnel Cloudflare per rendere accessibili le API al frontend.
### Sesta Slide
Chiarita l’architettura, passo alla costruzione del dataset. Prima di tutto, ho dovuto stabilire cosa intendiamo per casual, elegante e sportivo.
Casual è un concetto ampio, che include abbigliamento da tutti i giorni: jeans, polo, t-shirt, felpe ... in generale tutto ciò che è informale ma curato.
Elegante, secondo il fashion, è più un atteggiamento che un look. Ma per il modello ho deciso di associare questa etichetta a completi, camicie, cravatte e abiti sobri.
Infine, sportivo include abbigliamento tecnico: maglie traspiranti, pantaloncini, scarpe da ginnastica, capi da palestra o calcio.
Per creare il dataset ho cominciato con la raccolta manuale e annotazione delle immagini, ma è un processo lentissimo: dopo 150 immagini, ho sviluppato uno script per generarle automaticamente.
Ho installato Stable Diffusion 3 Medium in locale, e in circa 20 giorni ho generato 840 immagini, rendendo il processo molto più efficiente.
Per bilanciare le differenze tra immagini reali e sintetiche (soprattutto per quanto riguarda luce, rumore, contesto), ho integrato altre immagini reali, arrivando a un totale di circa 360 reali su 1200.
### Settima - Ottava - Nona 
Di fatti ecco alcuni esempi di immagini reali paragonate a immagini sintetiche appartenenti alla stessa classe, come si può vedere la luce gioca un grande ruolo nelle immagini sintetiche paragonabile solo alle immagini reali fatte da modelli e fotografi professionisti che sono state prese da siti come Nike e Adidas.
### Decima Slide 