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