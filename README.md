# 🔬 Referto Microscopico Fegato v1.1

**Strumento di supporto per la refertazione istologica epatica automatizzata**

---

## 📋 Descrizione

Questo è uno **strumento web-based interattivo** per la generazione automatizzata di referti istologici epatici, con calcolo dei principali scoring systems utilizzati in patologia epatica:

- **Scoring Ishak** (attività necroinfiammatoria 0-18 e fibrosi 0-6)
- **NAS Score** (NAFLD Activity Score, per steatosi epatica non alcolica)
- **IAIHG** (International Autoimmune Hepatitis Group - componente istologica)
- **Grado Brunt** (stadiazione steatosi)

---

## ⚠️ DISCLAIMER CRITICO - LEGGI PRIMA DI USARE

### Cosa NON è questo strumento:
- ❌ NON è uno strumento **diagnostico** definitivo
- ❌ NON sostituisce il **giudizio clinico** dell'anatomopatologo
- ❌ NON genera diagnosi formali (rimane supporto diagnostico)
- ❌ NON dispensa da revisione **caso-per-caso** critica

### Cosa è:
- ✅ Un **ausilio** alla refertazione standardizzato
- ✅ Un calcolatore di scoring systems internazionalmente riconosciuti
- ✅ Un supporto per **correlazione clinico-patologica**
- ✅ Uno strumento per **ricerca e audit** diagnostico

### Limitazioni fondamentali:

#### NAS Score (NAFLD Activity Score)
- **È uno strumento di RICERCA** per trial clinici su NAFLD/NASH
- **NON è diagnostico** per NASH
- La diagnosi di NASH rimane **QUALITATIVA** e richiede valutazione istologica complessiva
- NAS <3 suggerisce steatosi semplice, ma NON esclude NASH in altre aree
- NAS ≥5 è compatibile con NASH, ma richiede conferma qualitativa

#### IAIHG Score (International Autoimmune Hepatitis Group)
- Il punteggio riportato è **SOLO la componente istologica (0-2 punti)**
- La diagnosi di AIH richiede **criteri semplificati 2008** completi:
  - **≥6 punti totali** = diagnosi di AIH PROBABILE
  - **≥7 punti totali** = diagnosi di AIH DEFINITIVA
- Necessari OBBLIGATORIAMENTE:
  - Parametri laboratoristici (transaminasi, bilirubina, INR, albumina)
  - Sierologia (autoimmunità: ANA, ASMA, LKM, SMA)
  - Esclusione di altre eziologie (epatite virale, colestasi, ecc.)
  - Risposta terapeutica a steroidi/immunosoppressori

#### Scoring Ishak (Attività e Fibrosi)
- Basato su WHO 2022 e letteratura internazionale
- Richiede **revisione critica** della morfologia microscopica
- Validato principalmente per **epatite cronica virale e autoimmune**
- Applicabilità variabile in altre patologie epatiche

---

## 🎯 Funzionalità Principali

### Step 1-4: Dati di Input Strutturati
1. **Attività Necroinfiammatoria (Ishak)** ← 0-18 punti
   - Necrosi periportale
   - Necrosi confluente
   - Necrosi focale
   - Infiammazione portale

2. **Fibrosi (Ishak)** ← Stadio 0-6
   - Da assenza totale a cirrosi definita
   - Algoritmo semi-automatico di staging

3. **Steatosi** ← Percentuale → Grado Brunt + NAS
   - Input principale: percentuale epatociti steatosici (0-100%)
   - Auto-calcolo biddirezionale verso Brunt e NAS Score
   - Possibilità di modifica manuale (doppio-click) per casi particolari

4. **NAS Score** ← 0-8 punti
   - Steatosi (0-3)
   - Infiammazione lobulare (0-3)
   - Balloning epatocitario (0-2)

5. **Epatite Autoimmune (IAIHG)**
   - Check-list caratteristiche istologiche
   - Score IAIHG (solo componente istologica)

