---
title: "Claude di Anthropic scopre vulnerabilità in AES e nel candidato post‑quantum HAWK: l’AI entra nella cripto‑analisi"
date: 2026-07-29T14:43:40.704592
slug: anthropic-claude-cryptanalysis-aes-hawk
topic_id: 10
---

# Claude di Anthropic scopre vulnerabilità in AES e nel candidato post‑quantum HAWK: l’AI entra nella cripto‑analisi

## Un’intelligenza artificiale che mette alla prova i mattoni della sicurezza digitale

Nel fine settimana del 28 luglio 2026 Anthropic ha annunciato che il suo modello di frontiera, **Claude Mythos Preview**, è riuscito a individuare due nuove debolezze in algoritmi crittografici di grande rilevanza. Una di queste riguarda **HAWK**, uno dei candidati più promettenti per la firma digitale resistente ai futuri computer quantistici; l’altra è un attacco più veloce contro una versione ridotta dell’**Advanced Encryption Standard (AES)**, il cifrario simmetrico più diffuso al mondo.

> *“Le scoperte dimostrano che l’AI può andare oltre la ricerca di bug di implementazione, arrivando a sviscerare la matematica alla base dei protocolli di cifratura.”* – Nicholas Carlini, ricercatore di Anthropic

Sebbene le vulnerabilità non colpiscano sistemi in produzione, il risultato segna un cambiamento di paradigma: da mesi a settimane, da centinaia di migliaia di dollari di lavoro umano a poche centinaia di migliaia di dollari di calcolo cloud, un modello di linguaggio è riuscito a fare ciò che anni di revisione da parte di esperti non avevano ancora scoperto.

---

## Claude Mythos Preview: come funziona

Claude Mythos è una variante di Claude, l’assistente conversazionale di Anthropic, ottimizzata per la ricerca di vulnerabilità. Il modello è stato alimentato con una serie di strumenti – compilatori matematici, paper accademici e librerie di crittografia – e lasciato operare in modalità quasi autonoma. In entrambi i casi (HAWK e AES) la macchina ha prodotto migliaia di token di ragionamento prima di arrivare a una soluzione, mentre i ricercatori umani hanno svolto il ruolo di supervisori e validatori.

- **Costo computazionale**: circa 100 000 USD per ciascuna scoperta.
- **Tempo di esecuzione**: 60 ore per l’attacco a HAWK, tre giorni per la nuova tecnica contro AES‑7‑round.
- **Intervento umano**: limitato a prompt di incoraggiamento e verifica dei risultati per diverse settimane.

---

## La falla in HAWK: una riduzione della sicurezza del 50 %

HAWK è un algoritmo di firma digitale basato su strutture a reticolo, proposto al **NIST** nella sua gara di crittografia post‑quantistica. Dopo due cicli di revisione da parte di esperti internazionali, HAWK sembrava solido.

Claude ha individuato una **simmetria matematica non sfruttata** (un’automorfismo non banale) all’interno del reticolo che consente di ridurre drasticamente il numero di operazioni necessarie per recuperare la chiave privata. In termini pratici, la difficoltà di un attacco al parametro più piccolo (HAWK‑256) è scesa da circa \(2^{64}\) operazioni a \(2^{38}\), un miglioramento di ordine 10^6.

> *“Per mantenere lo stesso livello di sicurezza bisognerebbe raddoppiare la dimensione delle chiavi, annullando gran parte dei vantaggi di efficienza che avevano reso HAWK interessante.”* – Ellen Boehm, Keyfactor

Va sottolineato che HAWK non è ancora stato adottato in produzione; la scoperta serve quindi come segnale precoce per gli standard‑setter.

---

## Un attacco più veloce contro una versione ridotta di AES

AES‑128, adottato dal NIST nel 2001, è stato sottoposto a migliaia di anni‑cum‑anno di analisi. Per valutare la robustezza dei cifrari, i ricercatori studiano spesso **varianti con meno round** (7 anziché 10) per capire dove possa trovarsi il margine di sicurezza.

Claude ha inventato una tecnica chiamata **“Möbius Bridge”**, un metodo di fingerprinting che elimina una fase di ricerca di 256 valori, riducendo così il lavoro complessivo di un fattore compreso tra 200 e 800 rispetto all’attacco più efficace conosciuto fino a quel momento.

L’attacco rimane teorico: richiederebbe più di \(2^{105}\) testi in chiaro scelti dall’avversario e costi economici dell’ordine di centinaia di milioni di dollari, ben al di fuori delle capacità di qualsiasi infrastruttura attuale.

---

## Perché queste scoperte contano

1. **Accelerazione della crittanalisi** – Il tradizionale “bottleneck” della revisione crittografica era la disponibilità di esperti. Ora il limite è il budget di calcolo, e le AI di frontiera stanno rapidamente abbassando questa soglia.
2. **Validazione precoce degli standard** – Scoprire vulnerabilità prima che un algoritmo venga standardizzato è il risultato ideale di un processo di certificazione. Claude ha dimostrato che può contribuire a questo “stress‑testing” in modo autonomo.
3. **Allarme per le autorità** – Figure come Glenn Gerstell, ex general counsel della NSA, hanno già avvertito che la sicurezza delle cifre “potrebbe non essere più garantita entro due anni”. L’intervento di Anthropic rende concreta questa preoccupazione.

> *“Dobbiamo riconsiderare la nostra fiducia nella stabilità a lungo termine degli algoritmi di cifratura, soprattutto se i modelli di AI continuano a migliorare a questo ritmo.”* – Glenn Gerstell, ex NSA

---

## Reazioni della comunità e dei decisori

- **NIST**: Anthropic ha condiviso i risultati con il NIST tramite la mailing list dedicata, chiedendo una valutazione indipendente prima della pubblicazione.
- **Accademia**: Ricercatori di ETH Zurich, Tel Aviv University e University of Haifa hanno collaborato alla creazione di **CryptanalysisBench**, un benchmark pubblico per misurare le capacità crittografiche dei modelli di AI.
- **Industria**: Ellen Boehm (Keyfactor) ha sottolineato l’importanza di una visibilità continua sulla crittografia all’interno delle imprese, soprattutto in vista della transizione verso soluzioni post‑quantistiche.

---

## Prospettive future

Anthropic ha già annunciato ulteriori ricerche su altri cifrari (LEA, Serpent, Salsa20, SHA‑1) e suggerisce che il prossimo passo sarà affrontare **algoritmi già in uso**. La questione più pressante resta la **responsabilità della divulgazione**: come reagire se un modello AI scopre una falla in un sistema critico con conseguenze immediate?

Nel frattempo, le autorità di regolamentazione stanno valutando l’adozione di linee guida più rigide per l’uso di AI in ambito di sicurezza, mentre le aziende dovranno integrare test basati su AI nei loro cicli di sviluppo e audit.

---

## Conclusioni

Claude Mythos Preview non ha rotto AES né compromesso alcun servizio attivo, ma ha dimostrato che l’IA può **superare la capacità umana nella scoperta di vulnerabilità matematiche**. Questo rappresenta sia una risorsa preziosa per la fase di progettazione e verifica degli standard crittografici, sia una sfida per chi deve garantire che le difese digitali rimangano un passo avanti rispetto a chi, ora più che mai, utilizza l’intelligenza artificiale come arma.

Il messaggio è chiaro: la sicurezza del futuro non sarà più solo una questione di algoritmi, ma anche di **chi controlla le capacità computazionali** che li analizzano.
