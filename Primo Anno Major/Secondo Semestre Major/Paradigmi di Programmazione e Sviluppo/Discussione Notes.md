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

```prolog
search(X,cons(X,_)).
search(X,cons(_,Xs)) :-search(X,Xs).
```

```prolog
search2 (X , cons (X , cons (X , _))) .
search2 (X , cons (_ , Xs )) :- search2 (X , Xs ).
```

```prolog
search_two (X , cons (X , cons (_ , cons(X, _)))) .
search_two (X , cons (_ , Xs )) :- search_two (X , Xs ).
```

```prolog
search_anytwo (X , cons (X , cons (_ , cons(X, _)))) .
search_anytwo (X , cons (X , cons (X , _))) .
search_anytwo (X , cons (_ , Xs )) :- search_anytwo (X , Xs ).
```


