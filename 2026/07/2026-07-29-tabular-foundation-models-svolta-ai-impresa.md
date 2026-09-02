---
title: "Tabular Foundation Models: la svolta dell'AI per le imprese"
date: 2026-07-29T14:30:15.110301
slug: tabular-foundation-models-svolta-ai-impresa
category: "Tecnologia"
topic_id: 1
---

# Tabular Foundation Models: la svolta dell'AI per le imprese

## Una nuova era per i dati strutturati

Le tabelle – CSV, fogli di calcolo o tabelle relazionali – costituiscono il cuore pulsante di quasi tutti i sistemi informativi aziendali. Storicamente, per trasformarle in previsioni utili si è dovuto ricorrere a workflow complessi: pulizia, feature‑engineering, ottimizzazione di iper‑parametri e, infine, addestramento di modelli basati su alberi (XGBoost, LightGBM, CatBoost).  Il risultato è un ciclo di sviluppo che può durare settimane per ogni nuovo dataset.

Il **Tabular Foundation Model (TFM)**, introdotto da Google Research con *TabFM* il 30 giugno 2026, propone una rottura radicale: **previsioni zero‑shot** direttamente su tabelle mai viste, senza alcun addestramento specifico né tuning manuale.

---

> "TabFM legge l’intera tabella – righe di training + righe da predire – come un unico prompt e restituisce le risposte in un solo forward pass." – Weihao Kong, Google Research

---

## Come funziona il salto di qualità

### 1. In‑context learning applicato alle tabelle

I grandi modelli linguistici (LLM) hanno dimostrato che è possibile risolvere nuovi compiti fornendo esempi contestuali, senza aggiornare i pesi. TabFM trasporta lo stesso principio al dominio tabellare: le righe etichettate fungono da *few‑shot examples*, mentre le righe da predire sono il *target*.

### 2. Architettura ibrida su misura per i dati 2‑D

Le tabelle non sono sequenze: l’ordine delle righe o delle colonne è irrilevante. Per rispettare questa proprietà TabFM combina due idee già sperimentate:

1. **Attenzione alternata riga‑colonna** – un modulo di attenzione multilayer che scorre prima sulle colonne, poi sulle righe, catturando interazioni complesse senza dover costruire manualmente feature incrociate.
2. **Compressione delle righe** – ogni riga, dopo l’attenzione, viene ridotta a un vettore denso (CLS token). Questo passaggio riduce drasticamente la lunghezza della sequenza su cui opera il transformer finale.
3. **Transformer di in‑context learning** – il modello finale elabora la sequenza di vettori compressi, apprendendo le relazioni tra colonne e generando le previsioni in un unico passo.

### 3. Pre‑training su dati sintetici

Un ostacolo storico dei modelli di fondazione per dati tabulari è la mancanza di dataset pubblici di grandi dimensioni e variegati. Google ha aggirato il problema generando **centinaia di milioni di tabelle sintetiche** mediante modelli causali strutturali, coprendo una vasta gamma di distribuzioni, tipi di variabili e schemi di correlazione. Il risultato è un modello che possiede un “bagaglio di conoscenze” generico ma potente, pronto a generalizzare su tabelle reali.

## Prestazioni sui benchmark e casi d’uso aziendali

TabFM è stato valutato su **TabArena**, un benchmark vivo che confronta algoritmi tramite punteggi Elo. Su 38 dataset di classificazione e 13 di regressione (da 700 a 150 000 righe) il modello ha superato i più raffinati ensemble di alberi, sia nella configurazione base (singolo forward pass) sia nella variante *TabFM‑Ensemble* a 32 modelli con pesi ottimizzati.

### Applicazioni concrete

| Settore | Problema tipico | Come TabFM semplifica il workflow |
|---|---|---|
| **Finanza** | Rilevazione frodi su transazioni | Si passa la tabella storica di transazioni etichettate e la nuova batch di record; il modello restituisce una probabilità di frode in pochi secondi, senza creare pipeline di feature engineering. |
| **Customer Intelligence** | Predizione churn | Basta caricare il CSV dei clienti con le loro attività recenti; TabFM restituisce il rischio di abbandono senza dover ottimizzare un XGBoost. |
| **Supply Chain** | Forecast di domanda a livello SKU | Le variabili di vendita, stagionalità e promozioni sono ingerite direttamente; la previsione avviene in tempo reale, facilitando decisioni operative. |

In tutti questi scenari il tempo di messa in produzione si riduce da **settimane a minuti**, e le competenze richieste passano da data‑science specialist a semplici analisti con familiarità di base con Python o SQL.

## Integrazione con gli ecosistemi aziendali

Google ha già predisposto l’accesso a TabFM tramite:
- **Hugging Face** (modello e checkpoint PyTorch)
- **GitHub** (codice open‑source, licenza Apache 2.0)
- **BigQuery AI.PREDICT** (in arrivo): gli utenti potranno richiamare il modello con una singola istruzione SQL, ad esempio `SELECT AI.PREDICT('tabfm', ...)`.

Questa integrazione abbassa ulteriormente la soglia d’ingresso, trasformando la predizione tabellare in un’operazione di tipo *self‑service*.

## Limiti e prospettive future

Nonostante le promesse, TabFM presenta alcune restrizioni da tenere in conto:
- **Capacità di contesto**: il modello gestisce al meglio tabelle con qualche migliaio di righe; dataset più grandi richiedono campionamento o suddivisione.
- **Spiegabilità**: le architetture transformer non offrono la stessa trasparenza dei tree‑based models, il che può essere un ostacolo in ambiti regolamentati.
- **Performance su dati estremamente rumorosi**: la robustezza a valori mancanti o categorie ultra‑rare è ancora oggetto di studio.

Il prossimo passo probabilmente vedrà l’arrivo di versioni più scalabili (es. *TabFM‑Large*) e di **ibridi con LLM** per combinare capacità testuali e numeriche, aprendo la strada a sistemi di AI multimodale capaci di analizzare simultaneamente report testuali, log di sistema e tabelle finanziarie.

## Conclusioni

I Tabular Foundation Models rappresentano una svolta concettuale per l’AI in azienda: **un unico modello pre‑addestrato che può rispondere a qualsiasi tabella** senza la tradizionale catena di pulizia, feature‑engineering e tuning. Se i risultati preliminari su benchmark indipendenti continueranno a confermarsi su dati reali, potremmo assistere a una radicale semplificazione dei processi di data‑science, con impatti diretti su velocità di innovazione, costi operativi e democratizzazione dell’analisi predittiva.

> *“Non addestrare più un modello per ogni nuovo set di dati, ma chiedere al modello di leggere il tuo CSV e dare la risposta.”* – sintesi della visione di TabFM.
