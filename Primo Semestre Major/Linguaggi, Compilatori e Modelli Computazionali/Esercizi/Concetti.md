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
## Pumping Lemma
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
![[Pasted image 20260120232839.png]]
In maniera più specifica => S è composto (tramite la pipe | ) da tutte le trasformazioni (che non sono indicate mannaggia alla madonna) che portano l'automa in accettazione, ovvero a stack vuoto.
Dobbiamo considerare che partiamo dallo stato iniziale $q_0$ e abbiamo $Z_0$ nello stack, quindi dobbiamo scrivere al posto di $q_f$ tutti gli altri stati :
Esempio:
se io ho due stati $q$ e $p$ con stato iniziale $q$ e $Z_0$ come valore iniziale di stack ho che:
$S\rightarrow [qZ_0q]\\\ |\\\ [qZ_0p]$.

![[Pasted image 20260120232850.png]]
![[Pasted image 20260120232859.png]]