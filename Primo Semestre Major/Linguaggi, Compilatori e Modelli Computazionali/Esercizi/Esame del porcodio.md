# Esame Del Porcodio

## Teoria
### Regex To $\epsilon$-NFA
????
### $\epsilon$-NFA To DFA
![[Pasted image 20260120172607.png]]
### CFG to PDA
![[Pasted image 20260127005556.png]]
### Pumping Lemma REG Con Dimostrazione
![[Pasted image 20260127005541.png]]
### Pumping Lemma CFL Con Dimostrazione
![[Pasted image 20260121182032.png]]
![[Pasted image 20260127010150.png]]
Consideriamo un cammino $A0$,$A1$ … $Aka$ di lunghezza massima: ha lunghezza $≥ m + 1$.
Esistono $i \neq j$ tali che $A_i = A_j$ (assumiamo che $i, j$ siano fra le ultime $m + 1$ variabili del cammino)
- Osservazione 1: l’albero radicato in $A_i$ ha altezza $≤ m + 1$, quindi la stringa corrispondente ha lunghezza $≤ 2^m = n$ (cioe’ $|vwx| ≤ n$) 
- Osservazione 2: le stringhe $v$ e $x$ non possono essere entrambe vuote in quanto $A_i$ (essendo la grammatica in CNF) genera due variabili entrambe non annullabili (quindi $|vx| > 0$) 
- Osservazione 3: l’albero sintattico ottenuto ripetendo un numero arbitrario di volte (possibilmente anche $0$ volte) la parte di albero radicato in $A_i$ meno l’albero radicato in $A_j$, continua ad essere un albero sintattico corretto (quindi $\forall i ≥ 0, uv^iwx^iy ∈ L$)
## How To Esercizi
## Classificazione Dei Linguaggi
esempio:
> Si consideri il seguente linguaggio su alfabeto {0,1}: L = { vwvRwR | v e w sono numeri binari (inclusa la stringa vuota) } Classificare il linguaggio dicendo se è un linguaggio regolare, libero, ricorsivo, ricorsivamente enumerabile, o nemmeno ricorsivamente enumerabile. Giustificare formalmente la risposta.

Gli step vanno seguiti in fila, dato che $$\text{Regolari}\subset\text{Liberi dal contesto}\subset\text{Ricorsivi}\subset\text{Ricorsivamente enumerabili}$$Steps:
1. Controllo della regolarità (REG)
	Se $L$ fosse regolare, esisterebbe un $p>0$ (costante di pumping) tale che ogni stringa $s \in L$ con $∣s∣≥p$ si può scrivere come $s=xyz$ con:
	1. $∣xy∣≤p$
	2. $∣y∣>0$
	3. $xy^i z \in L$ per ogni $i≥0$ 
	Tipicamente se ci sono simmetrie e/o conteggi troppo grandi non è regolare:
	>i linguaggi regolari non possono "contare" o memorizzare lunghezze arbitrariamente grandi
	
2. Controllo CFL
	Usare o il pumping lemma per CFL oppure la chiusura dei CFL:
	1. Pumping lemma:
		Se $L$ è un linguaggio context-free, allora esiste una costante $p>0$ tale che **ogni stringa $s∈L$ con $∣s∣≥ p$ può essere scritta come**: $s=uvwxy$
		con:
		1. $∣vwx∣≤p$
		2. $∣vx∣≥1$ (cioè almeno un simbolo in $v$ o $x$)
		3. $uv^i w x^i y \in L$ per ogni $i≥0$ 
		> Per Entrambi i pumping lemma solitamente si sceglie una $i$ uguale a $0$ oppure a $2$ che tipicamente rompe $\in L$.
		
	2. Chiusura dei CFL:
		si scompone il linguaggio dato in due sottolinguaggi e si cerca di dimostrare che $L_1$ ed $L_2$ siano uno regolare e l'altro libero, oppure entrambi liberi perchè $L_1 \in REG, \\\ L_2 \in CFL, \\\ L_1\cap L_2 \in CFG$ e $L_1\cap L_2 = L$ che è il linguaggio fornito.
3. Controllo Ricorsivo
	Se esiste una TM (algoritmo) che termina se $x\in L$ e accetta oppure termina se $x \not\in L$ se non accetta.
	Problemi DECIDIBILI.	
4. Controllo RE:
	Se esiste una TM (algoritmo) che termina se $x\in L$ e accetta, ed invece non termina MAI se $x\not\in L$ andando avanti all'infinito.
	Problema SEMI-DECIDIBILE
## Algoritmo Riempi Tabella
1. metti una x per le coppie del seguente tipo: 
	(stato d'accettazione, non stato d'accettazione)![[esempio]]
