# 🔬 Referto Microscopico Fegato v1.5.1

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

**Versione:** 1.5.1 | **Status:** Production-ready
