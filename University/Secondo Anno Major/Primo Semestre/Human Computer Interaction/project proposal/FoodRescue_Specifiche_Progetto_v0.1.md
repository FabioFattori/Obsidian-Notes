# FoodRescue — Specifiche Di Progetto

Specifiche di progetto e wireframe concettuali

Versione 0.1 • 13 ottobre 2026 • Documento di lavoro

Environmental Sustainability / Human–AI Interaction / Playful Interaction

# Ispirations && Thought Process

![alt text](505443202_18396467926115959_2074978408196801276_n.jpg) ![alt text](768679815_18464671318115959_7398180066008208696_n.jpg) ![alt text](799277799_18469818388115959_3563788787123411252_n.jpg)

# 1. Executive Summary

FoodRescue è una web app pensata inizialmente per studenti fuori sede che vogliono ridurre gli sprechi alimentari domestici. L’esperienza parte dagli alimenti già posseduti: li rende visibili, aiuta a identificarne le priorità d’uso, propone ricette antispreco e incoraggia abitudini di acquisto più consapevoli con sfide e riflessioni personali.

North star: «Usa ciò che hai, prima di comprare altro». La sostenibilità ambientale è l’unico tema verticale scelto; nutrizione/calorie, mappa dei produttori e accessibilità dei negozi sono fuori ambito.

# 2. Decisioni E Confini

| ID   | Decisione                                                                                         | Stato           |
|------|---------------------------------------------------------------------------------------------------|-----------------|
| D-01 | Tema verticale esclusivo: Environmental Sustainability                                            | Confermata      |
| D-02 | Target iniziale: studenti fuori sede; da verificare con interviste                                | Ipotesi         |
| D-03 | Smart Fridge + ricette contestuali = percorso principale                                          | Confermata      |
| D-04 | AI per assistenza e suggerimenti, sempre correggibili                                             | Confermata      |
| D-05 | Playfulness/gamification non competitiva                                                          | Da validare     |
| D-06 | Niente calorie, obiettivi nutrizionali o piani dietetici                                          | Esclusa         |
| D-07 | Niente mappa produttori, località accessibili o notifiche stagionali                              | Esclusa         |
| D-08 | React (o altro framework JS) FE e Node.js BE; nessun dettaglio implementativo in questo documento | Vincolo tecnico |

# 3. Problema, Utenti, Obiettivi

Problema ipotizzato: chi vive da solo o con coinquilini dimentica alimenti acquistati, non sa come combinarli con ciò che ha e compra prodotti duplicati. Questo è un punto di partenza per la ricerca, NON un risultato già dimostrato.

- Utenti primari ipotizzati: studenti fuori sede che acquistano e cucinano autonomamente.

- Obiettivo utente: capire rapidamente cosa consumare e trovare un’azione praticabile.

- Obiettivo di prodotto: favorire decisioni che prevengano lo spreco, senza colpevolizzare.

- Misure di usabilità: riuscita dei task, tempo, errori, chiarezza delle raccomandazioni, fiducia e controllo percepito.

# 4. Esperienza Di Riferimento (User Journey)

| Fase            | Azione utente                                | Risposta del sistema                       |
|-----------------|----------------------------------------------|--------------------------------------------|
| 1\. Inserimento | Aggiunge alimenti manualmente o da foto      | Mostra prodotti proposti da confermare     |
| 2\. Verifica    | Corregge quantità/scadenza                   | Salva solo informazioni confermate         |
| 3\. Priorità    | Consulta cibi a rischio                      | Distingue urgenza da date mancanti         |
| 4\. Scelta      | Chiede ricette con vincoli pratici           | Offre suggerimenti spiegati e modificabili |
| 5\. Esito       | Segna consumato / scartato / ancora presente | Aggiorna stato e progressi                 |
| 6\. Riflessione | Consulta sfida e andamento                   | Propone azioni realistiche e non punitive  |

# 5. Specifiche Funzionali — modulo per modulo

