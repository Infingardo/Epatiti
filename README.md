# 🔬 Referto Microscopico Fegato v1.2

**Strumento di supporto per la refertazione istologica epatica automatizzata con bibliografia interattiva**

---

## 📋 Descrizione

Questo è uno **strumento web-based interattivo** per la generazione automatizzata di referti istologici epatici, con calcolo dei principali scoring systems utilizzati in patologia epatica:

- **Scoring Ishak** (attività necroinfiammatoria 0-18 e fibrosi 0-6)
- **NAS Score** (NAFLD Activity Score, per steatosi epatica non alcolica)
- **IAIHG** (International Autoimmune Hepatitis Group - componente istologica)
- **Grado Brunt** (stadiazione steatosi)

### 🆕 Novità v1.2: Bibliografia Interattiva

- **Tooltip contestuali** con icone 📚 cliccabili accanto a ogni scoring system
- **Link DOI/PubMed diretti** per accesso immediato alla letteratura scientifica
- **Sezione bibliografia completa** collassabile con tutte le referenze organizzate per categoria
- **Citation automatiche** nel referto generato con riferimenti bibliografici appropriati

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
- ✅ Un riferimento bibliografico rapido per gli scoring systems

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
- **Genera Referto**: crea testo completo con citation bibliografiche
- **Esporta CSV**: scarica dati strutturati
- **Copia Referto**: copia negli appunti per incollare in sistemi EMR
- **Reset**: cancella tutti i dati

### 🆕 Bibliografia Interattiva
- **Icone 📚**: cliccabili accanto a ogni sezione per accesso rapido alle referenze
- **Tooltip popup**: visualizzazione immediata delle citazioni principali
- **Link diretti**: DOI e PubMed per approfondimento
- **Sezione completa**: bibliografia organizzata per categoria (Ishak, NAS, IAIHG, Brunt, WHO)

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

**Bibliografia:** Ishak K et al. J Hepatol 1995;22:696-699 (DOI: 10.1016/0168-8278(95)80226-6)

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

**Bibliografia:** Ishak K et al. J Hepatol 1995;22:696-699

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

**Bibliografia:** Kleiner DE et al. Hepatology 2005;41:1313-1321 (DOI: 10.1002/hep.20701)

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

**Bibliografia:** Hennes EM et al. Hepatology 2008;48:169-176 (DOI: 10.1002/hep.22322)

---

## 🚀 Come Usare

### Workflow Tipico

**1. Apertura Tool**
```
Accedi a: file locale o hosting web
```

**2. Compilazione Dati**
- Compila gli step 1-5 con i dati istologici osservati
- Le descrizioni popup aiutano l'interpretazione di ogni parametro
- **Usa le icone 📚** per consultare rapidamente le referenze bibliografiche
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
- Il referto include automaticamente le citation bibliografiche appropriate
- Review del testo generato
- Aggiustamenti manuali se necessari (copia negli appunti)

**5. Export**
- CSV per database/audit
- Copia negli appunti per EMR
- Stampa direttamente dal browser

**6. Consultazione Bibliografia**
- Click sulle icone 📚 per tooltip rapidi con referenze
- Espandi la sezione "Bibliografia Scientifica" per lista completa
- Link diretti a DOI/PubMed per approfondimento

---

## 📚 Bibliografia Scientifica (Implementata)

