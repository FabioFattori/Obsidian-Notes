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
### Da Espressioni Regolari a $\epsilon$-NFA
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
![[Pasted image 20260119223836.png]]
![[Pasted image 20260119223857.png]]
Per gli esercizi, spesso viene chiesto che tipo di linguaggio è un linguaggio fornito, per capire se NON è regolare ti tocca fare il pumping lemma:
- supponi che sia regolare, quindi rispetta il pumping lemma
- definisci tutto le cagate di formule del pumping lemma, specialmente w, che raffigura la nostra word, quindi una stringa
- poi provi a spare $k=2$(raddoppi la lunghezza di y) oppure $k=0$(elimini y) e vedi se le stringhe ottenute appartengono comunque al linguaggio, se no, stai pur sicuro che non è regolare lo zio.
## Proprietà Di Chiusura ???
## Proprietà Di Decisione ??? no Idea a Che Cazzo Servano PORCODIO
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
## Forma Normale di Chomsky
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
### Ora possiamo trasformare il CFG semplificato nella forma CNF seguendo i passaggi:
- Mettere TUTTI i simboli terminali in una nuova variabile singolarmente ($B\rightarrow x$) a meno che non siano già in questa forma
- SE una trasformazione ha come risultato un corpo di lunghezza $>2$ prendere tutte le variabili tralasciando la prima e metterle in una variabile:
	$A → B1B2 · · · Bk$ con $k>2$ allora devo fare così:$$\begin{split}A → B1C1\\ C1 → B2C2\\ · · ·\\ Ck−3 → Bk−2Ck−2 \\ Ck−2 → Bk−1Bk\end{split}$$
BENE! ora sei un figo ed hai la CFG in forma CNF.
## Pumping Lemma per CFG in forma CNF
![[Pasted image 20260121182032.png]]
Anche questo è usato per dire se un linguaggio NON è un linguaggio libero dal contesto.
## Macchine di Turing
![[Pasted image 20260121231107.png]]
## Linguaggi Ricorsivamente Enumerabili
![[Pasted image 20260121234230.png]]
## Linguaggi Ricorsivi
![[Pasted image 20260121234350.png]]
ogni linguaggio per cui sia possibile in modo automatico verificare se una data stringa vi appartiene oppure no è ricorsivo
## Linguaggio Diagonale
![[Pasted image 20260122184423.png]]![[Pasted image 20260122184614.png]]
![[Pasted image 20260122184627.png]]
## Linguaggio universale
![[Pasted image 20260122184744.png]]
![[Pasted image 20260122184802.png]]
![[Pasted image 20260122185014.png]]
## Logica di base
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
