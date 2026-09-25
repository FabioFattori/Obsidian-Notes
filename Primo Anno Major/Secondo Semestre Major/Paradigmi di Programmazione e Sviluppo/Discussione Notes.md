# File Da Portare a far Vedere
## EngineFacade
Punti da sottolineare:
- Purezza funzionale data dall'assenza di uno stato globale e side/hidden effects
- Opaque type Session usato per incapsulare e non rendere disponibile un'implementazione concreta ai "client" che chiameranno l'api
- Consistenza e coerenza con il resto del progetto tramite l'utilizzo di Either 
- Utilizzo di Value Objects coerenti e significativi come return types 
## Gestione Del Rendering
Qui si parla di più file, nello specifico di:
- (Logica di conversione da model a comando) RendererManager
- (Generatore di comandi) Painter (interfaccia) con implementazione concreta PaintArchitect
- (colui che effettivamente disegna su canvas) ShapePainter 
Cosa dire di buono:
Questo flusso applica il pattern functional core / imperative shell al rendering: la generazione del piano di disegno è pura, completamente testabile, mentre l'unico punto di mutazione (l'interprete ScalaFX) è isolato e sostituibile senza toccare la logica di dominio.
Da sottolineare come i colori siano estratti in maniera deterministica partendo dal TeamId della entity.
**Alla domanda: poteva essere fatto meglio? / cosa miglioreresti?**
Rispondo con due miglioramenti alla soluzione attuale:
1. i nomi portano il flusso (principalmente la parte di dominio) ad essere ambigua, potevano essere scelti dei nomi migliori
2. è possibile un refactoring nella classe PaintArchitect creando una funzione privata che si occupi di fare il match sulla shape del locatable passato, ed in base ad essa eseguire due callback passate alla funzione stessa per eliminare la "duplicazione" strutturale presente nei due metodi `drawCircle` e `drawRectangle`.
## Unit Ed Integration Tests Di SaveTeamFormDialog
Gli unit evidenziano come ho/abbiamo sfruttato gli `scoped access modifier` di scala per testare delle funzioni private dei form (ma anche di altri object) per realizzare gli unit in AAA.
Mentre gli integration evidenziano il nostro approccio filosofico al testing della grafica, ovvero come per noi tutto ciò che deve interagire con il thread scalaFX (come mostrare un dialog) è integration dato che ha delle dipendenze esterne.
Inoltre negli integration sono presenti anche gli snapshot test visuali e architetturali del dialog.
# Prolog
## General Concepts
![[Pasted image 20260916231808.png]]
![[Pasted image 20260916231932.png]]
### Abstract Syntax
![[Pasted image 20260916232028.png]]
![[Pasted image 20260916232240.png]]
### Real Syntax
![[Pasted image 20260916232953.png]]
![[Pasted image 20260917145508.png]]
### Es Solutions
![[Pasted image 20260917205559.png]]
```prolog
search(X,cons(X,_)).
search(X,cons(_,Xs)) :-search(X,Xs).
```
![[Pasted image 20260917205634.png]]
```prolog
search2 (X , cons (X , cons (X , _))) .
search2 (X , cons (_ , Xs )) :- search2 (X , Xs ).
```
![[Pasted image 20260917205648.png]]
```prolog
search_two (X , cons (X , cons (_ , cons(X, _)))) .
search_two (X , cons (_ , Xs )) :- search_two (X , Xs ).
```
![[Pasted image 20260917205701.png]]
```prolog
search_anytwo (X , cons (X , cons (_ , cons(X, _)))) .
search_anytwo (X , cons (X , cons (X , _))) .
search_anytwo (X , cons (_ , Xs )) :- search_anytwo (X , Xs ).
```
![[Pasted image 20260917221702.png]]
```prolog
size(nil, zero).
size(cons(_, T), s(Size)) :- size(T, Size).
```
![[Pasted image 20260922155407.png]]
```prolog
add(zero, Y, Y).
add(s(X), Y, s(Z)) :- add(X, Y, Z).

sum_list(nil, zero).
sum_list(cons(H,T), Sum) :-
	sum_list(T, SumT),
	add(H, SumT, Sum).
```
![[Pasted image 20260922161219.png]]
![[Pasted image 20260922161239.png]]
```prolog
max(List, Max) :- max(List, 0, Max).

max(nil, Max, Max).

max(cons(H, T), TempMax, Max) :- 
	H > TempMax,
	max(T, H, Max).
max(cons(H, T), TempMax, Max) :- 
	H =< TempMax,
	max(T, TempMax, Max).
```
![[Pasted image 20260922172227.png]]
```prolog
min_max(cons(H,L), Min, Max) :- min_max(cons(H,L), H, H, Min, Max).

min_max(nil, Min, Max, Min, Max).

min_max(cons(H, T), TempMin, TempMax, Min, Max) :- 
	H > TempMax,
	min_max(T, TempMin, H, Min, Max).
min_max(cons(H, T), TempMin, TempMax, Min, Max) :- 
	H < TempMin,
	min_max(T, H, TempMax, Min, Max).
min_max(cons(H, T), TempMin, TempMax, Min, Max) :- 
	H =< TempMax,
	H >= TempMin,
	min_max(T, TempMin, TempMax, Min, Max).
```
![[Pasted image 20260922172544.png]]
```prolog
same(nil, nil).

same(cons(X,T1), cons(X, T2)) :- same(T1, T2).
```
![[Pasted image 20260922173238.png]]
```prolog
all_bigger(nil, nil).

all_bigger(cons(H1, T1), cons(H2, T2)) :- 
	H1 > H2,
	all_bigger(T1, T2).
```
![[Pasted image 20260923191445.png]]
```prolog
search(X, cons(X,_)).
search(X, cons(_, Xs)) :- search(X, Xs).

sublist(nil, _).
sublist(cons(H1, T1), List2) :- 
	search(H1, List2),
	sublist(T1, List2).
```
![[Pasted image 20260923191718.png]]
![[Pasted image 20260923193332.png]]
```prolog
seqR (zero, nil).
seqR (s(X), cons(X,T)) :-  seqR(X, T).
```
![[Pasted image 20260925111422.png]]
```prolog
last(nil,X, cons(X, nil)).
last(cons(H1, T1),X, cons(H1, T2)) :- last(T1, X, T2).

seqR2(zero, nil).
seqR2(s(X), List) :- 
    seqR2(X, T),
    last(T, X, List).
```