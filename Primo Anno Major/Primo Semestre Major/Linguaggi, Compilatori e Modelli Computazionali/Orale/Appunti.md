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
### Sematic Analyzer
![[Pasted image 20260515213325.png]]
#### Symbol Table
Il Compiler fino ad ora:
![[Pasted image 20260515190612.png]]
La symbol table ha:
![[Pasted image 20260515213406.png]]
> Per nesting level si intende il livello di scope al quale la variabile, il metodo o la classe appartiene

##### Static Scoping
![[Pasted image 20260515213924.png]]
![[Pasted image 20260515214018.png]]
##### Dynamic Scoping
![[Pasted image 20260515214220.png]]
![[Pasted image 20260515214314.png]]
#### Rules for Our Language
> static scoping alla C++
![[Pasted image 20260515214519.png]]
![[Pasted image 20260515214641.png]]

> Una volta che TUTTE le dichiarazioni sono state visitate e tutti i  loro utilizzi linkati ai vari ID la symbol table non  sara più utile a nulla.
#### Operazioni Sulla Symbol Table
![[Pasted image 20260515215025.png]]
#### Possibili Implementazioni Della Symbol Table
![[Pasted image 20260515215520.png]]
##### List of Hashtable (Implementazione Del Nostro progetto)
![[Pasted image 20260515215608.png]]
![[Pasted image 20260515215621.png]]
![[Pasted image 20260515215634.png]]
![[Pasted image 20260515215738.png]]
##### Hashtable of Lists
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

![[Pasted image 20260515223014.png]]
![[Pasted image 20260515223043.png]]
###### Notazione
![[Pasted image 20260515223139.png]]
![[Pasted image 20260515223218.png]]
> Esempio
> ![[Pasted image 20260515223515.png]]


![[Pasted image 20260515223401.png]]
###### Soundness
![[Pasted image 20260516102626.png]]
###### Regole per Le Costanti
![[Pasted image 20260516102734.png]]
###### Object Creation
![[Pasted image 20260516102806.png]]
###### Not E while Loop
![[Pasted image 20260516102958.png]]
![[Pasted image 20260516103053.png]]
###### Problema Con Il Tipo Durante L'utilizzo Della Variabile
![[Pasted image 20260516103339.png]]
###### Soluzione - Type Enviroment
![[Pasted image 20260516103404.png]]
![[Pasted image 20260516103517.png]]
> questa cosa è folle! ma funzia quindi adesso dobbiamo modificare le regole precedenti
> ![[Pasted image 20260516103729.png]]
###### Function Invocation
l'introduzione del Type Enviroment permette la definizione di una nuova regola
![[Pasted image 20260516104118.png]]
e  poi anche delle function:
![[Pasted image 20260516104150.png]]
##### Tirando Le Somme
![[Pasted image 20260516104549.png]]
#### Subtyping - Problemi E Soluzioni
![[Pasted image 20260516114837.png]]
> è troppo restrittiva perchè la prima regola $e_0:T_0$ dice "$e_0$ DEVE essere dello TIPO $T_0$" e quindi non consente subtyping (ereditarietà)

Soluzione:
![[Pasted image 20260516115110.png]]
![[Pasted image 20260516115143.png]]
> la scritta $O[T_0 / x]$ rappresenta l'aggiunta al Type enviroment della dichiarazione della variabile $x$. 
##### Static Types and Dynamic Types
![[Pasted image 20260516115421.png]]
![[Pasted image 20260516115539.png]]
###### Soundness of the Typechecking System
![[Pasted image 20260516115638.png]]
###### Assign Rule of Already Declared Variable Needed
![[Pasted image 20260516120325.png]]
> questa regola serve appunto per prendere anche il caso in cui la variabile x sia già stata dichiarata e noi dobbiamo solo riassegnarla. 
> Infatti manca l'aggiunta al Type Enviroment di $x$.
###### Function Invocation with Subtyping
![[Pasted image 20260516120908.png]]
##### Class Subtyping
![[Pasted image 20260516121455.png]]
###### Field Overriding
Per overridare i field di una classe bisogna fare una distinzione: 
- Se i field sono mutabili (quindi da fuori della classe si possono fare delle assegnazioni) il field subtyping NON è più SOUND
	![[Pasted image 20260516121722.png]]
Quindi si scegli di permettere l'override dei field che però sono immutabili quindi non assegnabili una volta che l'oggetto della classe è creato, questa soluzione è SOUND, ed i field prendono il nome di **Covariant Fields**.
###### Method Overriding
![[Pasted image 20260516123334.png]]
Quindi nel metodo overridato:
- il valore di output deve rispettare la  **Covarianza**, quindi la freccia rispetta la direzione del subtyping tra le classi $B<=A$ dove $B$ è  la classe che eredita ed estende $A$.
  Quindi mettiamo caso che il tipo di ritorno del metodo nella classe $A$ sia $T$, nella classe $B$ il tipo di ritorno sarà $T'$ che è un subtype di $T$ => $T'<=T$ 
- i field di input devono rispettare la **Controvarianza**, quindi il metodo overridato avrà $e_1,...,e_n$ come input che saranno dei tipi $T'_1,...,T'_n$ che avranno la direzione inversa rispetto le classi: 
  Se i valori di input del metodo in $A$ hanno tipi $T_1,...,T_n$ essi saranno dei **sottotipi** rispetto i tipi $T'$  del metodo overridato.
  ![[Pasted image 20260516142556.png]]
## Generazione di codice
#### Memory management
![[Pasted image 20260516172741.png]]
##### Memory Layout
![[Pasted image 20260516172822.png]] 
Dove **Other Space** è dove i dati vengono immagazzinati => Other Space = Data Space.
> Quindi il compilatore è responsabile:
> 	=> della generazione del codice (Code Block)
> 	=> Organizzare l'uso dell'area dei dati (Data Space)

##### Obbiettivi della code generation
![[Pasted image 20260516173100.png]]
##### Assunzioni
![[Pasted image 20260516173157.png]]
##### Attivazioni
![[Pasted image 20260516173240.png]]
##### Lifetime delle variabili
![[Pasted image 20260516173310.png]]
##### Activation Trees
![[Pasted image 20260516173421.png]]
![[Pasted image 20260516173432.png]]
######  Importantissimo
![[Pasted image 20260516173550.png]]
##### Memory Layout Revisited con lo Stack delle attivazioni
![[Pasted image 20260516173722.png]]
##### Activation Record
![[Pasted image 20260516173901.png]]
###### Content of AR
![[Pasted image 20260516173926.png]]
![[Pasted image 20260516174015.png]]
> Esempio
> ![[Pasted image 20260516174239.png]]
> ![[Pasted image 20260516174253.png]]
> dove ogni blocchetto nello stack è una valore appartenente ad un AR di $f$ o $main$ (che non viene rappresentato dato che è poco interessante ma ci dovrebbe essere anche lui)

##### Variabili Globali
![[Pasted image 20260516174717.png]]
##### Memory Layout con anche le variabili globali
![[Pasted image 20260516174818.png]]
##### Variabili dichiarate in altri scope
![[Pasted image 20260516175508.png]]
> Viene introdotto il campo **access link** => il quale punta al valore PIù RECENTE della variabile definita in un outer scope (Per la regola Most Closely Nested)

###### Access Link, come settare il valore
![[Pasted image 20260516175951.png]]
##### Heap Storage
![[Pasted image 20260516180135.png]]
