# Programmazione Concorrente E Distribuita
Recupera fino a pagina 44
## Critical Situations
interferenze ed errori in programmi concorrenti possono portare ad errori critici come:
- Deadlock
- Starvation
- Livelock
## Macchine Concorrenti
è una macchina che manda in esecuzione un programma concorrente, tale linguaggio implementa e rende disponibili dei costrutti e delle classi per la gestione concorrente.
![[drawing 1]]
> Fine Pdf 1 inizio Pdf 2.
# Da Programmi a Modelli E Viceversa
![[drawing 2]]
Questo approccio crea un grafo (rete di Petri con l'aggiunta delle azioni Atomiche).
A livello rigoroso per Speed independence assumption si intende:
> Modellare l'esecuzione di un programma concorrente come una sequenza di azioni ottenute dall' interleaving arbitrario delle azioni dei processi. 

> Per **Scenario/Computazione** si intende una sequenza d'esecuzione che può accadere come risultato dell' interleaving.

> I modelli sono utili per capire se un programma va in deadlock oppure no (non ho idea come).

## Esempio
![[Screenshot 2026-02-20 alle 10.48.52.png]]
![[Screenshot 2026-02-20 alle 10.47.55.png]]

### Come Calcolare Il Numero Di Scenari in Base Al Numero Di Processi Ed Il Numero Di Azioni Che Essi Hanno (Poco importante)
![[Screenshot 2026-02-20 alle 10.52.32.png]]
## Strutture Non Atomiche
La parola "atomico" può essere definito sia alle **azioni** ma anche alle **strutture dati**.
> Un data object è definibile come atomico se può essere in un numero finito di stati uguale al numero di valori che può assumere, quindi le operazioni su di esso cambiano in maniera atomica lo stato del data object.

Tipicamente i tipi primitivi nei linguaggi concorrenti sono atomici, ma non sempre (*double* in Java non lo è ad esempio).
I tipi di dato astratti composti da più strutture dati semplici sono genericamente non atomiche.
## Sezione criti