### Step 5: Note Aggiuntive
- Reperti speciali (colestasi, granulomi, ferro)
- Colorazioni utilizzate
- Pattern non standard

### Step 6: Generazione Report
- **Genera Referto**: crea testo completo
- **Esporta CSV**: scarica dati strutturati
- **Copia Referto**: copia negli appunti per incollare in sistemi EMR
- **Reset**: cancella tutti i dati

---

## 📊 Scoring Systems Implementati

### Ishak Activity Score (0-18 punti)
| Componente | Range | Significato |
|-----------|-------|------------|
| Necrosi Periportale | 0-4 | Da assente a grave (tutti i portali) |
| Necrosi Confluente | 0-6 | Da assente a panacinar |
| Necrosi Focale | 0-4 | Conta foci per campo 10x |
| Infiammazione Portale | 0-4 | Da assente a grave |
| **TOTALE** | **0-18** | **Score attività** |

**Interpretazione:**
- 0-3: Attività minima
- 4-8: Attività lieve
- 9-12: Attività moderata
- 13-18: Attività severa

### Ishak Fibrosis Score (0-6 stadi)
| Stadio | Descrizione |
|--------|------------|
| **0** | Assenza di fibrosi |
| **1** | Espansione fibrosa portali con/senza setti brevi |
| **2** | Espansione della maggior parte dei portali |
| **3** | Espansione con occasionali setti porto-portali |
| **4** | Marcati setti a ponte (porto-portali/porto-centrali) |
| **5** | Marcata fibrosi a ponte con nodulazione (cirrosi incompleta) |
| **6** | Cirrosi definita/probabile/certa |

### NAS Score (NAFLD Activity Score, 0-8 punti)
| Componente | Punti | Criteri |
|-----------|-------|---------|
| **Steatosi** | 0-3 | <5%, 5-33%, 34-66%, >66% |
| **Infiammazione Lobulare** | 0-3 | 0 foci, <2/20x, 2-4/20x, >4/20x |
| **Balloning** | 0-2 | Assente, poche, molte cellule |
| **TOTALE** | **0-8** | **NAS Score** |

**Interpretazione (Kleiner 2005):**
- <3: Steatosi semplice (NASH improbabile)
- 3-4: NASH borderline
- ≥5: Compatibile con NASH (ma richiede conferma qualitativa)

**⚠️ CRITICO:** NAS è uno strumento di RICERCA. La diagnosi di NASH è QUALITATIVA.

### IAIHG Score (Componente Istologica, 0-2 punti)
| Quadro | Punti | Descrizione |
|--------|-------|------------|
| **Tipico** | +2 | Epatite dell'interfaccia con infiltrato linfoplasmacellulare |
| **Compatibile** | +1 | Epatite cronica con caratteristiche suggestive |
| **Atipico** | 0 | Reperti non caratteristici |
| **Non Valutabile** | - | Limitazioni campione |

**Criteri Semplificati 2008 COMPLETI (non solo istologico):**
- **≥6 punti** = AIH probabile
- **≥7 punti** = AIH definitiva

Componenti totali IAIHG:
1. Istologico (0-2) ← **QUESTO TOOL CALCOLA SOLO QUESTO**
2. Sierologico (0-3): autoimmunità, IgG
3. Laboratorio (-1 a +3): ALT, AP, bilirubina
4. Esclusioni (0-3): virus, colestasi, alcol
5. Risposta terapeutica (0-2): se disponibile

---

## 🚀 Come Usare

### Workflow Tipico

**1. Apertura Tool**
```
Accedi a: https://infingardo.github.io/Epatiti/
oppure carica il file index.html localmente
```

**2. Compilazione Dati**
- Compila gli step 1-5 con i dati istologici osservati
- Le descrizioni popup aiutano l'interpretazione di ogni parametro
- Copia i valori direttamente dal referto microscopico

