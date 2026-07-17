# 🔬 Referto Microscopico Fegato v1.6.4

**Strumento di supporto per la refertazione istologica epatica — HTML/JS self-contained, client-side only.**

---

## 📋 Descrizione

Tool web-based per la generazione assistita di referti istologici epatici, con calcolo degli scoring systems principali, valutazione del pattern morfologico descrittivo e output separato tra dati oggettivi e interpretazione proposta (modificabile).

**Non sostituisce il giudizio dell'anatomopatologo. È uno strumento di supporto.**

---

## 🎯 Funzionalità

### Dati del campione
- Numero frammenti, spazi portali, vene centrolobulari
- Valutazione adeguatezza automatica (Rockey 2009): ≥11 ottimale / 6-10 sufficiente / <6 subottimale

### Attività necroinfiammatoria — Ishak (0-18)
- Necrosi periportale (0-4)
- Necrosi confluente (0-6)
- Necrosi focale/litica, apoptosi (0-4)
- Infiammazione portale (0-4)

### Fibrosi — Ishak (0-6)
- Equivalente Metavir calcolato automaticamente (F0-F4)

### Steatosi — nomenclatura MASLD 2023
- Input percentuale → Grado Brunt e NAS sincronizzati
- Flag macro/microvescicolare con alert dedicato per microvescicolare
- Nomenclatura aggiornata: MASLD (ex NAFLD), MASH (ex NASH) — Rinella et al. Hepatology 2023

### NAS Score (0-8)
- Steatosi (0-3), infiammazione lobulare (0-3), balloning (0-2)
- Strumento di **ricerca**, non diagnostico per MASH
- Interpretazione differenziata per NAS ≥5 con balloning = 0 (vedi changelog)

### Epatite Autoimmune — IAIHG (componente istologica, 0-2)
- 4 caratteristiche con suggerimento automatico orientativo (Hennes 2008)
- Campo `aih-int` **indipendente** da Ishak NPP (vedi changelog)

### Pattern Morfologico Descrittivo *(nuovo in v1.5)*
16 checkbox in 4 categorie:
- **Distribuzione zonale**: zona 3, zona 1, porto-centrale, panacinar
- **Danno biliare**: duct injury, ductopenia, colestasi canalicolare/epatocitaria
- **Strutture e depositi**: granulomi, rosette fibrotiche, siderosi, depositi rame (PAS-D)
- **Alterazioni epatocitarie**: ground-glass (HBsAg), corpi acidofili, Mallory-Denk, displasia

Pattern selezionati generano suggerimenti contestuali nell'interpretazione (es. ground-glass → richiedere IHC HBsAg/HBcAg; displasia in Ishak 6 → follow-up ecografico semestrale).

### Output separato *(nuovo in v1.5)*
- **Colonna sinistra — Score calcolati**: dati numerici, staging, pattern. Oggettivo.
- **Colonna destra — Interpretazione proposta**: textarea editabile, generata automaticamente, modificabile prima dell'export.

---

## 📊 Scoring Systems

| Sistema | Range | Riferimento |
|---------|-------|-------------|
| Ishak Activity | 0-18 | Ishak et al. J Hepatol 1995;22:696-699 |
| Ishak Fibrosis | 0-6 | Ishak et al. J Hepatol 1995;22:696-699 |
| Metavir (equivalente) | F0-F4 | Bedossa & Poynard. Hepatology 1996;24:289-293 |
| Brunt (steatosi) | G0-G3 | Brunt et al. Am J Gastroenterol 1999;94:2467-2474 |
| NAS Score | 0-8 | Kleiner et al. Hepatology 2005;41:1313-1321 |
| IAIHG (istologico) | 0-2 | Hennes et al. Hepatology 2008;48:169-176 |

**Nomenclatura MASLD/MASH:** Rinella et al. Hepatology 2023;78:1966-1986

---

## 📝 Changelog

### v1.6.4 (Luglio 2026) — correzioni logiche e cross-check clinici

