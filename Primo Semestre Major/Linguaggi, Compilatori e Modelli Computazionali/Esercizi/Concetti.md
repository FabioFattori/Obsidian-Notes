# Concetti

## Transformazioni Linguaggi
### NFA E DFA
Per ogni NFA $N$ c'è un DFA $D$ tale che $L(D) = L(N)$.
Questo comporta una costruzione a sottoinsiemi, un esempio importante di come un automa B puo’ essere costruito da un altro automa A.
Quindi partiamo da:
![[Pasted image 20260119174157.png]]
otteniamo la tabella (che è la cosa che ci permette di ottenere il DFA)
![[Pasted image 20260119174214.png]]
e poi lavoriamo con i sottoinsiemi partendo da $\{q_0\}$ e quindi si ottiene questo:
![[Pasted image 20260119174313.png]]
### Da $\epsilon$-NFA a DFA
![[Pasted image 20260120172607.png]]
![[Pasted image 20260119174606.png]]
Si parte da questo:
![[Pasted image 20260119180715.png]]
poi si trova la $ENCLOSE(q_0)$ in questo caso $\{q_0, q_1\}$ e questo è lo stato iniziale.
Poi si esegue in maniera iterativa il seguente algoritmo:
1. si trovano l'insieme di stati che si riesce a raggiungere  per ogni simbolo dell'alfabeto partendo da ciascuno stato del sottoinsieme:
	Esempio:
	Parto da $q_0$ avente come simbolo il + ed ho come sottoinsieme $\{q_1\}$, poi parto da $q_1$ e non vado da nessuna parte quindi facendo l'unione tra $\{q_1\}$ e insieme vuoto otterrò un sottoinsieme che mi rappresenta un nuovo stato del DFA. 
2. Finiti i simboli dell'alfabeto da provare per ogni stato del sottoinsieme (ovvero il nuovo stato del DFA finale) si procede in maniera iterativa per ogni nuovo stato individuato
3. Il DFA è completo quando non vi sono più nuovi sottoinsiemi individuati
### Da DFA/NFA a Espressione Regolare
Per quanto riguarda SOLO la parte finale
![[Pasted image 20260119201706.png]]
Guarda questo per piangere fortissimo
![[NFA2RE]]Ulteriore esempio
![[Pasted image 20260119203837.png]]
![[Pasted image 20260119203852.png]]
### Da Espressione Regolare a $\epsilon$-NFA
Prendi questi blocchettini:
- $R+S$
	![[Pasted image 20260119204227.png]]
- $RS$
	![[Pasted image 20260119204239.png]]
- $R$* 
	![[Pasted image 20260119204251.png]]
