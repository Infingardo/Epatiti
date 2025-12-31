# 🔬 Referto Microscopico Fegato v1.3

**Strumento di supporto per la refertazione istologica epatica automatizzata con bibliografia interattiva**

---

## 📋 Descrizione

Questo è uno **strumento web-based interattivo** per la generazione automatizzata di referti istologici epatici, con calcolo dei principali scoring systems utilizzati in patologia epatica:

- **Scoring Ishak** (attività necroinfiammatoria 0-18 e fibrosi 0-6)
- **NAS Score** (NAFLD Activity Score)
- **IAIHG** (International Autoimmune Hepatitis Group - componente istologica)
- **Grado Brunt** (stadiazione steatosi)

### 🆕 Novità v1.3

- **Dati del campione**: numero frammenti, spazi portali, vene centrolobulari con valutazione automatica dell'adeguatezza
- **Sezione AIH rivisitata**: dropdown individuali per ogni caratteristica (4 items) con suggerimento automatico dello score
- **Sincronizzazione Brunt ↔ NAS**: i due campi sono sempre allineati
- **Interfaccia semplificata**: rimossi disclaimer ridondanti, aggiunti tooltip informativi "?" per NAS e IAIHG
- **Referto più snello**: eliminata la sezione limitazioni, mantenuti solo i dati essenziali

---

## 🎯 Funzionalità Principali

### Dati del Campione
- Numero frammenti
- Spazi portali (con valutazione adeguatezza: ≥11 ottimale, 6-10 sufficiente, <6 subottimale)
- Vene centrolobulari

### Attività Necroinfiammatoria (Ishak 0-18)
- Necrosi periportale (0-4)
- Necrosi confluente (0-6)
- Necrosi focale (litica), apoptosi e infiammazione focale (0-4)
- Infiammazione portale (0-4)

### Fibrosi (Ishak 0-6)
- Da assenza di fibrosi (0) a cirrosi definita (6)

### Steatosi
- Input percentuale (0-100%) → calcolo automatico Grado Brunt e NAS
- Sincronizzazione bidirezionale Brunt ↔ NAS Steatosi

### NAS Score (0-8)
- Steatosi (0-3) - sincronizzato con Brunt
- Infiammazione lobulare (0-3)
- Balloning epatocitario (0-2)
- Tooltip "?" con spiegazione (strumento di ricerca, non diagnostico)

### Epatite Autoimmune (IAIHG)
- 4 caratteristiche istologiche con dropdown Assente/Presente:
  - Epatite dell'interfaccia *(sincronizzata con necrosi periportale Ishak)*
  - Infiltrato linfoplasmacellulare
  - Rosette epatocitarie
  - Emperipolesi
- Suggerimento automatico score (Tipico +2 / Compatibile +1 / Atipico 0)
- Override manuale sempre possibile
- Tooltip "?" con criteri semplificati 2008

### Note Aggiuntive
- Campo libero per reperti speciali (colestasi, granulomi, ferro, etc.)

### Bibliografia Interattiva
- Icone 📚 cliccabili per accesso rapido alle referenze
- Sezione bibliografia completa collassabile
- Link DOI/PubMed diretti

---

## 📊 Scoring Systems Implementati

### Ishak Activity Score (0-18 punti)
| Componente | Range | Significato |
|-----------|-------|------------|
| Necrosi Periportale | 0-4 | Da assente a grave (tutti i portali) |
| Necrosi Confluente | 0-6 | Da assente a panacinar |
| Necrosi Focale | 0-4 | Conta foci per campo 10x |
| Infiammazione Portale | 0-4 | Da assente a grave |

**Interpretazione:**
- 0-3: Attività minima
- 4-8: Attività lieve
- 9-12: Attività moderata
- 13-18: Attività severa

**Bibliografia:** Ishak K et al. J Hepatol 1995;22:696-699

### Ishak Fibrosis Score (0-6 stadi)
| Stadio | Descrizione |
|--------|------------|
| 0 | Assenza di fibrosi |
| 1 | Espansione fibrosa portali con/senza setti brevi |
| 2 | Espansione della maggior parte dei portali |
| 3 | Espansione con occasionali setti porto-portali |
| 4 | Marcati setti a ponte (porto-portali/porto-centrali) |
| 5 | Marcata fibrosi a ponte con nodulazione (cirrosi incompleta) |
| 6 | Cirrosi definita/probabile/certa |

### NAS Score (0-8 punti)
| Componente | Punti | Criteri |
|-----------|-------|---------|
| Steatosi | 0-3 | <5%, 5-33%, 34-66%, >66% |
| Infiammazione Lobulare | 0-3 | 0 foci, <2/20x, 2-4/20x, >4/20x |
| Balloning | 0-2 | Assente, poche, molte cellule |