2. ora per ogni tipo di carattere dell'alfabeto segui le freccie delle coppie rimanenti, esempio:
	$\delta(q_1,a) \rightarrow q_2 \\\ , \\\ \delta(q_3,a) \rightarrow q_1$  $(q_2,q_3)$ questa coppia di stati ottenuti ha già una x nella tabella QUINDI la mettiamo anche per la coppia $(q_1,q_3)$, se invece avessimo ottenuto una coppia di stati senza x avremmo dovuto fare lo stesso test anche con $b$.
	NOTA => devi mettere una x diversa all'esame dato che ogni step che stiamo facendo è una PASSATA diversa da quella precedente, per esempio metti "xx"
3. Da qui in poi la lunghezza della stringa aumenta di 1 ad ogni passata (step) e con essa le diverse combinazioni che dobbiamo testare.
	Quindi dopo lo step 2 la stringa da dare in input al delta aumenta di uno, ma il meccanismo è sempre quello, se le due trasformazioni mi portano ad una coppia di stati che ha una x, metto una x, altrimenti mi faccio i CAZZI miei.
> Continuare fino a che avviene una passata che non mi fa mettere nessuna nuova x 

## Formule Logiche Dei Predicati Rispettate per Dei Modelli
![[Pasted image 20260125193741.png]]
Per ogni modello fornito devi fare le seguenti cose:
- capire bene su che universo si basa il modello, $M_1$ ad esempio si basa sui numeri naturali.
- identificare la formula cosa dice, esempio della prima formula in relazione con $M_1$:
	per ogni numero naturale ($x$) esiste un altro numero naturale ($y$) tale che il prodotto tra $y * y = x$ quindi ti sta dicendo che ogni numero naturale può essere rappresentato tramite il quadrato di un altro numero naturale.
	Dato che questa formula ha il $\forall$, **basta un solo numero** per il quale la formula non è vera per renderla **non soddisfatta**. 
Ripeti per ogni modello switchando il contesto.
## LL(1) Con Tabella
![[Primo Semestre Major/Linguaggi, Compilatori e Modelli Computazionali/Esercizi/LL1/es1]]
### Calcolo First
nella trasformazione prendi il primo simbolo terminale se presente, altrimenti prendi il first del simbolo non terminale e lo unisci con il first che stai calcolando, le condizioni in or sono anche esse da calcolare e da unire con il first che hai già calcolato.
S -> aBb
B -> cA | ε
A -> S | B

first(S) -> {a}
first(B) -> {c, ε} = {c} $\bigcup$ {$\epsilon$}
first(A) -> {a, c, ε} = {a} $\bigcup$ {c, $\epsilon$}    
$\epsilon$ si aggiunge solo quando TUTTO può sparire, se per qualche motivo hai una situa del genere:
S -> B
B -> ε

first(B) = {$\epsilon$} 
e basta il first di S non c'è 
![[Pasted image 20260126004231.png]]
### Calcolo Follow
1. follow iniziale:
	si calcolano solo i follow degli stati non terminali e partono tutti come insieme vuoto TRANNE lo stato iniziale ($S$) che ha un $ dentro.
	Follow(S) = {$}
	Follow(A) = {}
	…
2. Guardo la prima produzione (S):
	guardo il risultato della produzione skippando tutti i terminali fino a che non trovo un terminale, quando lo trovo:
	- dopo c'è un terminale:
		esempio: S -> aBc.
		il Follow(B) diventa l'unione con il corrente Follow(B) e {c}.
	-  dopo c'è un non terminale:
		esempio: S -> aBCd.
		il Follow(B) diventa l'unione con il corrente Follow(B) e First(C) -{$\epsilon$}.
		Ora fai un check: $\epsilon \in \text{First}(C)$?
		- se si continui rifacendo il passo 2, quindi se c'è un terminale ecc…
		- se no bella hai finito e continui a leggere la produzione fino alla fine.
	- dopo non c'è un beneamato cazzo:
		esempio: S -> aB.
		il Follow(S) diventa l'unione con il corrente Follow(S) e Follow(B)
3. continui con tutte le produzioni.
### Creazione Della Tabella
Sulle righe gli stati non terminali, sulle colonne gli stati terminali.
Leggi una produzione:
1. prendi il first di tale produzione e per ogni elemento fai questo:
	è $= \epsilon$?
	- NO:
		Ottieni una coppia: Stato finale di origini della produzione e valore del first i-esimo:
		esempio => S -> Ba, first(S) = {b}
		coppia \[S,b\] = Ba
		La coppia sono le coordinate della tabella dove bisogna scrivere il risultato della produzione 
	- SI:
		dici fanculo porcodio e inizi a ciclare su tutti i valori del Follow facendo la stessa cosa che fai quando hai un valore del first non $= \epsilon$.
## Da $\epsilon$-NFA a DFA
> consiglio: ti calcoli tutti gli $\epsilon \text{-ENCLOSE}$ degli stati forniti.