- **[#15 — bug IAIHG] «Compatibile» non è più scambiato per «atipico».** Secondo i criteri semplificati IAIHG (Hennes 2008), l'assenza dei soli criteri tipici (epatite d'interfaccia, rosette, emperipolesi) in un quadro di epatite cronica linfocitaria e **senza segni di un'altra diagnosi** vale «compatibile» = 1/2, non «atipico» = 0/2. «Atipico» richiede segni **positivi** di un'altra diagnosi (pattern steatosico = steatosi significativa + ballooning; pattern biliare = reazione duttulare/duttopenia/colestasi; pattern virale = ground-glass). Il suggerimento nel form ora propone «compatibile (+1)» in assenza di tali segni e «atipico (0)» quando presenti; il referto stampa l'etichetta esplicita («compatibile»/«atipico») accanto al numero e cita Hennes 2008. Una conclusione compatibile-per-sola-assenza resta comunque «epatite cronica aspecifica» (non «compatibile con AIH»): il +1 è un debole punto istologico, spiegato nella Nota, non una diagnosi di AIH.
- **[#16 — NAS] Punteggio sospeso quando la steatosi è 0%.** Il NAS (Kleiner 2005) è validato per un fegato già steatosico: con steatosi dichiarata a 0% il referto non genera più alcun blocco NAS (né totale né sotto-componenti), evitando un numero clinicamente fuorviante.
- **[#17 — cross-check] Ballooning senza steatosi → nota differenziale DILI.** Nuova regola automatica: ballooning epatocitario presente con steatosi 0% genera nella Nota la frase di alert sul differenziale con danno epatocitario tossico/farmacologico (DILI), personalizzata sul quesito clinico se dichiarato («né di AIH…»). Il ballooning resta descritto in prosa nella conclusione anche quando il NAS è soppresso.
- **[#18 — adeguatezza] Lunghezza campione come flag esterno, non clausola nel testo.** Nuovo campo facoltativo «Lunghezza complessiva del campione (mm)». Se non specificata (o sotto ~20 mm con ≥11 spazi portali) compare un avviso di lavorazione nell'interfaccia — dismissibile, mai inserito nel testo copiabile del referto. Il messaggio di adeguatezza nel referto resta basato sul numero di spazi portali.
- **[#19 — fibrosi] Conferma su colorazione dedicata come flag esterno.** Nuovo checkbox facoltativo «Fibrosi valutata su colorazione dedicata (tricromica/reticolo)». Se non spuntato, avviso di lavorazione nell'interfaccia (non nel referto).
- **[#20 — siderosi] Quantificazione Perls come flag esterno, non paragrafo nel testo.** Il referto riporta il reperto morfologico con la sede dichiarata («depositi di pigmento emosiderinico [a sede …]»), senza la richiesta di Perls nel corpo del testo; la richiesta/quantificazione Perls vive come avviso di lavorazione. Aggiunti sede (epatocitaria/sinusoidale-Kupfferiana/mista) e checkbox «Perls eseguita».

**Principio di progettazione (#18–#20):** la soglia di adeguatezza è un supporto al giudizio del patologo, non un cancello sulla diagnosi. I tre avvisi vivono solo nell'interfaccia di lavoro (pannello «Avvisi di lavorazione»), separati dal referto, visibili ma dismissibili con un clic e mai incorporati nel testo clinico copiabile.

- **[formato] Referto in prosa narrativa.** Il testo generato è ora un referto discorsivo — intestazione del campione → descrizione morfologica in prosa → *Diagnosi:* → *Grading/Staging secondo Ishak* → *Nota:* → nota differenziale — invece dei blocchi a sezione con citazioni «Rif:» inline. I punteggi di calcolo (Ishak/Brunt/NAS/IAIHG) sono invariati: cambia solo la loro presentazione. Il toggle Sintetico/Descrittivo continua a governare la sola riga di *Diagnosi:*.

### v1.6.3 (Luglio 2026) — generazione ibrida prosa + template

Estensione narrativa: il referto genera ora, **oltre** ai punteggi a template (invariati), una prosa motivata cucita insieme ai punteggi.

- **[#11 — adeguatezza] Frase motivata invece dell'etichetta isolata.** Il referto compone "Il campione comprende almeno [N] spazi portali e [M] vene centrolobulari ed è **pertanto** [adeguato / da interpretare con cautela / non adeguato] ai fini della valutazione" (soglie Rockey 2009). Il numero che giustifica il giudizio è sempre nella stessa frase.
- **[#12 — negativi in prosa] Frasi negative aggregate dai checkbox "Assente".** Convenzione italiana: un solo "Non si osservano" in apertura, virgole tra gli elementi e "né" solo davanti all'ultimo. Generate in aggiunta al punteggio, non in sostituzione.
- **[#13 — commento] Il commento nomina i criteri, non solo la categoria.** Per l'IAIHG il commento esplicita i criteri morfologici principali (epatite d'interfaccia, infiltrato linfoplasmacellulare) valutati/assenti e chiude con il rinvio clinico ("richiedono correlazione con il profilo clinico, sierologico e farmacologico") per tutte le categorie tranne il "+2".
- **[#14 — quesito clinico] Nuovo campo "Quesito clinico"** (Sospetta AIH / MASLD-MASH / Follow-up virale / Alterazione aspecifica / Altro). Modula quali negativi e commenti in prosa generare: senza selezione il comportamento resta quello attuale (solo punteggi + commento).
- **[grammatica] Concordanza "attività minima/moderata"** nella conclusione sintetica (prima "attività minimo/moderato").

### v1.6.2 (Luglio 2026) — patch issue tracker

- **[#1 — UX/generazione] Diagnosi sintetica/descrittiva mutuamente esclusive.** Aggiunto un toggle *Sintetico / Descrittivo* per la conclusione: il cambio **rigenera e sostituisce** il contenuto invece di concatenarlo. Validazione pre-copia (`hasDoubleDiagnosis`) che blocca la copia se il campo contiene entrambe le formulazioni non disambiguate.
- **[#2 — generazione] Nessun bullet muto nei pattern morfologici.** Ogni pattern che genera un bullet porta ora un dettaglio minimo (nota tecnica/istochimica o descrittore semiquantitativo); rimossa la possibilità di una riga "• siderosi" priva di contenuto.
- **[#3 — logica clinica/UX] Hint interfaccia post-selezione.** L'hint "Necrosi periportale Ishak ≥1" compare solo **dopo** che l'utente ha scelto Presente/Assente su Epatite d'interfaccia, come verifica post-hoc e non come suggerimento pre-scelta.
- **[#4 — citazioni] Deroga IAIHG tracciata.** Quando lo score usa la categoria "Compatibile (+1)", la citazione nel referto riporta "criterio esteso localmente a presentazioni acute selezionate — cfr. nota metodologica"; aggiunta la nota metodologica in bibliografia.
- **[#5 — logica clinica] "Risposta terapeutica" solo se dichiarata.** Nuovo campo *Terapia antivirale/immunosoppressiva in atto (sì/no/non noto)*: l'ipotesi "o risposta terapeutica" appare solo se impostato su "sì".
- **[#6 — logica clinica] Soglia Rockey qualificata per tipo di prelievo.** Nuovo campo *Tipo di prelievo*: se diverso da bioptico standard, il messaggio di adeguatezza (form e referto) aggiunge l'avvertenza sulla validità della soglia Rockey 2009.
- **[#7 — UI/template] Spaziatura label pattern verificata.** Confermata la corretta separazione nome/descrizione (nessuna stringa concatenata tipo "Duttopeniaperdita…" / "Ground-glass hepatocytessuggestivi").
- **[#8 — accuratezza] Note tecniche IHC/istochimiche uniformi.** Granulomi (Ziehl-Neelsen/PAS-Grocott), ground-glass (IHC HBsAg/HBcAg), depositi di rame (orceina/rhodanina), siderosi (Perls/Deugnier) riportano la nota di conferma nel referto generato, non solo nel form.
- **[#9 — logica clinica] Blocco effettivo NAS/Brunt su microvescicolare.** Con steatosi microvescicolare il box Grado Steatosi e il referto mostrano "N.A."; nessun grado Brunt/NAS numerico compare nell'output.
- **[#10 — output] Bibliografia deduplicata nel referto.** Ogni fonte (Ishak, Kleiner, Brunt/Rinella, Hennes) compare una sola volta nel testo generato anche se rilevante per più sezioni.

### v1.5.1 (Febbraio 2026) — patch metodologica
**Fix critici:**

- **[METODOLOGICO] Rimossa sincronizzazione automatica Ishak NPP → AIH**
  La versione precedente impostava automaticamente `aih-int = Presente` quando necrosi periportale Ishak ≥1. Questo introduceva un bias cognitivo silenzioso: lo stesso pattern morfologico si osserva in HCV, PBC early, danno farmaco-indotto e riacutizzazione virale. Il campo AIH è ora completamente indipendente. Al suo posto: hint visivo non vincolante con elenco esplicito delle diagnosi differenziali.

- **[CLINICO] NAS ≥5 con balloning = 0: framing separato**
  Il balloning epatocitario è la lesione discriminante per MASH (Brunt 1999). NAS ≥5 in assenza di balloning non supporta la diagnosi di steatoepatite attiva e non deve generare lo stesso framing interpretativo. Branch dedicato: "NAS elevato ma balloning assente — valutare pattern qualitativo prima di concludere per MASH."

- **[MORFOLOGICO] Displasia epatocitaria: interpretazione contestuale per stadio fibrosi**
  Tre rami distinti:
  - Ishak 6 (cirrosi): fattore di rischio HCC, follow-up ecografico semestrale
  - Ishak 4-5: monitorare progressione; peso aumenta al raggiungimento della cirrosi
  - Ishak 0-3: peso prognostico limitato — da segnalare, non da allarmare

- **[BUG] Reset ora pulisce anche l'hint NPP**

---

### v1.5 (Gennaio 2026)
- **Sezione Pattern Morfologico Descrittivo**: 16 checkbox in 4 categorie cliniche
- **Output a due colonne**: score calcolati (oggettivo) separati da interpretazione proposta (editabile)
- Suggerimenti contestuali per pattern (ground-glass → IHC, porto-centrale → Budd-Chiari, etc.)
- Campo note pattern testo libero

### v1.4 (Gennaio 2026)
- Nomenclatura MASLD/MASH (Rinella 2023) in tutto il tool
- Fix bug `iaihg-desc` mancante nel DOM
- Fix CSV export per `aih-caratteristiche`
- Alert attività/fibrosi: soglia corretta (≥13 per severo, non ≥8)
- Flag macro/microvescicolare con alert per microvescicolare
- Equivalente Metavir in tempo reale nel pannello fibrosi
- Logica AIH corretta per Hennes 2008

### v1.3 (Dicembre 2025)
- Sezione dati campione con valutazione adeguatezza
- Sezione AIH con dropdown individuali e suggerimento automatico
- Sincronizzazione bidirezionale Brunt ↔ NAS
- Tooltip bibliografici interattivi

### v1.2 (Novembre 2025)
- Bibliografia interattiva con link DOI/PubMed

### v1.1
- Interpretazione finale, gestione note

### v1.0
- Release iniziale

---

## ⚙️ Setup GitHub Pages

File singolo, nessuna dipendenza esterna.

```
repository/
└── index.html   ← tutto qui
```

Settings → Pages → Branch: main → / (root) → Save.

---

## 🔐 Privacy

- Nessun dato lascia il dispositivo
- No server, no tracking, no cookie
- Tutto client-side

---

## 📚 Bibliografia essenziale

- Ishak K et al. *J Hepatol.* 1995;22:696-699
- Bedossa P, Poynard T. *Hepatology.* 1996;24:289-293
- Brunt EM et al. *Am J Gastroenterol.* 1999;94:2467-2474
- Kleiner DE et al. *Hepatology.* 2005;41:1313-1321
- Hennes EM et al. *Hepatology.* 2008;48:169-176
- Rockey DC et al. *Hepatology.* 2009;49:1017-1044
- Rinella ME et al. *Hepatology.* 2023;78:1966-1986

---

## 👨‍⚕️ Autore

**Dr. Filippo Bianchi**
Direttore, SC Anatomia Patologica
ASST Fatebenefratelli-Sacco, Milano

---

**Versione:** 1.6.4 | **Status:** Production-ready