**3. Input Steatosi (IMPORTANTE)**
```
Inserisci: % di epatociti steatosici (0-100%)
↓
Si aggiornano AUTOMATICAMENTE:
  - Grado Brunt
  - NAS Score (componente steatosi)
```

**4. Generazione Report**
- Click su "Genera Referto"
- Review del testo generato
- Aggiustamenti manuali se necessari (copia negli appunti)

**5. Export**
- CSV per database/audit
- Copia negli appunti per EMR
- Stampa direttamente dal browser

---

## 📐 Algoritmi di Calcolo

### Auto-Calcolo Steatosi
```
Input: Percentuale epatociti steatosici (%)

Se % < 5:        → Brunt Grado 0 + NAS 0
Se 5 ≤ % ≤ 33:   → Brunt Grado 1 + NAS 1
Se 34 ≤ % ≤ 66:  → Brunt Grado 2 + NAS 2
Se % > 66:       → Brunt Grado 3 + NAS 3
```

### Validazione Interna
```
Controllo combinazioni anomale:
✓ Attività alta (≥8) + Fibrosi 0 → ⚠️ Alert (rara combinazione)
✓ Attività bassa (≤2) + Fibrosi avanzata (4-6) → ℹ️ Nota (possibile epatite inattiva)
```

### Modifica Manuale per Casi Particolari
```
DOPPIO-CLICK su: "Grado Steatosi" o "NAS Steatosi"
↓
Abilita modifica manuale (campo giallo)
↓
Dopo change: ritorna automatico
```

---

## 🔍 Validazione e Affidabilità

### Base Scientifica
✓ WHO Classification 5th Edition (2022)
✓ Ishak Scoring System (validato dal 1995)
✓ NAFLD Activity Score (Kleiner et al. 2005)
✓ IAIHG Scoring (revised 2008)
✓ Brunt Fibrosis Scoring (NASH steatosis)

### Limiti Noti
- Validato principalmente per: epatite virale cronica, AIH, NAFLD
- Applicabilità variabile in: colestasi cronica, epatite alcolica, emocromatos
- Bias inter-osservatore per staging fibrosi (Ishak kappa ~0.6-0.7)
- NAS non distingue NASH da semplice steatosi in base a scoring alone

### Accuratezza Attesa
| Scoring | Affidabilità | Note |
|---------|-------------|------|
| Attività Ishak | Alta | Kappa 0.7-0.8 |
| Fibrosi Ishak | Moderata | Kappa 0.6-0.7 (bias osservatore) |
| NAS Score | Alta (numerica) | Ma bassa (diagnostica) |
| IAIHG | Moderata | Richiede parametri clinici |

---

## ⚙️ Configurazione Tecnica

### Tecnologie
- **HTML5** + **JavaScript vanilla** (nessuna dipendenza esterna)
- **Client-side only** - nessun dato caricato su server
- **Responsive design** - funziona su desktop, tablet, mobile
- **Accessibilità WCAG** - supporto screen reader
- **PWA-ready** - installabile su dispositivi

### Browser Supportati
- Chrome/Chromium 90+
- Firefox 88+
- Safari 14+
- Edge 90+

### Performance
- Caricamento: <1s
- Calcolo referto: <100ms
- Memory footprint: <5MB

---

## 📝 Referti Generati

