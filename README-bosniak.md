# 🩻 Classificazione Bosniak — Neoformazioni Cistiche Renali v1.0

**Strumento di supporto oncologico e istologico per le neoformazioni cistiche renali — HTML/JS self-contained, client-side only.**

---

## 📋 Descrizione

Tool web-based per l'inquadramento delle neoformazioni cistiche renali secondo la classificazione di Bosniak (versione 2019, Silverman et al.), con:

- calcolo automatico della categoria (I, II, IIF, III, IV) a partire dalle caratteristiche morfologiche di imaging;
- stima del rischio di malignità e del management oncologico per categoria;
- correlazione istologica attesa per ciascuna categoria;
- output separato tra dati oggettivi (criteri soddisfatti) e interpretazione proposta (editabile).

**Non sostituisce il giudizio del radiologo, dell'urologo o dell'anatomopatologo. È uno strumento di supporto.**

---

## 🎯 Funzionalità

### Dati dell'esame
Modalità (TC/RM con mdc), sede, dimensione, polo — campi descrittivi riportati nell'output.

### Pattern "cisti iperdensa"
Percorso classificativo dedicato per masse omogenee, non enhancing, a margini netti: Bosniak II se ≤3 cm e ben definita, IIF altrimenti — indipendente dalla morfologia di parete/setti.

### Criteri morfologici
- **Parete**: hairline / minimo ispessimento liscio / ispessita-irregolare-nodulare
- **Setti**: assenti / pochi (1-3) sottili / numerosi (≥4) sottili / ispessimento liscio / irregolari
- **Enhancement** di parete/setti: assente / percepito (non misurabile) / misurabile (≥10-15 HU o incremento RM significativo)
- **Calcificazioni**: assenti / sottili / spesse-nodulari
- **Componente solida enhancing indipendente** (nodulo murale ≥4mm): la sua presenza determina da sola la categoria IV

### Classificazione automatica
Motore a regole che riproduce la gerarchia dei criteri Bosniak 2019: nodulo solido → IV; enhancement misurabile → III; pattern iperdenso → II/IIF; altrimenti categoria derivata dal grado di complessità di parete/setti/calcificazioni con enhancement assente o solo percepito → I/II/IIF. Ogni calcolo espone i criteri determinanti.

### Output oncologico
Per ciascuna categoria: rischio di malignità stimato (Schoots et al. 2017) e management suggerito (follow-up per immagini, chirurgia nephron-sparing, sorveglianza attiva selettiva, discussione multidisciplinare).

### Correlazione istologica
Spettro atteso di diagnosi istologiche per categoria (cisti semplice, MEST, MCRNLMP, carcinoma papillare, carcinoma a cellule chiare variante cistica), con evidenziazione della categoria calcolata nel confronto tra tutte le categorie.

### Output separato
- **Colonna sinistra — Dati oggettivi**: categoria, criteri, rischio di malignità
- **Colonna destra — Interpretazione proposta**: prosa editabile con management e correlazione istologica, generata automaticamente

---

## 📊 Riferimento — Categorie Bosniak

| Categoria | Rischio di malignità | Management |
|-----------|----------------------|-------------|
| I | ~0% | Nessun follow-up |
| II | ~0-11% (pooled ~5%) | Nessun follow-up di routine |
| IIF | ~19% (range 5-63%) | Sorveglianza per immagini (6, 12 mesi, poi annuale fino a 5 anni) |
| III | ~50% (range 17-100%) | Chirurgia nephron-sparing / sorveglianza attiva selettiva |
| IV | ~88% (range 56-100%) | Chirurgia |

*Rischio di malignità da Schoots IG et al. J Urol 2017;198:12-21 (revisione sistematica, stime di popolazione).*

---

## 📝 Changelog

### v1.0 (Luglio 2026) — release iniziale
- Motore di classificazione Bosniak 2019 (Silverman et al.) a criteri gerarchici espliciti
- Pattern dedicato "cisti iperdensa"
- Stima del rischio di malignità e management per categoria (Schoots et al. 2017)
- Correlazione istologica per categoria con evidenziazione della categoria calcolata
- Output a due colonne (dati oggettivi / interpretazione editabile) coerente con il tool di refertazione epatica
- Glossario dei criteri (enhancement percepito/misurabile, parete/setto hairline, nodulo murale, MCRNLMP) e bibliografia

---

## ⚙️ Setup GitHub Pages

File singolo, nessuna dipendenza esterna.

```
repository/
└── bosniak.html   ← tutto qui
```

Raggiungibile da `https://<utente>.github.io/<repo>/bosniak.html` una volta pubblicato GitHub Pages.

---

## 🔐 Privacy

- Nessun dato lascia il dispositivo
- No server, no tracking, no cookie
- Tutto client-side

---

## 📚 Bibliografia essenziale

- Bosniak MA. *Radiology.* 1986;158:1-10.
- Israel GM, Bosniak MA. *Urology.* 2005;66:484-488.
- Silverman SG, Pedrosa I, Ellis JH, et al. *Radiology.* 2019;292:475-488.
- Schoots IG, Zaccai K, Hunink MG, Verhagen PCMS. *J Urol.* 2017;198:12-21.
- Moch H, Cubilla AL, Humphrey PA, Reuter VE, Ulbright TM. *Eur Urol.* 2016;70:93-105.
- Williamson SR, Halat S, Eble JN, et al. *Am J Surg Pathol.* 2012;36:1425-1433.
- Campbell SC, Uzzo RG, Allaf ME, et al. *J Urol.* 2017;198:520-529.
- Ljungberg B, Albiges L, Abu-Ghanem Y, et al. *Eur Urol.* 2022;82:399-410.

---

**Versione:** 1.0 | **Status:** Production-ready