Esempio:
trasformiamo $(0+1)$* $1(0+1)$ ottengo questo:
![[Pasted image 20260119210555.png]]
che se ci pensi ci sta, qui è letteralmente come giocare con i lego.
## Pumping Lemma LR
![[Pasted image 20260125215528.png]]
Per gli esercizi, spesso viene chiesto che tipo di linguaggio è un linguaggio fornito, per capire se NON è regolare ti tocca fare il pumping lemma:
- supponi che sia regolare, quindi rispetta il pumping lemma
- definisci tutto le cagate di formule del pumping lemma, specialmente w, che raffigura la nostra word, quindi una stringa
- poi provi a spare $k=2$(raddoppi la lunghezza di y) oppure $k=0$(elimini y) e vedi se le stringhe ottenute appartengono comunque al linguaggio, se no, stai pur sicuro che non è regolare lo zio.
## Equivalenza E Minimizzazione
due stati si definiscono equivalenti ($\equiv$) quando una stringa $w$ viene accettata o respinta dal linguaggio partendo da entrambi i due stati.
Esempio:
![[Pasted image 20260119231946.png]]
Prendiamo per esempio A ed E:
![[Pasted image 20260119232324.png]]
Allora teoricamente dovresti provare un pò tutte le combo di $w$ ma, dato che stiamo parlando di un DFA ha quindi senso provare solo le $w$ con lunghezza massima $n$ che rappresenta in numero di stati presenti nel DFA.
Nell'esempio $A\equiv E$ perchè i singoli char dell'alfabeto portano i due stati negli stessi stati quindi bella sono equivalenti.
![[Pasted image 20260119232644.png]]
quelli con le $x$ sono distinguibili.
### Equivalenza Tra Linguaggi Regolari
![[Pasted image 20260119232734.png]]
Il punto 3 è quello importante, di fatto si svolge così:
![[Pasted image 20260119232823.png]]
### Minimizzazione
Prendendo sempre questo DFA come esempio:
![[Pasted image 20260119231946.png]]
lui ha le seguenti classi di equivalenza:
{{A, E}, {B, H}, {C}, {D, F }, {G}} quindi:
![[Pasted image 20260119232955.png]]
abbastanza easy.
## CFG E CFL (linguaggi liberi)
### Albero Sintattico
![[Pasted image 20260120174349.png]]
#### Prodotto Di Un Albero Sintattico
![[Pasted image 20260120174710.png]]
#### Ambiguità Delle Grammatiche
![[Pasted image 20260120175129.png]]
Teorema 5.29: Data una CFG $G$, una stringa terminale $w$ ha due distinti alberi sintattici se e solo se $w$ ha due distinte derivazioni a sinistra dal simbolo iniziale. (anche destra)
![[Pasted image 20260120175841.png]]L'ambiguità si può rimuovere dando una precedenza tra gli operatori e dando delle regole di raggruppamento per lo stesso operatore.
### Da PDA Ad Accettazione per Pila Vuota a PDA Ad Accettazione per Stato Finale
![[Pasted image 20260120194158.png]]
### Da PDA Ad Accettazione per Stato Finale a PDA Ad Accettazione per Pila Vuota
![[Pasted image 20260120194344.png]]
![[Pasted image 20260120194444.png]]
### IMPORTANTISSIMO PORCODIO
![[Pasted image 20260120201204.png]]
### Da CFG a PDA
![[Pasted image 20260120201521.png]]
Di fatto fai questo:
![[Pasted image 20260120201600.png]]
Quindi:
- il PDA ha solo uno stato che è $q$
- si parte definendo la trasformazione  
    $δ(q,ϵ,S)$, dove $S$ è il simbolo di start, e come risultati si mettono **tutte le produzioni della grammatica** con $S$ a sinistra
- per **ogni non terminale $A$**,  
    $\delta(q, \epsilon, A)$ restituisce **le produzioni di $A$** nella CFG
- per **ogni simbolo terminale $a∈Σ$**,  
    si definisce  $δ(q,a,a)=\{(q,ϵ)\}$ che serve a **consumare il simbolo dall’input e dallo stack**
### Da PDA a CFG
![[Pasted image 20260120230522.png]]
Esempio 1:
![[Pasted image 20260120230756.png]]
Cosa succede:
![[Pasted image 20260120232833.png]]
Questo passaggio va fatto senza guardare le trasformazioni, bisogna mettere tutte le combinazioni boia cane.

![[Pasted image 20260120232839.png]]
In maniera più specifica => S è composto (tramite la pipe | ) da tutte le trasformazioni (che non sono indicate mannaggia alla madonna) che portano l'automa in accettazione, ovvero a stack vuoto.
Dobbiamo considerare che partiamo dallo stato iniziale $q_0$ e abbiamo $Z_0$ nello stack, quindi dobbiamo scrivere al posto di $q_f$ tutti gli altri stati :
Esempio:
se io ho due stati $q$ e $p$ con stato iniziale $q$ e $Z_0$ come valore iniziale di stack ho che:
$S\rightarrow [qZ_0q]\\\ |\\\ [qZ_0p]$.
QUANDO hai una cosa di questo tipo $δ(p,a,A)=(q,B)$ applichi la seguente formula:$$[pAr]→a[qBr]$$
QUANDO hai una situazione del tipo $\delta(q,a,A)=\{(q,BC)\}$ con $B$ che può essere uguale ad $A$ fai questo:
![[Pasted image 20260121162520.png]]
QUANDO HAI QUESTO FAI COSì:
quindi di fatto fai tutte le possibili combinazioni di $r$ ed $s$.
![[Pasted image 20260120232859.png]]
Se invece della $\epsilon$ nella tripla hai un terminale avrai questo:$$(p,a,A)\rightarrow (q,\epsilon) \\\ [pAq]\rightarrow a$$![[PDA2CFG]]
## Forma Normale Di Chomsky
Per prima cosa bisogna semplificare la CFG associata al CFL, e per farlo facciamo prima questi passaggi:
1. Eliminiamo i simboli non generanti e poi i simboli non raggiungibili
	Per non generanti si intende i simboli per i quali non vi è una trasformazione:
	![[Pasted image 20260121172251.png]]
	$B$ in questo caso non è generante quindi si elimina TUTTA la trasformazione $S\rightarrow AB$ facendo diventare la grammatica $$S\rightarrow a,A\rightarrow b$$
	Mentre per simboli non raggiungibili si intendono quei simboli che, partendo da $S$ non possono essere MAI raggiunti, usando l'esempio di prima $A$ è non raggiungibile, quindi possiamo tirare nel casino $A\rightarrow b$ lasciando solo $S\rightarrow a$ 
