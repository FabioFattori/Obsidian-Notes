# Compilatori
## TODO Fino a Secondo Pdf a Pag 29
### 14/10/2025 Ambiguità Inerente Fino a Pag 51
Un CFL (Context-Free Languages) è inerentemente ambiguo se tutte le grammatiche per $L$ sono ambigue.
Esempio:
$$\{a^n b^nc^md^m: n\geq 1,m\geq 1\} \cup \{a^n b^mc^md^m: n\geq 1,m\geq 1\}$$
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/1.png]]
#### Automi a Pila (Push Down Automaton)

> Da immaginare lo Stack sdraiato da sinistra a destra(sinistra next pop).

Un automa a pila PDA è in pratica un automa a stati finiti ($\epsilon$-NFA che è la versione più estesa deli automi a stati finiti) con una pila (struttura dati).
Non devono essere deterministici.
IMPORTANTE => è una pila perchè l'ultimo blocco che incontriamo è quello da cui dobbiamo partire, perchè funzioniona come un xml o comunque come una gestione a tag (html) quindi ha senso che sia una stack anzichè una queue.
1. Consuma un simbolo di input o esegue una transizione $\epsilon$.
2. Va in un nuovo stato (o rimane dove e’).
3. Rimpiazza il top della pila con una stringa (consuma il carattere in cima, e mette al suo posto una stringa, eventualmente vuota o uguale al carattere consumato lasciando quindi la pila inalterata) $\rightarrow$ fa un pop ed una push per rimpiazzare con un carattere scelto da noi!
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/2.png]]
Esempio:
$$L_{wwr} = \{ ww^r: w ∈ \{0,1\}^*\}$$
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/3.png]]
Punto 2 $\rightarrow$ il PDA ad ogni carattere prende due strade, la prima per provare a capire se è in mezzo non deterministica va nello stato $q_1$ e prova a matchare $ww^r$ con il primo elemento dello stack, se c'è un mismatch si blocca.

> UNA STRINGA è accettata quando sono in uno stato di accettazione e l'input è finito (è stato tutto "mangiato" dal PDA)

![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/4.png]]
in cima alla pila, dove c'è scritto $0,Z_0 /0\ Z_0$ che rappresenta questo:
- il primo zero limita l'input => ci deve essere lo zero in input e ci deve essere lo $Z_0$ sulla cima della pila
- mentre lo $/0 \ Z_0$ rapprenta la stringa da sostituire rendendo la pila in questo modo qui:
	  - Posizione 0 $\rightarrow$ $Z_0$ 
	  - Posizione 1 (prossimo pop) $\rightarrow$ 0
Queste transizioni non vanno a cambiare il contenuto ma anzi lo mantiene dallo stato $q_0$ allo stato $q_1$, in maniera tale da andare sempre avanti qualunque sia l'input, questa politica rimane fino al tratto da $q_1$ a $q_1$ nel quale avviene ad esempio:
	se c'è zero nell'input, pop del valore 0 che deve essere in cima alla pila e continuo fino ad avere solo $Z_0$ che mi fa il tratto da $q_1$ a $q_2$, quindi in stato di accettazione, ma la stringa potrebbe non essere accetta se l'input a questo punto non è ancora finito.
#### Significato Di $\epsilon$
$\epsilon$ in base a dove è vuol dire "qualsiasi valore" oppure "nulla":
- se è nell'input ad esempio con $\epsilon$ , $Z_0 \ /Z_0$ mi sta a significare $\rightarrow$ "qualsiasi valore ci sia di input e con $Z_0$ nella cima della pila, *non mangiare nulla dall'input*".
- mentre $0\ , \ 0 \ / \epsilon$ vuol dire "0 in input e 0 in cima alla pila, *mangia l'input e non mettere niente nella pila*"
## Definizione Formale Di PDA
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/5.png]]
uguale alla definizione degli $\epsilon$-NFA, in più c'è che la funzione degli $\epsilon$-NFA va da triple a coppie, si parla della funzione $\delta$, in più c'è $\Gamma^*$ che rappresenta degli sottoinsiemi di stringhe perchè è non deterministico.
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/6.png]]
### Descrizioni Istantanee
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/7.png]]
- $a \ \rightarrow$ primo simbolo dell'input
- $X \ \rightarrow$ stringa che va nello stack
ed infatti dopo la transizione si ha che l'automa può essere rappresentato dalla seguente tripla $(p,w,a\beta)$ dove:
- $p \ \rightarrow$ è il nuovo stato dell'automa
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/9.png]]
#### Accettazione per Stato Finale
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/8.png]]
[[14_10_2025]]
### Accettazione per Pila Vuota
![[10.jpeg]]

> Adesso chiedo che la pila sia vuota e $q$ può essere uno stato non di accettazione

