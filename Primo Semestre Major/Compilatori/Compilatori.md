# Compilatori
## TODO Fino a Secondo Pdf a Pag 29
### 14/10/2025 Ambiguità Inerente
Un CFL (Context-Free Languages) è inerentemente ambiguo se tutte le grammatiche per $L$ sono ambigue.
Esempio:
$$\{a^n b^nc^md^m: n\geq 1,m\geq 1\} \cup \{a^n b^mc^md^m: n\geq 1,m\geq 1\}$$
![[Primo Semestre Major/Compilatori/imgs/1.png]]
#### Automi a Pila (Push Down Automaton)
Un automa a pila PDA è in pratica un automa a stati finiti ($\epsilon$-NFA che è la versione più estesa deli automi a stati finiti) con una pila (struttura dati).
Non devono essere deterministici.
IMPORTANTE => è una pila perchè l'ultimo blocco che incontriamo è quello da cui dobbiamo partire, perchè funzioniona come un xml o comunque come una gestione a tag (html) quindi ha senso che sia una stack anzichè una queue.
1. Consuma un simbolo di input o esegue una transizione $\epsilon$.
2. Va in un nuovo stato (o rimane dove e’).
3. Rimpiazza il top della pila con una stringa (consuma il carattere in cima, e mette al suo posto una stringa, eventualmente vuota o uguale al carattere consumato lasciando quindi la pila inalterata) $\rightarrow$ fa un pop ed una push per rimpiazzare con un carattere scelto da noi!
![[Primo Semestre Major/Compilatori/imgs/2.png]]
Esempio:
$$L_{wwr} = \{ ww^r: w ∈ \{0,1\}^*\}$$
![[Primo Semestre Major/Compilatori/imgs/3.png]]
Punto 2 $\rightarrow$ il PDA ad ogni carattere prende due strade, la prima per provare a capire se è in mezzo non deterministica va nello stato $q_1$ e prova a matchare $ww^r$ con il primo elemento dello stack, se c'è un mismatch si blocca.
> UNA STRINGA è accettata quando sono in uno stato di accettazione e l'input è finito (è stato tutto "mangiato" dal PDA)

![[Primo Semestre Major/Compilatori/imgs/4.png]]
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
![[Primo Semestre Major/Compilatori/imgs/5.png]]
uguale alla definizione degli $\epsilon$-NFA, in più c'è che la funzione degli $\epsilon$-NFA va da triple a coppie, si parla della funzione $\delta$, in più c'è $\Gamma^*$ che rappresenta degli sottoinsiemi di stringhe perchè è non deterministico.
![[Primo Semestre Major/Compilatori/imgs/6.png]]
### Descrizioni Istantanee
![[Primo Semestre Major/Compilatori/imgs/7.png]]
- $a \ \rightarrow$ primo simbolo dell'input
- $X \ \rightarrow$ stringa che va nello stack
ed infatti dopo la transizione si ha che l'automa può essere rappresentato dalla seguente tripla $(p,w,a\beta)$ dove:
- $p \ \rightarrow$ è il nuovo stato dell'automa![[Primo Semestre Major/Compilatori/imgs/9.png]]
#### Accettazione per Stato Finale
![[Primo Semestre Major/Compilatori/imgs/8.png]]
[[14_10_2025]]
### Accettazione per Pila Vuota
![[10.jpeg]]
> Adesso chiedo che la pila sia vuota e $q$ può essere uno stato non di accettazione