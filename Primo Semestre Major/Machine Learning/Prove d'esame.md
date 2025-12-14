# Prove D'esame
## 07/12/2016
### Dare la Definizione Di Training, Validation E Test Set E Discutere Una Possibile Suddivisione Dei Dati Nei Tre Insiemi
_Per training set_ si intende una partizione del dataset atta all'addestramento interno del modello, quindi all'aggiornamento dei pesi e dei coefficenti del modello.
_Per Validation set_ si intende un sottoinsieme del dataset utilizzato per l'ottimizzazione degli iperparametri del modello, usato anche per attuare tecniche come early-stopping.
Mentre per _Test set_ si intende una partizione del dataset usata solo alla fine per stimare le prestazioni finali del modello.
Per la suddivisione si tende ad usare una distribuzione standard come segue:
-  Training set 60-70%
-  Validation set 15-20%
-  Test set 15-20%
Esempio 70%|15%|15%.
Ma può essere messa in atto quando si ha un dataset di medi/grandi dimensioni, se invece si ha a disposizione pochi dati si può decidere di non avere un validation set a favore dell'applicazione della k-fold  cross validation per ottimizzare gli iper parametri.
### Nella Formulazione dell’SVM Lineare la Funzione Obiettivo Richiede Di Massimizzare Il Margine. L’ottimizzazione È Però Vincolata; in Cosa Consistono I Vicoli? Quanti Sono?

Hard Margin
Dato un dataset dove $x_i$ è l'i-esimo dato e $y_i \in \{-1,+1\}$ si richiede che tutti i dati siano classificati correttamente e fuori dal margine, quindi:
$$y_i(w*x_i+b)-1 \geq 0\\\ per \\\ i=1...n$$
la quale richiede:
- che tutti i dati siano dal lato corretto dell'iperpiano
- la distanza dall'iperpiano sia $\geq 1$ 
Questo per ogni dato, quindi sono $n$ vincoli.

Soft Margin
Vengono introdotte delle slack variables per consentire violazioni:
$$$$