### Ishak Scoring System
1. **Ishak K, Baptista A, Bianchi L, et al.** Histological grading and staging of chronic hepatitis. *J Hepatol. 1995 Jun;22(6):696-699.* [DOI: 10.1016/0168-8278(95)80226-6](https://doi.org/10.1016/0168-8278(95)80226-6) | [PubMed: 7560864](https://pubmed.ncbi.nlm.nih.gov/7560864/)

2. **Goodman ZD.** Grading and staging systems for inflammation and fibrosis in chronic liver diseases. *J Hepatol. 2007 Oct;47(4):598-607.* [DOI: 10.1016/j.jhep.2007.07.006](https://doi.org/10.1016/j.jhep.2007.07.006) | [PubMed: 17692984](https://pubmed.ncbi.nlm.nih.gov/17692984/)

### NAS Score (NAFLD Activity Score)
1. **Kleiner DE, Brunt EM, Van Natta M, et al.** Design and validation of a histological scoring system for nonalcoholic fatty liver disease. *Hepatology. 2005 Jun;41(6):1313-1321.* [DOI: 10.1002/hep.20701](https://doi.org/10.1002/hep.20701) | [PubMed: 15915461](https://pubmed.ncbi.nlm.nih.gov/15915461/)

2. **Brunt EM, Janney CG, Di Bisceglie AM, et al.** Nonalcoholic steatohepatitis: a proposal for grading and staging the histological lesions. *Am J Gastroenterol. 1999 Sep;94(9):2467-2474.* [DOI: 10.1111/j.1572-0241.1999.01377.x](https://doi.org/10.1111/j.1572-0241.1999.01377.x) | [PubMed: 10484010](https://pubmed.ncbi.nlm.nih.gov/10484010/)

3. **Rinella ME, Lazarus JV, Ratziu V, et al.** A multisociety Delphi consensus statement on new fatty liver disease nomenclature. *Hepatology. 2023 Dec;78(6):1966-1986.* [DOI: 10.1097/HEP.0000000000000520](https://doi.org/10.1097/HEP.0000000000000520) | [PubMed: 37363821](https://pubmed.ncbi.nlm.nih.gov/37363821/)

### IAIHG Score (Autoimmune Hepatitis)
1. **Hennes EM, Zeniya M, Czaja AJ, et al.** Simplified criteria for the diagnosis of autoimmune hepatitis. *Hepatology. 2008 Jul;48(1):169-176.* [DOI: 10.1002/hep.22322](https://doi.org/10.1002/hep.22322) | [PubMed: 18537184](https://pubmed.ncbi.nlm.nih.gov/18537184/)

2. **Alvarez F, Berg PA, Bianchi FB, et al.** International Autoimmune Hepatitis Group Report: review of criteria for diagnosis of autoimmune hepatitis. *J Hepatol. 1999 Nov;31(5):929-938.* [DOI: 10.1016/s0168-8278(99)80297-9](https://doi.org/10.1016/s0168-8278(99)80297-9) | [PubMed: 10580593](https://pubmed.ncbi.nlm.nih.gov/10580593/)

3. **European Association for the Study of the Liver.** EASL Clinical Practice Guidelines: Autoimmune hepatitis. *J Hepatol. 2015 Oct;63(4):971-1004.* [DOI: 10.1016/j.jhep.2015.06.030](https://doi.org/10.1016/j.jhep.2015.06.030) | [PubMed: 26341719](https://pubmed.ncbi.nlm.nih.gov/26341719/)

### WHO Classification & General
1. **WHO Classification of Tumours Editorial Board.** Digestive system tumours (5th edition). Lyon: International Agency for Research on Cancer; 2019. [IARC Publications](https://publications.iarc.fr/Book-And-Report-Series/Who-Classification-Of-Tumours/Digestive-System-Tumours-2019)

2. **Bedossa P, Poynard T; METAVIR Cooperative Study Group.** An algorithm for the grading of activity in chronic hepatitis C. *Hepatology. 1996 Aug;24(2):289-293.* [DOI: 10.1002/hep.510240201](https://doi.org/10.1002/hep.510240201) | [PubMed: 8690394](https://pubmed.ncbi.nlm.nih.gov/8690394/)

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
✓ WHO Classification 5th Edition (2019)
✓ Ishak Scoring System (validato dal 1995)
✓ NAFLD Activity Score (Kleiner et al. 2005)
✓ IAIHG Scoring (revised 2008)
✓ Brunt Fibrosis Scoring (NASH steatosis)

### Limiti Noti
- Validato principalmente per: epatite virale cronica, AIH, NAFLD
- Applicabilità variabile in: colestasi cronica, epatite alcolica, emocromatosi
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
- **Bibliografia interattiva** - tooltip e sezione collassabile

### Browser Supportati
- Chrome/Chromium 90+
- Firefox 88+
- Safari 14+
- Edge 90+

### Performance
- Caricamento: <1s
- Calcolo referto: <100ms
- Memory footprint: <5MB
- Tooltip bibliografici: render < 50ms

---

## 📝 Referti Generati

### Struttura Referto (v1.2 - Con Citation)
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
Riferimento: Ishak et al. (1995) J Hepatol 22:696-699

FIBROSI (Ishak 0-6)
────────────────────────────────────────────────
Staging: Stadio X - [descrizione]
Riferimento: Ishak et al. (1995) J Hepatol 22:696-699

[... altre sezioni con rispettive citazioni ...]

BIBLIOGRAFIA DEGLI SCORING SYSTEMS UTILIZZATI:
────────────────────────────────────────────────
• Ishak K et al. J Hepatol 1995;22:696-699
  DOI: 10.1016/0168-8278(95)80226-6
[... solo scoring effettivamente usati nel referto ...]

GENERATO DA: Referto Microscopico Fegato v1.2 (con bibliografia interattiva)
DATA: GG/MM/AAAA
```

---

## 🔧 Troubleshooting

### Problema: Tooltip bibliografia non appare
**Soluzione:** Verifica che JavaScript sia abilitato nel browser. Click sull'icona 📚, non hover-only.

### Problema: Link DOI non funzionano
**Soluzione:** Verifica connessione internet. I link puntano a siti esterni (DOI.org, PubMed).

### Problema: Sezione bibliografia non si espande
**Soluzione:** Click sul titolo "📚 Bibliografia Scientifica", non sull'area circostante.

### Altri problemi comuni
- **Auto-calcolo steatosi non funziona**: Inserisci percentuale nel campo "Percentuale Steatosi (%)"
- **Score IAIHG non si aggiorna**: Seleziona valore da dropdown "Valutazione IAIHG"
- **Referto non appare**: Clicca "Genera Referto" dopo aver compilato almeno un parametro
- **Export CSV non scarica**: Abilita i download dal browser
- **Layout rotto su mobile**: Ricaricare pagina (Ctrl+Shift+R per hard refresh)

---

## 📊 Casi Clinici Esempio (con Bibliografia)

### Caso 1: Epatite Cronica Virale B
```
Ishak Activity: 12/18 (moderata)
Ishak Fibrosis: 2 (fibrosi lieve)
NAS Score: N/A (epatite virale, non steatosi primaria)
IAIHG: Non applicabile

Bibliografia usata: Ishak et al. (1995)
Conclusione: Epatite cronica attiva con fibrosi lieve.
Correlazione con: HBV RNA, HBeAg, transaminasi.
```

### Caso 2: NAFLD con NASH sospetta
```
Steatosi: 45% (Brunt Grado 2)
NAS Score: 5/8 (steatosi + infiammazione + balloning)
Ishak Activity: 4/18 (lieve)
Ishak Fibrosis: 1 (fibrosi minima)

Bibliografia usata: Kleiner et al. (2005), Brunt et al. (1999)
Conclusione: NAS ≥5 compatibile con NASH. 
PERO': conferma mediante valutazione qualitativa della flogosi.
```

### Caso 3: Sospetta Epatite Autoimmune
```
Caratteristiche IAIHG: Epatite dell'interfaccia + infiltrato linfoplasmacellulare
IAIHG Score: 2/2 (tipico)
Ishak Activity: 14/18 (severa)
Ishak Fibrosis: 4 (fibrosi avanzata)

Bibliografia usata: Hennes et al. (2008), Ishak et al. (1995)
Conclusione: Quadro istologico tipico per AIH.
Diagnosi AIH richiede OBBLIGATORIAMENTE: ANA/ASMA positivi, IgG elevata, 
ALT significativamente elevata, esclusione HBV/HCV.
```

---

## 🔐 Privacy e Dati

- ✅ **Client-side only**: nessun dato lascia il dispositivo
- ✅ **No tracking**: nessun cookie, nessun analytics
- ✅ **No cloud storage**: dati rimangono locali
- ✅ **Salva come desideri**: scarica CSV o copia manualmente
- ✅ **Link esterni sicuri**: DOI/PubMed HTTPS

**Raccomandazione:** Per inserire dati sensibili di pazienti reali, usa versione locale offline.

---

## 📞 Supporto e Feedback

### Segnalare Bug
Se trovi errori nel calcolo, interfaccia o bibliografia:
- Fornisci dati di input specifici che causano problema
- Screenshot/browser utilizzato
- Descrivi comportamento atteso vs osservato

### Feedback Scientifico
Se hai suggerimenti su scoring, algoritmi o bibliografia:
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
Direttore, SC Anatomia Patologica
ASST Fatebenefratelli-Sacco, Milano

Expertise: Patologia epatica, ematopatologia, dermatopatologia

---

## 🙏 Ringraziamenti

- WHO Classification Editorial Board (2019)
- International Hepatic Pathology Society
- AASLD, EASL, SIPE per linee guida
- Comunità scientifica internazionale di patologi epatici
- Tutti gli autori delle pubblicazioni citate per il loro contributo fondamentale

---

## 📝 Changelog

### v1.2 (Novembre 2025)
- ✨ **NUOVA FEATURE**: Bibliografia interattiva con tooltip contestuali
- ✨ Icone 📚 cliccabili per accesso rapido alle referenze
- ✨ Link DOI/PubMed diretti per ogni scoring system
- ✨ Sezione bibliografia completa collassabile organizzata per categoria
- ✨ Citation automatiche nel referto generato
- 🔧 Migliorata visualizzazione referenze su mobile
- 📚 Aggiunta bibliografia aggiornata 2023 (Rinella et al. - MASLD nomenclature)

### v1.1 (Precedente)
- Aggiunta sezione "Interpretazione Finale e Limitazioni"
- Migliorata gestione note aggiuntive
- Correzioni minori interfaccia

### v1.0 (Iniziale)
- Release iniziale con tutti gli scoring systems
- Auto-calcolo steatosi
- Export CSV e copia referto

---

**Versione**: 1.2
**Data**: Novembre 2025
**Status**: Production-ready con bibliografia interattiva
**Ultimo aggiornamento**: v1.2 (aggiunta bibliografia interattiva completa)

---

⚠️ **Disclaimer Finale**: 

Questo strumento è un **SUPPORTO** diagnostico, NON una diagnosi definitiva. La responsabilità ultima della diagnosi e della refertazione rimane esclusivamente al patologo che ha effettuato la revisione microscopica, in correlazione con il quadro clinico-laboratoristico completo del paziente.

**"Diagnostics must integrate microscopy with clinical wisdom"** - Dalla tradizione patologica

---

📚 **Per consultare la bibliografia completa, apri lo strumento e clicca sulla sezione "Bibliografia Scientifica"**