## 5.1 Smart Fridge

Scopo: rappresentare con poco sforzo gli alimenti realmente disponibili.

- Inserimento manuale: nome, quantità/unità, eventuale data indicata dall’utente, note facoltative.

- Inserimento fotografico assistito da AI: lista di possibili alimenti; modifica/rimozione/aggiunta prima di salvare.

- Stati degli alimenti: disponibile, usato, scartato; date mancanti evidenziate senza presumere una scadenza.

- Ordinamento per priorità d’uso; messaggi non allarmistici e senza affermazioni sulla sicurezza del cibo basate solo sulla data.

Criterio di accettazione del prototipo: un utente può aggiungere 3 prodotti, correggere un riconoscimento errato e trovare quello da usare per primo.

## 5.2 Rescue Recipes

Scopo: trasformare gli alimenti disponibili in opzioni concrete per il pasto.

- Suggerimenti orientati all’uso di ingredienti già presenti, con priorità a quelli scelti come urgenti.

- Vincoli dichiarati dall’utente: tempo a disposizione, numero di porzioni, ingredienti da evitare/preferire.

- Scheda ricetta: ingredienti posseduti, eventuali ingredienti mancanti, preparazione, motivazione del consiglio.

- Comandi espliciti: «Non mi piace», «Non ho questo ingrediente», «Proponi alternativa».

Criterio di accettazione: l’utente trova una ricetta utilizzabile, comprende il perché del suggerimento e sa correggerne una premessa.

## 5.3 Zero-Waste Challenges

Scopo: sostenere un comportamento ripetibile senza ricompensare il consumo forzato.

- Missioni personali facoltative, p.es. «Cucina usando almeno un ingrediente già disponibile».

- Feedback su azioni concrete e un piccolo orto virtuale che cresce simbolicamente.

- Nessuna classifica pubblica, penalità per alimenti scartati o promessa di impatti ambientali non verificabili.

Criterio di accettazione: completare una missione è semplice e il feedback descrive l’azione compiuta.

## 5.4 Waste Insights

Scopo: favorire una riflessione sulle abitudini, non un giudizio sulla persona.

- Riepilogo di prodotti segnati come usati/scartati, per periodo e categoria, con indicazione dei dati mancanti.

- Domanda di riflessione facoltativa su cause dello scarto: dimenticanza, porzioni, cambiamento di piani, altro.

- Suggerimenti prudenti di pianificazione degli acquisti, coerenti con lo storico disponibile.

Criterio di accettazione: l’utente capisce da dove provengono le statistiche e può correggere registrazioni errate.

# 6. AI: Regole Dell’esperienza

| Principio       | Specifiche di interazione                                                   |
|-----------------|-----------------------------------------------------------------------------|
| Controllo umano | Ogni alimento riconosciuto va confermato prima di salvarlo.                 |
| Trasparenza     | Distinguere dati forniti dall’utente, risultati AI e ipotesi.               |
| Correggibilità  | Offrire modifica immediata di prodotti e ricette suggerite.                 |
| Incertezza      | Segnalare riconoscimenti dubbi e dati mancanti; non inventare scadenze.     |
| Sicurezza       | Non qualificare un alimento come sicuro solo in base alla foto o alla data. |
| Privacy         | Minimizzare le informazioni richieste e chiarire l’uso delle foto.          |

# 7. Architettura Informativa (Concettuale)

Navigazione primaria: Home → Frigorifero → Ricette → Progressi. «Aggiungi prodotto» è un’azione principale del Frigorifero; preferenze e impostazioni restano secondarie.

Percorso essenziale: HOME (priorità) → FRIGO (verifica) → RICETTE (scelta) → ESITO (usato/scartato) → PROGRESSI (riflessione).

# 8. Wireframe Delle Schermate Principali

I seguenti mockup sono schematici, mobile-first e non definitivi. Il prodotto finale sarà una web app sviluppata con framework JS lato frontend e Node.js lato backend, senza imporre ora librerie, endpoint o modello dati.

