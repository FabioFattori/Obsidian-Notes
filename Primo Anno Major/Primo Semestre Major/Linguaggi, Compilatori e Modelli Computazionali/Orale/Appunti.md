# Struttura di un compilatore
![[Pasted image 20260514212035.png]]
## Analisi lessicale e sintattica
### Lexer
Lessemi e token => obiettivo dell'analisi lessicale:
![[Pasted image 20260514203438.png]]
#### Maximal Match Rule
![[Pasted image 20260514203529.png]]
#### Lexer dichiarativo e lexer imperativo
![[Pasted image 20260514204134.png]]
Una volta ottenuti tutti i singoli FA dei token si mergiano per ottenere il lexer automaton:
![[Pasted image 20260514204642.png]]
#### Full declarative lexer
![[Pasted image 20260514204733.png]]
quando si parla di continuare a leggere nel punto  4, si intende l'implementare  il look ahead che in questo caso è unbounded => posso fare undo di qualsiasi numero di caratteri letti.
![[Pasted image 20260514204937.png]]
> Nella pratica l'automata è specificato tramite l'utilizzo delle espressioni regolari.
> ![[Pasted image 20260514205255.png]]

![[Pasted image 20260514205444.png]] 
### Generatori di lexer
![[Pasted image 20260514205841.png]]
Genera direttamente il FULL DECLARATIVE LEXER con anche le  priorità dei token e tutto.![[Pasted image 20260514210410.png]]
### Parser
![[Pasted image 20260514212147.png]]
![[Pasted image 20260514212208.png]]
dove il Parse Tree è:
![[Pasted image 20260514212249.png]]
![[Pasted image 20260514212427.png]]
#### Operazioni (task) del parser
![[Pasted image 20260514212550.png]]
> Un Parser così come un Lexer può essere generato dando in input una descrizione della struttura sintattica, ovvero come le espressioni, statement e definizioni sono fatte.

#### Generare il Parser
