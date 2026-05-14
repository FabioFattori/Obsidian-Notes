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
