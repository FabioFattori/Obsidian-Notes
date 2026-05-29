## Identificare Quali prodotti sono i più profittevoli e/o quelli ad alta rotazione
### Max Profitto
Identificare quali prodotti nel DB sono i più profittevoli:
> sarà presente un costo d'acquisto ed un costo di vendita per ogni prodotto sui quali si fa $$Margine \ per \ Unità= Prezzo\ di \ vendita\ -\ Costo \ di \ Acquisto$$
> e poi si potrà definire un intervallo di tempo per il quale vengono prese le unità vendute con il quale si può eseguire questa formula:$$Profitto \ Totale \ = \ Margine \ per \ Unità \ * Quantità \ venduta \ in \ intervallo$$

quindi basterà eseguire una query per identificare quale prodotto permette di massimizzare il profitto calcolato.
### Alta Rotazione
> Basta calcolare l'indice di rotazione per ogni prodotto:$$Indice \ di \ Rotazione \ = \frac{Quantità \ Totale \ Venduta}{Giacenza \ Media \ in \ Magazzino}$$
> Quindi anche qui si identifica una periodo di tempo nel quale calcolare tale indice 

anche qui basta fare delle query semplici => Nessuna AI necessaria
#### Principio di Pareto
![[Pasted image 20260529152005.png]]
## Task riservate all'AI
### Previsione della domanda
Questo rappresenta un pò il task **principale**.
> Obbiettivo => Predirre la quantità di prodotti richiesti nei prossimi 7, 15 e/o 30 giorni

Fatto in python, algoritmo consigliato, da selezionare il migliore tramite magari gridsearch:
- Meta Prophet
- ARIMA/SARIMAX
### Rilevamento "Anomalie"
> Obbiettivo => Monitorare la velocità di svuotamento del magazzino in tempo reale.
> Se la pendenza della curva dei consumi subisce un'impennata improvvisa rispetto alla media storica di quel periodo, l'AI lancia un alert all'operatore.

Esempio di alert:

> [!NOTE] ATTENZIONE: Il ritmo di uscita del _Prodotto Y_ nelle ultime 48 ore è triplicato rispetto al trend normale. Le scorte si esauriranno tra 12 ore anziché tra 5 giorni. **Azione: Anticipa l'ordine al fornitore**

### \<Possibile\> Associazione Prodotti per l'Ottimizzazione del Picking
Se dei prodotti si sa anche la disposizione nel magazzino si può considerare anche la seguente applicazione per ottimizzare il carico/scarico dei prodotti.
> NOTA BENE => se questa applicazione è possibile, è possibile inoltre estend