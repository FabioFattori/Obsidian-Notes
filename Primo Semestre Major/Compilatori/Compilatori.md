# Compilatori
## TODO Fino a Secondo Pdf a Pag 29
### 14/10/2025 Ambiguità Inerente
Un CFL (Context-Free Languages) è inerentemente ambiguo se tutte le grammatiche per $L$ sono ambigue.
Esempio:
$$\{a^n b^nc^md^m: n\geq 1,m\geq 1\} \cup \{a^n b^mc^md^m: n\geq 1,m\geq 1\}$$
![[Primo Semestre Major/Compilatori/imgs/1.png]]#### Automi a Pila (Push Down Automaton)
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
```
UNA STRINGA è accettata quando sono in uno stato di accettazione e l'input è finito (è stato tutto "mangiato" dal PDA)
```
![[Primo Semestre Major/Compilatori/imgs/4.png]]
in cima alla pila, dove c'è scritto $0,Z_0 /0\ Z_0$ che rappresenta questo:
- il primo zero limita l'input => ci deve essere lo zero e ci deve essere lo zero
- mentre lo $/o \