## Wireframe 1 E 2

![Wireframe concettuale 1](image1.png)

![Wireframe concettuale 2](image2.png)

## Wireframe 3 E 4

![Wireframe concettuale 3](image3.png)

![Wireframe concettuale 4](image4.png)

*Wireframe concettuali: contenuto e visual design indicativi, da rivedere dopo il needfinding.*

# 9. Interazioni Critiche Da Verificare in Laboratorio

| Task di usability test                                     | Cosa osservare                                       |
|------------------------------------------------------------|------------------------------------------------------|
| Aggiungi 3 alimenti da una foto con un errore intenzionale | L’utente nota e corregge l’errore?                   |
| Individua l’alimento da usare per primo                    | Capisce priorità e limiti delle date?                |
| Trova una ricetta entro 20 minuti senza nuovi acquisti     | Riesce a impostare vincoli e leggere la motivazione? |
| Rifiuta una proposta AI non adatta                         | Trova facilmente una via alternativa?                |
| Segna il cibo come usato e consulta i progressi            | Comprende come cambia il riepilogo?                  |

# 10. Piano HCI Allineato Alle Slide Del Corso

| Assignment                                | Output previsto                                                |
|-------------------------------------------|----------------------------------------------------------------|
| A1 — Needfinding                          | Interviste/osservazioni; problemi e bisogni, target e priorità |
| A2 — Storyboard + low-fi                  | Scenario d’uso e prime sequenze di schermate                   |
| A3 — Heuristic evaluation                 | Valutazione individuale di prototipi secondo euristiche        |
| A4 — Medium-fidelity                      | Prototipo navigabile e revisioni sui feedback                  |
| A5 — High-fidelity + usability evaluation | Prototipo interattivo in codice e report di test               |

Nota: le slide richiedono un prototipo high-fidelity interattivo, non un prodotto completo. Funzionalità complesse e alcuni dati possono essere simulati o predefiniti.

# 11. Priorità Di Ambito

| Livello                        | Funzionalità                                                                                                  |
|--------------------------------|---------------------------------------------------------------------------------------------------------------|
| Core                           | Inserimento/gestione alimenti, priorità d’uso, ricette contestuali, modifica suggerimenti, esito del prodotto |
| Importante                     | Foto AI con conferma, 2–3 challenge, progressi di base                                                        |
| Solo se emerge dal needfinding | Orto virtuale, consigli pre-acquisto, raggruppamento alimenti tra coinquilini                                 |
| Fuori ambito                   | Calorie, nutrizione, mappe produttori, stagionalità/notifiche, accessibilità negozi, social leaderboard       |

# 12. Domande Aperte E Registro Decisionale

| ID   | Domanda da validare                                                    | Prossimo passo                               |
|------|------------------------------------------------------------------------|----------------------------------------------|
| Q-01 | Qual è la parte più fastidiosa: inserire prodotti o scegliere ricette? | Interviste + task osservato                  |
| Q-02 | Le foto riducono davvero lo sforzo rispetto al manuale?                | Prototipi alternativi                        |
| Q-03 | Le sfide motivano o infastidiscono?                                    | Intervista + test di concept                 |
| Q-04 | È utile tracciare «scartato» o provoca abbandono?                      | Test su copy e reazioni                      |
| Q-05 | Singolo utente o frigorifero condiviso?                                | Needfinding                                  |
| Q-06 | Quale dispositivo rappresenta il contesto realistico?                  | Scelta post ricerca: mobile web come ipotesi |

# 13. Registro Modifiche

| Versione | Data       | Contenuto                                                                                                               |
|----------|------------|-------------------------------------------------------------------------------------------------------------------------|
| 0.1      | 13/10/2026 | Consolidate le decisioni sulla sostenibilità; specifiche preliminari; quattro wireframe concettuali; punti da validare. |

Riferimento: «Themes and Projects Overview», Human Computer Interaction, AY 2026/27 (materiale del corso fornito dall’utente).