2. Eliminiamo le produzione $\epsilon$
	Ovvero vanno AGGIUNTE tutte le possibili combinazioni quando un simbolo ha una trasformazione che lo porta ad annullarsi ($\epsilon$).
	Per fare ciò bisogna seguire la seguente procedura:
	- se ho $B\rightarrow \alpha A \beta$ con $\alpha$ e $\beta$ che sono variabili oppure simboli terminali
	- tolgo con cattiveria $A \rightarrow \epsilon$ 
	- AGGIUNGO alla trasformazione $B$ questo: $B\rightarrow \alpha\beta$
	- Quindi ottengo questo: $B\rightarrow \alpha A \beta \\\ | \\\ \alpha\beta$ 
	Continuo in maniera iterativa fino a che non ci sono più trasformazioni del tipo $A \rightarrow \epsilon$ 
3. Eliminiamo le produzioni unità
	Ovvero eliminiamo le produzioni semplici del tipo $A\rightarrow B$, tale eliminazione avviene espandendo la produzione, ovvero sostituendo $B$ con tutte le sue trasformazioni:
	$$\begin{split}A → B | a \\	B → C | b\end{split}$$
	quindi in questo caso abbiamo che $A\rightarrow B$ può essere espansa e diventa pari a $A\rightarrow C \\\ | \\\ b$ e quindi si ottiene: $A\rightarrow C \\\ | \\\ b \\\ | \\\ a$.
	**CI POSSONO ESSERE DEI CICLI** perchè siamo gay noi ce ne sbattiamo più o meno il cazzo perchè quando torniamo nella situazione iniziale TIRIAMO NEL CASINO la produzione risultante:
	$$\begin{split}A → B | a \\	B → C | b \\ C → A | c\end{split}$$
	In questo esempio infatti abbiamo che:
	- $A\rightarrow C \\\ | \\\ b$
	- poi devo rifare per $C$ quindi ottengo $A\rightarrow A \\\ | \\\ c \\\ | \\\ b$ 
	- ed infine $A\rightarrow B \\\ | \\\ a \\\ | \\\ c \\\ | \\\ b$
	- Noto che la trasformazione $A\rightarrow B$ l'ho già fatta quindi la tiro nel casino ed $A$ alla fine è così $A\rightarrow a \\\ | \\\ c \\\ | \\\ b$
### Ora Possiamo Trasformare Il CFG Semplificato Nella Forma CNF Seguendo I Passaggi
- Mettere TUTTI i simboli terminali in una nuova variabile singolarmente ($B\rightarrow x$) a meno che non siano già in questa forma
- SE una trasformazione ha come risultato un corpo di lunghezza $>2$ prendere tutte le variabili tralasciando la prima e metterle in una variabile:
	$A → B1B2 · · · Bk$ con $k>2$ allora devo fare così:$$\begin{split}A → B1C1\\ C1 → B2C2\\ · · ·\\ Ck−3 → Bk−2Ck−2 \\ Ck−2 → Bk−1Bk\end{split}$$
BENE! ora sei un figo ed hai la CFG in forma CNF.
## Pumping Lemma per CFG in Forma CNF
![[Pasted image 20260121182032.png]]
Anche questo è usato per dire se un linguaggio NON è un linguaggio libero dal contesto.
## Macchine Di Turing
![[Pasted image 20260121231107.png]]
## Linguaggi Ricorsivamente Enumerabili
![[Pasted image 20260121234230.png]]
## Linguaggi Ricorsivi
![[Pasted image 20260121234350.png]]
ogni linguaggio per cui sia possibile in modo automatico verificare se una data stringa vi appartiene oppure no è ricorsivo
## Linguaggio Diagonale
![[Pasted image 20260122184423.png]]![[Pasted image 20260122184614.png]]
![[Pasted image 20260122184627.png]]
## Linguaggio Universale
![[Pasted image 20260122184744.png]]
![[Pasted image 20260122184802.png]]
![[Pasted image 20260122185014.png]]
## Logica Di Base
![[Pasted image 20260122191503.png]]
### Propositional Logic
![[Pasted image 20260122191952.png]]
![[Pasted image 20260122192340.png]]
## LTL
Le logiche temporali permettono di esprimere proprietà temporali: 
	vere in alcuni “mondi”, false in altri.