## Noi Vogliamo Arrivare a Questo (Parte Destra Delle Frecce, Da PDA a PDA)
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/13.png]]
Sono equipotenti, e possiamo passare da uno all'altro attraverso l'applicazione di un algoritmo.
### Da Pila Vuota a Stato Finale
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/11.png]]
Consiste in una emulazione di un PDA ad accettazione per Pila vuota su un PDA ad accettazione per Stato finale.
Di fatto prima di far partire il PDA "emulato" si aggiunge una $X_0$ nuovo, poi si fa esegue $\epsilon X_0 /Z_0X_0$ che rende la pila così:
- posizione 0 $\rightarrow$ $X_0$
- posizione 1 (next pop) $\rightarrow$ $Z_0$ 
partire il PDA emulato, quando egli finisce ad ogni stato parto una transizione che chiede che ci sia $X_0$ nella pila e porta il PDA da pila vuota allo stato finale del PDA a stato finale(padre) ![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/14.png]]
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/15.png]]
### Da Stato Finale a Pila Vuota
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/12.png]]
Qua invece si mettono delle transizioni ad ogni stato del PDA a stato finale che porta ad uno stato specifico (svuotatore) che cicla fino a quando la pila non è vuota, e per evitare che la pila si svuoti a caso (cosa che non vogliamo se no succede il delirio) facciamo come prima, quindi ci mettiamo un $X_0$.
## Adesso Faccio la Parte Sinistra Delle Frecce (Da PDA a Grammatica)
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/16.png]]
Left-Most.
Lui considera la variabile più a sinistra e viene messa nello stack al next pop.
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/17.png]]![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/18.png]]![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/19.png]]
## 15/10/2025 Fino a Pag
### Da PDA a CFG
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/20.png]]![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/21.png]]
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/23.png]]
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/24.png]]
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/25.png]]
### PDA Deterministici
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/26.png]]
### DPDA Che Accettano per Stato Finale
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/27.png]]
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/28.png]]
### DPDA Che Accettano per Pila Vuota
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/29.png]]
### DPDA E Non Ambiguità
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/30.png]]
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/31.png]]
# 21/10/2025 - Continuo Da Pagina 64
## Proprietà Dei CFL
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/32.png]]
### Forma Normale Di Chomsky
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/33.png]]
l'albero sintattico della grammatica è binario.
Perderemo la stringa vuota se seguiamo questa forma normale di Chomsky, perchè non possiamo più rappresentare $\epsilon$.
#### Eliminazione Simboli Inutili
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/34.png]]
##### Esempio
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/imgs/35.png]]
#### Eliminazione Produzioni $\epsilon$
![[36.png]]
##### Esempio
![[37.png]]
#### Eliminazione Produzione Unità
![[38.png]]
![[39.png]]
![[40.png]]
##### PROBLEMA - Presenza Di Cicli
Questa trasformazione non va bene nei linguaggi che rappresentano cicli, bisogna fare un accorgimento:
Se incontro una produzione che ho già espanso, posso fermarmi ed eliminarla come di seguito:
![[41.png]]
## Forma Normale Di Chomsky per CNF
![[42.png]]
![[43.png]]
## Pumping Lemma per CFL
![[44.png]]
### Enunciato
![[45.png]]
GUARDA DA PAGINA 85 A PAG 86 nel pdf.
Sto qui sta parlando di fare botanica, ma che cazzo vuol dire porcaccio il dio.
### Applicazione Del Pumping Lemma per CFL
Linguaggio di esempio:
ha due 1 in mezzo a tre gruppi di 0 di numero uguale $\rightarrow$ 00010001000
![[46.png]]
### Proprietà Di Chiusura Dei CFL
![[47.png]]
## Proprietà Di Chiusura Dei CFL
![[48.png]]
### I CFL Non Sono Chiusi Rispetto All'intersezione
![[49.png]]
### Operazioni Su Liberi E Regolari
![[50.png]]
![[51.png]]
![[52.png]]
## Proprietà Di Decisione per CFL
![[53.png]]
### Verificare Se Un CFL È Vuoto
![[54.png]]
![[55.png]]
## Problemi Indecidibili per CFL
![[56.png]]
# FINE PARTE TEORICA (primo pdf)
---
# Compilatori
## Struttura Di Un Compilatore
![[57.png]]
Le prime tre fasi sono anche dette frontend, perchè devono controllare l'input, dopo le prime 2 fasi si crea un albero sintattico.
### Scanning
![[58.png]]
### Parsing
![[59.png]]
Diagramma di una frase:
![[60.png]]
Con un linguaggio di programmazione in maniera analoga:
![[61.png]]
### Semantic Analysis
![[62.png]]
![[63.png]]
### Code Generation
![[64.png]]
### Riassunto Struttura Di Un Compilatore
![[65.png]]
Il Parser è il master che orchestra il parsing del codice, e sarà lui a chiamare il lexer quando ne ha bisogno.
# Building a Lexer
dato il codice di input devo assegnare ad ogni partizione dell'input un ruolo (token).
Ogni variabile viene identificata tramite il suo nome che viene chiamato _lessema_ come da esempio:
![[66.png]]
Il numero di linea serve per dire all'utente tramite una notifica dove si trova il possibile errore di sintassi.
## Come Costruire Un Lexer
Non è facile farcelo a mano, noi ci basiamo sui lexer generator cosicchè noi possiamo concentrarci nel descrivere i lessema ed i token.
![[67.png]]
![[68.png]]
### Esempio Di Lexer Imperativo (come Java)
![[69.png]]
Esempio di implementazione:
![[70.png]]
Problema:
devi fare "undoNextChar" perchè il ciclo si è mangiato un carattere di troppo per capire che il nome della variabile è finito, _Ambiguo_.
#### Maximal Match Rule
![[71.png]]
Lo string di input è partizionato in lessemi più grandi possibile.
#### What VS How
- What:
	![[72.png]]
	![[73.png]]
![[74.png]]
### Lexer Dichiarativo
Dai un occhio all'esempio da pagina 27 a pagina 30.
Concetto importante: 
>_lookahead_ $\rightarrow$ operazione per vedere avanti che carattere ho e in base a quello decidere cosa fare, nel nostro caso specifico devo capire se il nome della variabile è finito oppure no.

Idea:
Proviamo ad aggiungere l'operazione _ASSIGN_:
Problema:
