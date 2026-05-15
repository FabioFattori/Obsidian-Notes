# Struttura Di Un Compilatore
![[Pasted image 20260514212035.png]]
## Analisi Lessicale E Sintattica
### Lexer
Lessemi e token => obiettivo dell'analisi lessicale:
![[Pasted image 20260514203438.png]]
#### Maximal Match Rule
![[Pasted image 20260514203529.png]]
#### Lexer Dichiarativo E Lexer Imperativo
![[Pasted image 20260514204134.png]]
Una volta ottenuti tutti i singoli FA dei token si mergiano per ottenere il lexer automaton:
![[Pasted image 20260514204642.png]]
#### Full Declarative Lexer
![[Pasted image 20260514204733.png]]
quando si parla di continuare a leggere nel punto  4, si intende l'implementare  il look ahead che in questo caso è unbounded => posso fare undo di qualsiasi numero di caratteri letti.
![[Pasted image 20260514204937.png]]
> Nella pratica l'automata è specificato tramite l'utilizzo delle espressioni regolari.
> ![[Pasted image 20260514205255.png]]

![[Pasted image 20260514205444.png]] 
### Generatori Di Lexer
![[Pasted image 20260514205841.png]]
Genera direttamente il FULL DECLARATIVE LEXER con anche le  priorità dei token e tutto.![[Pasted image 20260514210410.png]]
### Parser
![[Pasted image 20260514212147.png]]
![[Pasted image 20260514212208.png]]
dove il Parse Tree è:
![[Pasted image 20260514212249.png]]
![[Pasted image 20260514212427.png]]
#### Operazioni (task) Del Parser
![[Pasted image 20260514212550.png]]
> Un Parser così come un Lexer può essere generato dando in input una descrizione della struttura sintattica, ovvero come le espressioni, statement e definizioni sono fatte.

#### Generare Il Parser
![[Pasted image 20260514213730.png]]
![[Pasted image 20260514214111.png]]
> Le CFG sono una notazione naturale per descrivere strutture ricorsive come la struttura sintattica dei linguaggi.

![[Pasted image 20260514214047.png]]
#### Recursive Descent (Top Down)
![[Pasted image 20260515182438.png]]
nella pratica :
![[Pasted image 20260515182733.png]]
![[Pasted image 20260515182823.png]]
> i parser top down (ANTLR) funzionano tramite la discesa ricorsiva, ma essa non sempre funziona:![[Pasted image 20260515182304.png]]

![[Pasted image 20260515182940.png]]
> Questo procedimento è fatto AUTOMATICAMENTE da ANTLR

#### Tirando Le Somme
- strategia semplice  che può essere automatizzata
- è presente il backtracking => che la rende poco popolare a causa della sua inefficienza ma per linguaggi piccoli va bene 
- inefficienza che comunque può essere eliminata tramite la restrizione delle classi della grammatica
#### Predictive Parser
![[Pasted image 20260515183655.png]]
##### LL(1)
![[Pasted image 20260515183821.png]]
###### Left Factoring
![[Pasted image 20260515183851.png]]
#### Ambiguità
![[Pasted image 20260515184235.png]]
![[Pasted image 20260515184249.png]]
![[Pasted image 20260515184319.png]]
##### Definition
![[Pasted image 20260515184733.png]]
##### Come Sistema L'ambiguità
![[Pasted image 20260515184806.png]]
###### Dangling Else
![[Pasted image 20260515184838.png]]
![[Pasted image 20260515184924.png]]
![[Pasted image 20260515185149.png]]
##### Quindi?
![[Pasted image 20260515185327.png]]
![[Pasted image 20260515185356.png]]
> In ANTLR per di default viene utilizzata l'associazione a sinistra se 
> ```
> <assoc=right>
> ```
> non viene specificato

![[Pasted image 20260515185731.png]]
![[Pasted image 20260515185745.png]]
## Analisi Semantica
### Sematic analyzer
![[Pasted image 20260515213325.png]]
#### Symbol Table 
Il Compiler fino ad ora:
![[Pasted image 20260515190612.png]]
La symbol table ha:
![[Pasted image 20260515213406.png]]
> Per nesting level si intende il livello di scope al quale la variabile, il metodo o la classe appartiene

###### Static Scoping
![[Pasted image 20260515213924.png]]
![[Pasted image 20260515214018.png]]
###### Dynamic scoping
![[Pasted image 20260515214220.png]]
![[Pasted image 20260515214314.png]]
##### Rules for our language
> static scoping alla C++
![[Pasted image 20260515214519.png]]
![[Pasted image 20260515214641.png]]

> Una volta che TUTTE le dichiarazioni sono state visitate e tutti i  loro utilizzi linkati ai vari ID la symbol table non  sara più utile a nulla.
##### Operazioni sulla symbol table 
![[Pasted image 20260515215025.png]]
##### Possibili implementazioni della Symbol table
![[Pasted image 20260515215520.png]]
###### list of Hashtable  (Implementazione del  nostro progetto)
![[Pasted image 20260515215608.png]]
![[Pasted image 20260515215621.png]]
![[Pasted image 20260515215634.png]]
![[Pasted image 20260515215738.png]]
###### Hashtable of lists
![[Pasted image 20260515220339.png]]
> Il nesting level value in ogni list è IMPORTATISSIMO dato che ci permette di capire se l'id è stato definito nello scope corrente o in uno scope precedente

![[Pasted image 20260515220505.png]]
![[Pasted image 20260515220517.png]]
![[Pasted image 20260515220534.png]]
#### Type Checking
![[Pasted image 20260515221816.png]]
##### Type System
![[Pasted image 20260515221607.png]]
##### Type Inference
![[Pasted image 20260515221916.png]]
![[Pasted image 20260515222000.png]]
> le regole logiche vengono utilizzate perchè il type checking ed la inference è strettamente logica