> I “mondi” considerati corrispondono a diversi momenti temporali
![[Pasted image 20260123143050.png]]
![[Pasted image 20260123143305.png]]

$\diamondsuit$ rappresenta la frase "**adesso** o **in un futuro** la condizione si avvera"
$\square$ rappresenta la frase "la condizione è **sempre vera ora e nei mondi  futuri**" 
$u$  Usato per mettere in relazione due proposizioni, una vera ora ed in tutti momenti successivi fino ad un momento in cui è vera la seconda
![[Pasted image 20260123143729.png]]
### Annotazione Alternativa
![[Pasted image 20260123144724.png]]
#### Proprietà Safety
non si raggiungono mai stati con errori
Normalmente espresse così: $\square \neg...$   
#### Proprietà Liveness
prima o poi si eseguirà una certa azione
Normalmente espresse così:$\diamondsuit...$ 
#### Proprietà Fairness
se si richiede una cosa infinite volte, questa verrà eseguita infinite volte
$$\square \diamondsuit ready \rightarrow \square \diamondsuit run$$
## LTS
![[Pasted image 20260123145731.png]]
### Formalmente
![[Pasted image 20260123145745.png]]
## LTS Soddisfa LTL
![[Pasted image 20260123150533.png]]
### Formalmente
![[Pasted image 20260123150559.png]]
## Algebra Dei Processi
I sistemi modellati da tali automi (LTS) sono solitamente “sistemi concorrenti”.
Le “process algebra” sono un modo naturale per rappresentare sistemi di questo tipo 
- Descrivere ogni processo da solo
- Combinare le descrizioni di tali processi per ottenere l’intero sistema
Un processo è rappresentato come un LTS: 
- si danno nomi agli stati 
- per ogni stato si descrivono le transizioni che lo stato può fare
![[Pasted image 20260123160219.png]]
![[Pasted image 20260123160413.png]]
![[Pasted image 20260123160422.png]]
![[Pasted image 20260123160557.png]]
![[Pasted image 20260123160612.png]]
### Proprietà
![[Pasted image 20260123160811.png]]
![[Pasted image 20260123160739.png]]
### Hiding
definisce tramite la $@$ quali stati sono "visibili" e quindi sincronizzabili:
![[Pasted image 20260123173341.png]]
Le azioni non comprese dentro all'insieme della $@$ vengono rappresentate come un'azione "tau".
## Reti Di Pretri
Altro modo di rappresentare i sistemi concorrenti rispetto all'algebra dei processi.
![[Pasted image 20260123173628.png]]
### Formale
![[Pasted image 20260123174112.png]]
### Marking Graph
![[Pasted image 20260123174418.png]]
![[Pasted image 20260123174544.png]]
![[Pasted image 20260124134448.png]]
# How To
## Classificazione Dei Linguaggi
esempio:
> Si consideri il seguente linguaggio su alfabeto {0,1}: L = { vwvRwR | v e w sono numeri binari (inclusa la stringa vuota) } Classificare il linguaggio dicendo se è un linguaggio regolare, libero, ricorsivo, ricorsivamente enumerabile, o nemmeno ricorsivamente enumerabile. Giustificare formalmente la risposta.

Gli step vanno seguiti in fila, dato che $$\text{Regolari}⊂\text{Liberi dal contesto}⊂\text{Ricorsivi}⊂\text{Ricorsivamente enumerabili}$$
Steps:
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
	Se un linguaggio è ricorsivo è perforza anche RE, e se non è RE non è neanche Ricorsivo.
	Problema DECIDIBILE, se un linguaggio è CFL allora è anche Ricorsibi
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
	...
2. Guardo la prima produzione (S):
	guardo il risultato della produzione skippando tutti i terminali fino a che non trovo un terminale, quando lo trovo:
	- dopo c'è un terminale:
		esempio: S -> aBc.
		il Follow(B) diventa l'unione con il corrente Follow(B) e {c}.
	-  dopo c'è un non terminale:
		esempio: S -> aBCd.
		il Follow(B) diventa l'unione con il corrente Follow(B) e First(C) -{$\epsilon$}.
		Ora fai un check: $\epsilon \in \text{First}(C)$?
		- se si continui rifacendo il passo 2, quindi se c'è un terminale ecc...
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