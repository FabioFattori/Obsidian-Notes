# Transformazioni Linguaggi
## NFA E DFA
Per ogni NFA $N$ c'è un DFA $D$ tale che $L(D) = L(N)$.
Questo comporta una costruzione a sottoinsiemi, un esempio importante di come un automa B puo’ essere costruito da un altro automa A.
Quindi partiamo da:
![[Pasted image 20260119174157.png]]
otteniamo la tabella (che è la cosa che ci permette di ottenere il DFA)
![[Pasted image 20260119174214.png]]
e poi lavoriamo con i sottoinsiemi partendo da $\{q_0\}$ e quindi si ottiene questo:
![[Pasted image 20260119174313.png]]
## Da $\epsilon$-NFA a DFA
![[Pasted image 20260119174606.png]]
Si parte da questo:
![[Pasted image 20260119180715.png]]
poi si trova la $ENCLOSE(q_0)$ in questo caso $\{q_0, q_1\}$ e questo è lo stato iniziale.
Poi si esegue in maniera iterativa il seguente algoritmo:
1. si trovano l'insieme di stati che si riesce a raggiungere  per ogni simbolo dell'alfabeto partendo da ciascuno stato del sottoinsieme:
	Esempio:
	Parto da $q_0$ avente come simbolo il +
2. trovati tutti i  sottoinsiemi per 