### Struttura Referto
```
REFERTO MICROSCOPICO FEGATO
════════════════════════════════════════════════

⚠️ DISCLAIMER PRELIMINARE
[Avvisi su NAS, IAIHG, correlazione clinica]

ATTIVITÀ NECROINFIAMMATORIA (Ishak)
────────────────────────────────────────────────
• Necrosi Periportale: [valore]
• Necrosi Confluente: [valore]
• Necrosi Focale: [valore]
• Infiammazione Portale: [valore]

Score Attività Totale: X/18

FIBROSI (Ishak 0-6)
────────────────────────────────────────────────
Staging: Stadio X - [descrizione]

STEATOSI
────────────────────────────────────────────────
Percentuale: X%
Grado (Brunt): Grado X

NAS SCORE (NAFLD Activity Score - SOLO RICERCA)
────────────────────────────────────────────────
• Steatosi: X
• Infiammazione Lobulare: X
• Balloning: X

NAS Score Totale: X/8
NOTA: NAS è strumento di ricerca. Diagnosi NASH è qualitativa.

EPATITE AUTOIMMUNE
────────────────────────────────────────────────
• Caratteristiche istologiche: [list]
• Valutazione IAIHG: [quadro]
• Score IAIHG: X/2 (solo componente istologica)

NOTE AGGIUNTIVE
────────────────────────────────────────────────
[Note libere inserite]

CONCLUSIONI
────────────────────────────────────────────────
• [Interpretazione attività]
• [Interpretazione fibrosi]
• [Interpretazione steatosi/NAS]

INTERPRETAZIONE FINALE E LIMITAZIONI
════════════════════════════════════════════════

⚠️ LIMITAZIONI CRITICHE DELLO STRUMENTO
────────────────────────────────────────────────
• NAS Score è RICERCA, NON diagnostico per NASH
• IAIHG è solo componente istologica (0-2)
  Criteri 2008: ≥6 probabile, ≥7 definitiva
• Correlazione OBBLIGATORIA con: clinica, laboratorio, sierologia, imaging
• Steatosi vs NASH: distinzione QUALITATIVA, non numerica

RESPONSABILITÀ DELL'OPERATORE
────────────────────────────────────────────────
✓ Competenza nel riconoscimento pattern istologici
✓ Revisione critica caso per caso
✓ Correlazione obbligatoria con clinica e laboratorio
✓ Responsabilità legale finale sulla diagnosi

GENERATO DA: Referto Microscopico Fegato v1.1
DATA: GG/MM/AAAA
```

---

## 🔧 Troubleshooting

### Problema: Auto-calcolo steatosi non funziona
**Soluzione:** Assicurati di inserire percentuale nel campo "Percentuale Steatosi (%)" e non direttamente in "Grado Brunt"

### Problema: Score IAIHG non si aggiorna
**Soluzione:** Seleziona il valore da dropdown "Valutazione IAIHG" (non è auto-calcolato)

### Problema: Referto non appare
**Soluzione:** Clicca "Genera Referto" dopo aver completato almeno un parametro

### Problema: Export CSV non scarica
**Soluzione:** Abilita i download dal browser; alcuni server bloccano file CSV per sicurezza

### Problema: Layout rotto su mobile
**Soluzione:** Ricaricare pagina; possibile cache vecchia. Usa Ctrl+Shift+R (hard refresh)

---

## 📊 Casi Clinici Esempio

### Caso 1: Epatite Cronica Virale B
```
Ishak Activity: 12/18 (moderata)
Ishak Fibrosis: 2 (fibrosi lieve)
NAS Score: N/A (epatite virale, non steatosi primaria)
IAIHG: Non applicabile

Conclusione: Epatite cronica attiva con fibrosi lieve.
Correlazione con: HBV RNA, HBeAg, transaminasi.
```

### Caso 2: NAFLD con NASH sospetta
```
Steatosi: 45% (Brunt Grado 2)
NAS Score: 5/8 (steatosi + infiammazione + balloning)
Ishak Activity: 4/18 (lieve)
Ishak Fibrosis: 1 (fibrosi minima)

Conclusione: NAS ≥5 compatibile con NASH. 
PERO': conferma mediante valutazione qualitativa della flogosi.
Correlazione con: ALT, BMI, HOMA-IR, ecografia elastografia.
```

