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