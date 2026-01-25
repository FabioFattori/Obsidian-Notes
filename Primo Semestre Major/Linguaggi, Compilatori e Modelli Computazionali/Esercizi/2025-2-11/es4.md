---
excalidraw-plugin: parsed
tags: [excalidraw]
---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
Si considerino le seguenti formule della logica dei predicati su C={}, F={ times/2 }
e P={ =/2 }, con “=” in notazione infissa:
 x y x=times(y,y) x y x=times(times(y,y),y)
Come modelli si considerino M1, M2 ed M3 definiti come segue. M1 ha come universo A di valori
i numeri Naturali, cioè A=N (incluso lo 0); M2 ha come universo A i numeri Reali nonnegativi, cioè A={rR | r ≥ 0}; infine M3 ha come universo A tutti i numeri Reali, cioè A=R.
Inoltre in M1, M2 ed M3 il predicato “=” è l’uguaglianza tra numeri e la funzione "times" calcola
il prodotto di due numeri, cioè times(u,v) dà il numero u∙v. Per ogni formula dire se è soddisfatta
o meno, considerando ciascuno dei modelli M1, M2 ed M3. Giustificare le risposte. ^bEXwNyms

Procedimento per M1:
A = N incluso 0

∀x∃y : x = times(y,y) corrisponde a dire per ogni numero naturale esiste
un altro numero naturale y tale che x = y^2, questo non è vero per tutti i numeri
naturali, prendiamo come esempio x = 2, non esiste una y tale che y^2 = 2 nell'insieme
dei numeri naturali.
Quindi dato che la formula specifica il "per ogni" ci basta identificare una sola occorrenza
per la quale la formula non è rispettata per permetterci di dire che tale formula non è
rispettata. 

∀x∃y : x = times(times(y,y),y) corrisponde a dire che per ogni numero naturale esiste
un altro numero naturale y tale che y^3 = x, anche qui possiamo prendere come esempio 
x = 2 e vedremo che tale formula non è rispettata nella M1 

Procedimento per M2:
A = R >= 0

∀x∃y : x = times(y,y)
x = y^2 => y = √x 
dato che x 

∀x∃y : x = times(times(y,y),y)

x = y^3 quindi y = x^(1/3) e dato che x^(1/3) è definito nell'universo del modello M2
anche la seconda formula è soddisfatta.

Procedimento per M3:
 ^PKOiIBQV

%%
## Drawing
```compressed-json
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
```
%%