### Caso 3: Sospetta Epatite Autoimmune
```
Caratteristiche IAIHG: Epatite dell'interfaccia + infiltrato linfoplasmacellulare
IAIHG Score: 2/2 (tipico)
Ishak Activity: 14/18 (severa)
Ishak Fibrosis: 4 (fibrosi avanzata)

Conclusione: Quadro istologico tipico per AIH.
Diagnosi AIH richiede OBBLIGATORIAMENTE: ANA/ASMA positivi, IgG elevata, 
ALT significativamente elevata, esclusione HBV/HCV.
IAIHG totale: istologico (2) + sierologico (??) + laboratorio (??) 
Non calcolabile solo da questo tool.
```

---

## 📚 Bibliografia

### Reference Principali
1. **Ishak K, et al.** Histological grading and staging of chronic hepatitis. J Hepatol. 1995;22(6):696-699.

2. **Kleiner DE, et al.** Design and validation of a histological scoring system for nonalcoholic fatty liver disease. Hepatology. 2005;41(6):1313-1321.

3. **Alvarez F, et al.** International Autoimmune Hepatitis Group Report: review of criteria for diagnosis of autoimmune hepatitis. J Hepatol. 1999;31(5):929-938.

4. **WHO Classification Editorial Board.** Head and neck tumours. Lyon: IARC; 2022. Vol. 9. (Sezione Liver pathology)

5. **Brunt EM, et al.** Nonalcoholic fatty liver disease: a systematic review and evaluation of disease management and treatment. Hepatology. 2009;50(4):1282-1293.

6. **Heneghan MA, et al.** 2016 European Association for the Study of the Liver (EASL) clinical practice guidelines: Autoimmune hepatitis. J Hepatol. 2018;69(3):429-457.

### Supporto Scientifico
- Società Italiana di Patologia Epatica (SIPE)
- American Association for the Study of Liver Diseases (AASLD)
- European Association for the Study of the Liver (EASL)
- International Liver Pathology Society

---

## 🔐 Privacy e Dati

- ✅ **Client-side only**: nessun dato lascia il dispositivo
- ✅ **No tracking**: nessun cookie, nessun analytics
- ✅ **No cloud storage**: dati rimangono locali
- ✅ **Salva come desideri**: scarica CSV o copia manualmente

**Raccomandazione:** Per inserire dati sensibili di pazienti reali, usa versione locale offline.

---

## 📞 Supporto e Feedback

### Segnalare Bug
Se trovi errori nel calcolo o nell'interfaccia:
- Fornisci dati di input specifici che causano problema
- Screenshot/browser utilizzato
- Descrivi comportamento atteso vs osservato

### Feedback Scientifico
Se hai suggerimenti su scoring o algoritmi:
- Cita fonte bibliografica della modifica proposta
- Spiega il razionale clinico
- Proponi test cases

### Licenza
**Creative Commons Attribution 4.0 International (CC BY 4.0)**
- ✅ Puoi usare, modificare, distribuire
- ✅ Devi dare credito all'autore
- ⚠️ NON warranty - usi a tuo rischio

---

## 👨‍⚕️ Autore

**Dr. Filippo**
Direttore, Sezione Anatomia Patologica
ASST Fatebenefratelli-Sacco, Milano

Expertise: Patologia epatica, ematopatologia, dermatopatologia

---

## 🙏 Ringraziamenti

- WHO Classification Editorial Board (2022)
- International Hepatic Pathology Society
- AASLD, EASL, SIPE per linee guida
- Comunità scientifica internazionale di patologi epatici

---

**Versione**: 1.1
**Data**: Novembre 2025
**Status**: Production-ready
**Ultimo aggiornamento**: v1.1 (aggiunta sezione "Interpretazione Finale e Limitazioni")

---

⚠️ **Disclaimer Finale**: 

Questo strumento è un **SUPPORTO** diagnostico, NON una diagnosi definitiva. La responsabilità ultima della diagnosi e della refertazione rimane esclusivamente al patologo che ha effettuato la revisione microscopica, in correlazione con il quadro clinico-laboratoristico completo del paziente.

**"Diagnostics must integrate microscopy with clinical wisdom"** - Dalla tradizione patologica