Parti dall'ENCLOSE dello stato iniziale dell'NFA.
ti fai la tabella con sulle colonne ogni carattere dell'alfabeto, e sulle righe solo ENCLOSE dello stato iniziale che è lo stato iniziale anche dell'DFA.
Ora parti da OGNI stato appartenente all'ENCLOSE e vedi se riesci ad arrivare in qualche altro stato utilizzando il carattere corrente (lo devi fare per tutti $\in \Sigma$).
Ora prendi tutti gli stati ottenuti da questo processo, li unisci in un unico insieme e devi calcolare l'$\epsilon \text{-ENCLOSE}$ di tale insieme (SE hai culo è pari ad un $\epsilon \text{-ENCLOSE}$ che hai già calcolato).
PARTE FINALE DI OGNI ITERAZIONE:
prendi $\epsilon \text{-ENCLOSE}$ che hai appena ottenuto e la schiaffi nella riga e nella colonna correnti.

E VAI AVANTI FINO A CHE NON TI SI AGGIUNGONO **STATI NUOVI** alla tabella, perchè ogni $\epsilon \text{-ENCLOSE}$ che inserisci nella tabella rappresenterà poi nel DFA un singolo stato e quindi ogni stato nuovo che metti nel corpo della tabella corrisponde ad una RIGA in più nella tabella stessa.
![[Pasted image 20260126190738.png]]
## Algebra Dei Processi LTS
Per prima cosa ti vengono forniti degli automi singoli e tu li devi fare, non c'è molto da dire se non che ogni transizione si trasforma in uno stato, ad esempio : X = (b->c->X) diventa un automa come segue:
![[ltsTONfa]]
Oppure A = (b->A | a->STOP):![[ltsTONFA2]]
Poi li dovrai mettere in parallelo quindi fai questo:
0. identifichi quali sono le transizioni in comuni e quali no perchè:
	- Quelle in COMUNE possono essere fatte quando ENTRAMBI gli stati la prevedono nei modelli singoli
	- Quelle NON in comune possono essere fatte da un singolo stato, che cambia, e l'altro rimane invariato 
1. parti da entrambi gli stati iniziali dei due modelli, e la loro copia è uno stato
2. PER OGNI carattere nell'insieme delle transizioni possibili ti fai le seguenti domande:
	la transizione è in comune?
	- SI => entrambi gli stati la devono poter fare per essere effettivamente presente nel modello parallelo
	- NO => solo uno degli stati la può fare quindi basta che tale stato ci sia nella coppia per farla accadere
3. SE la transizione può accadere hai un nuovo stato dato dalla coppia dei due (oppure uno nel caso della transizione NON in comune) stato di arrivo della transizione.
Ad esempio se devi fare $A||X$ ottieni questo:![[AAA]]
Una volta ottenuto il modello parallelo devi verificare se le espressioni logiche fornite dall'esercizio siano verificate, ovvero possono accadere.
> basta un caso in cui esse non siano verificate per renderle false.

Ricordandosi che:
- <> => prima o poi accadrà quello che c'è dopo (esempio: <> a)
- $\alpha => ()\beta$ => la presenza di $\alpha$ implica che poi otterrò $\beta$.
- \[\] => ottengo SEMPRE quello che c'è dopo
- \\/ => or, o uno o l'altro
- /\ => and
- $\neg$ => not
## Grammatica LR(1)
1. Ti verrà fornita una grammatica, ad essa aggiungi un nuovo stato iniziale allo stato iniziale già presente così $S'$->$S$.
2. Ora parti dallo stato che hai appena creato e ne crei uno nuovo che sarà un stato dell'automa LR che mo facciamo:
	Le regole sono queste:
	- parti da $S'$->$S$ e scrivi nell'insieme $S'$->$.S,$$
	- Ora devi espandere S scrivendo le sue produzioni nell'insieme AGGIUNGENDO a ciascuna il punto all'inizio del risultato della produzione mettendo a ciascuna il => $,$$ alla fine.
	- ORA se ci sono dei simboli non terminali devi seguire questo algoritmo:
		avrai una roba di questo tipo $[A → α · B β , x]$ dove $B$ è terminale tu devi solo creare questa espansione nuova da aggiungere all'insieme: $[B → · γ , \text{FIRST}(β x)]$  dove $\gamma$ è il risultato delle produzioni di $B$ (questo procedimento è da fare per ogniuna delle produzioni) ricordandosi che il $FIRST(\$) = \$$.
	Continui fino a che non puoi più espandere perchè quello che ottieni non è più della forma $[A → α · B β , x]$, NON IMPORTA SE $\beta$ è non terminale.
3. Ora il tuo insieme è uno stato dell'automa LR(1), e mo dobbiamo fare le transizioni, per farle e capire quali fare dobbiamo solo spostare il punto di una posizione verso destra:
	ESEMPIO => $S \rightarrow . Bb, \$$