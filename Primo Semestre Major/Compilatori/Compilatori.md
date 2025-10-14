# Compilatori
## TODO Fino a Secondo Pdf a Pag 29
### Ambiguità Inerente
Un CFL (Context-Free Languages) è inerentemente ambiguo se tutte le grammatiche per $L$ sono ambigue.
Esempio:
$$\{a^n b^nc^md^m: n\geq 1,m\geq 1\} \cup \{a^n b^mc^md^m: n\geq 1,m\geq 1\}$$
![[Primo Semestre Major/Compilatori/imgs/1.png]]#### Automi a Pila (Push Down Automaton)
Un automa a pila PDA è in pratica un automa a stati finiti ($\epsilon$-NFA che è la versione più estesa deli automi a stati finiti) con una pila (struttura dati).
Non devono essere deterministici 