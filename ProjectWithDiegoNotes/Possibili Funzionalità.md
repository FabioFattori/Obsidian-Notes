# Possibili Funzionalità
## Funzionalità di base
Deve essere possibile gestire dei prodotti organizzati in un magazzino e la loro vendita ed acquisto gestendo la loro quantità.
### \<Possibile\> Gestione Prodotti nel Magazzino
Potrebbe essere possibile organizzare i settori per indicare una vicinanza tra loro e la zona di carico/scarico.
Ciò porterebbe ampliare le possibilità di aggiunta delle funzionalità _vedi sotto_.

## Identificare Quali Prodotti Sono I Più Profittevoli e/o Quelli Ad Alta Rotazione
### Max Profitto
Identificare quali prodotti nel DB sono i più profittevoli:
> sarà presente un costo d'acquisto ed un costo di vendita per ogni prodotto sui quali si fa $$Margine \ per \ Unità= Prezzo\ di \ vendita\ -\ Costo \ di \ Acquisto$$
> e poi si potrà definire un intervallo di tempo per il quale vengono prese le unità vendute con il quale si può eseguire questa formula:$$Profitto \ Totale \ = \ Margine \ per \ Unità \ * Quantità \ venduta \ in \ intervallo$$

quindi basterà eseguire una query per identificare quale prodotto permette di massimizzare il profitto calcolato.
### Alta Rotazione
> Basta calcolare l'indice di rotazione per ogni prodotto:$$Indice \ di \ Rotazione \ = \frac{Quantità \ Totale \ Venduta}{Giacenza \ Media \ in \ Magazzino}$$
> Quindi anche qui si identifica una periodo di tempo nel quale calcolare tale indice 

anche qui basta fare delle query semplici => Nessuna AI necessaria
#### Principio Di Pareto
![[Pasted image 20260529152005.png]]
## Task Riservate all'AI
### Previsione Della Domanda
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

Modelli consigliati (2 approcci):

- Approccio statistico <-> più semplice per iniziare
	- ![[Pasted image 20260529171735.png]]
- Approccio per situazioni più complesse
	- ![[Pasted image 20260529171804.png]]
### \<Possibile\> Associazione Prodotti per l'Ottimizzazione Del Picking
Se dei prodotti si sa anche la disposizione nel magazzino si può considerare anche la seguente applicazione per ottimizzare il carico/scarico dei prodotti.
> NOTA BENE => se questa applicazione è possibile, è possibile inoltre estendere l'utilizzo dei prodotti più profittevoli e ad alta rotazione indicando all'operatore che è caldamente consigliato avvicinare i prodotti ad alta rotazione alla zona di carico e scarico per ottimizzare ancor di più

> Obbiettivo => Analizza la composizione degli ordini storici per scoprire quali prodotti vengono **acquistati insieme più frequentemente** (es. l'80% delle volte che un cliente ordina il _Prodotto A_, ordina anche il _Prodotto B_ nello stesso carrello).

quindi questo task ha lo scopo di migliorare la disposizione del magazzino per facilitare l'assemblamento ordini di ordini in arrivo ed in uscita.

Modelli consigliati:
- Apriori
- FP-Growth