**Interpretazione:**
- <3: Steatosi semplice
- 3-4: Borderline
- ≥5: Compatibile con NASH

**Bibliografia:** Kleiner DE et al. Hepatology 2005;41:1313-1321

### IAIHG Score (Componente Istologica, 0-2 punti)
| Quadro | Punti | Criteri |
|--------|-------|---------|
| Tipico | +2 | Epatite interfaccia + infiltrato linfoplasmacellulare ± rosette/emperipolesi |
| Compatibile | +1 | Caratteristiche parziali |
| Atipico | 0 | Pattern non suggestivo |

**Criteri semplificati 2008:** ≥6 punti totali = probabile, ≥7 = definitiva

**Bibliografia:** Hennes EM et al. Hepatology 2008;48:169-176

---

## 📐 Logica di Sincronizzazione Steatosi

```
% Steatosi → Grado Brunt + NAS Steatosi (automatico)
Grado Brunt ↔ NAS Steatosi (sincronizzati)
```

- Se inserisci la %, Brunt e NAS si aggiornano automaticamente
- Se modifichi Brunt, NAS si allinea (e viceversa)
- La % non viene mai calcolata "al contrario" (evita valori fittizi)

## 📐 Logica di Sincronizzazione Ishak → AIH

```
Necrosi periportale (Ishak) ≥1 → Epatite dell'interfaccia (AIH) = Presente
Necrosi periportale (Ishak) = 0 → Epatite dell'interfaccia (AIH) = Assente
```

Sono lo stesso reperto valutato in modo diverso: quantitativo in Ishak, qualitativo in AIH.

---

## 🚀 Come Usare

1. **Dati campione**: inserisci frammenti, spazi portali, vene centrolobulari
2. **Compila gli scoring**: seleziona i valori dai dropdown
3. **Steatosi**: inserisci % oppure seleziona direttamente Brunt/NAS
4. **AIH**: se pertinente, compila le caratteristiche e verifica il suggerimento
5. **Note**: aggiungi reperti particolari
6. **Genera Referto**: click sul pulsante
7. **Export**: copia o scarica CSV

---

## 📚 Bibliografia Scientifica

### Ishak Scoring System
- Ishak K et al. J Hepatol 1995;22:696-699 [DOI: 10.1016/0168-8278(95)80226-6]
- Goodman ZD. J Hepatol 2007;47:598-607 [DOI: 10.1016/j.jhep.2007.07.006]

### NAS Score
- Kleiner DE et al. Hepatology 2005;41:1313-1321 [DOI: 10.1002/hep.20701]
- Brunt EM et al. Am J Gastroenterol 1999;94:2467-2474
- Rinella ME et al. Hepatology 2023;78:1966-1986 (nomenclatura MASLD)

### IAIHG Score
- Hennes EM et al. Hepatology 2008;48:169-176 [DOI: 10.1002/hep.22322]
- EASL Clinical Practice Guidelines. J Hepatol 2015;63:971-1004

### Adeguatezza campione
- Rockey DC et al. Hepatology 2009;49:1017-1044

---

## ⚙️ Configurazione Tecnica

- **HTML5 + JavaScript vanilla** (nessuna dipendenza esterna)
- **Client-side only** - nessun dato caricato su server
- **Responsive design** - funziona su desktop, tablet, mobile

---

## 🔐 Privacy

- ✅ Nessun dato lascia il dispositivo
- ✅ No tracking, no cookie
- ✅ Salvataggio locale (CSV o copia manuale)

---

## 📝 Changelog

### v1.3 (Dicembre 2025)
- ✨ Aggiunta sezione "Dati del Campione" con valutazione adeguatezza
- ✨ Sezione AIH con dropdown individuali e suggerimento automatico
- ✨ Sincronizzazione bidirezionale Brunt ↔ NAS
- ✨ Sincronizzazione necrosi periportale Ishak → epatite interfaccia AIH
- ✨ Tooltip "?" per NAS e IAIHG
- 🔧 Rimossi disclaimer ridondanti dal referto
- 🔧 Rimossa sezione "Interpretazione finale e limitazioni"
- 🔧 Corretto "Lytic" → "litica"
- 🔧 Rimosso campo "Epatite cronica" da AIH (ridondante)
- 🔧 Rimosso campo "Altro" da AIH

### v1.2 (Novembre 2025)
- Bibliografia interattiva con tooltip
- Link DOI/PubMed diretti
- Sezione bibliografia collassabile

### v1.1
- Sezione interpretazione finale
- Migliorata gestione note

### v1.0
- Release iniziale

---

## 👨‍⚕️ Autore

**Dr. Filippo**  
Direttore, SC Anatomia Patologica  
ASST Fatebenefratelli-Sacco, Milano

---

**Versione**: 1.3  
**Data**: Dicembre 2025  
**Status**: Production-ready
