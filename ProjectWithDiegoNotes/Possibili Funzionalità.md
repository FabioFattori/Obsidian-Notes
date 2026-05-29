## Identificare Quali prodotti sono i più profittevoli e/o quelli ad alta rotazione
### Max Profitto
Identificare quali prodotti nel DB sono i più profittevoli:
> sarà presente un costo d'acquisto ed un costo di vendita per ogni prodotto sui quali si fa $$Margine \ per \ Unità= Prezzo\ di \ vendita\ -\ Costo \ di \ Acquisto$$
> e poi si potrà definire un intervallo di tempo per il quale vengono prese le unità vendute con il quale si può eseguire questa formula:$$Profitto \ Totale \ = \ Margine \ per \ Unità \ * Quantità \ venduta \ in \ intervallo$$

quindi basterà eseguire una query per identificare quale prodotto permette di massimizzare il profitto calcolato.
### Alta Rotazione
> Basta calcolare l'indice di rotazione per ogni prodotto:$$Indice \ di \ Rotazione \ = \frac{Quantità \ Totale \ Venduta}{Giacenza \ Media \ in \ Magazzino}$$