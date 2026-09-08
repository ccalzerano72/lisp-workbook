---
inclusion: always
---

# Progetto Common Lisp — Regole di lavoro

## Struttura del workspace

```
BOOK/
├── manuale/   ← Workbook (pratica)
└── teoria/    ← Testo teorico
```

I due volumi sono **strettamente correlati**: ogni modifica deve mantenere coerenza filosofica e stilistica tra i due. Non trattarli mai come progetti indipendenti.

---

## I due volumi

### Workbook — `manuale/`
*Common Lisp — Guida Pratica*

Un libro di esercizi graduali. Non spiega: fa fare.

**Struttura:**
1. Introduzione + cheat sheet + guida Allegro CL
2. Quick Reference (consultazione, non lettura)
3. 148 esercizi in 10 capitoli, difficoltà ★–★★★★★
4. Suggerimenti (60 hint per esercizi ★★★+)
5. Soluzioni commentate (dettaglio proporzionale alla difficoltà)

**Percorsi:** minimo (25 ◆ essenziali), standard (79 ◆+■), completo (148).

**Tipi esercizio:**
| Box | Simbolo | Colore | Count |
|-----|---------|--------|-------|
| `essbox` | ◆ | Blu | 25 |
| `stdbox` | ■ | Verde | 54 |
| `colbox` | ○ | Grigio | 69 |

### Testo teorico — `teoria/`
*Common Lisp — Fondamenti e Pratica*

Un percorso narrativo. Non è una reference: è il "perché" e il "come si pensa".

**Struttura (capitoli scritti / da scrivere):**
| Cap. | Titolo | Esercizi workbook |
|------|--------|-------------------|
| 1 | Il modello mentale di Lisp | es. 1–11 |
| 2 | Funzioni e dati fondamentali | es. 1–21 |
| 3 | Liste e ricorsione | es. 22–65 |
| 4 | Higher-order e closure | es. 69–88 |
| 5 | Strutture dati | es. 93–120 |
| 6 | Macro | es. 121–123 |
| 7 | Backtracking e algoritmi | **da scrivere** |
| 8 | Stringhe, I/O e parsing | **da scrivere** |
| 9 | Stile e professione | **da scrivere** |
| App. A | Lo stack delle chiamate | — |

---

## Target

Studente universitario con basi imperative (C, Java, Python). Sa cos'è una variabile, un ciclo, una funzione. Non sa cosa sono una cons-cell, una closure, una macro. **Non va trattato né da bambino né da esperto.**

---

## Filosofia comune

- **Progressione rigorosa.** Ogni concetto si appoggia solo a ciò che è già stato introdotto. Nessun "lo vedremo più avanti" senza rimando esplicito.
- **Pratica immediata.** Ogni concetto teorico è seguito da esercizi. Il lettore non aspetta mai di poter mettere le mani sul codice.
- **Collegamento bidirezionale.** Il teorico rimanda agli esercizi del workbook. Il workbook è autosufficiente ma più potente se letto dopo la teoria corrispondente.
- **Spiegare il perché.** Non "questo è il codice" ma "perché si fa così e non diversamente".
- **Confrontare con l'imperativo dove aiuta.** Il lettore conosce Java/C: la differenza va nominata esplicitamente.

---

## Sistema visivo — teoria/

| Box | Colore | Uso |
|-----|--------|-----|
| `concetto` | Blu | Costrutto o idea centrale |
| `esempio` | Verde | Codice con output commentato |
| `attenzione` | Arancio | Errori tipici, trappole |
| `intuizione` | Teal | Salti concettuali chiave |
| `confronto` | Marrone-caldo | Paragoni con altri linguaggi |
| `nota` | Grigio corsivo | Dettagli secondari |
| `workbook` | Viola | Richiami agli esercizi |

**Gerarchia interna ai box:**
- `\keyline{etichetta}{testo}` — barra arancione + label sans-serif + testo bold blu
- `\detail{...}` — grigio small per contorno/dettagli
- `\boxsep` — linea sottile per respirare

**Fuori dai box:**
- `\argomento{...}` — sotto-titoli visivi senza numero
- `\seprule` — separatori leggeri

---

## Regole tipografiche

### Da fare
- **Conciso ma completo.** Ogni parola deve guadagnarsi il posto.
- **Esempi concreti sempre.** Ogni costrutto ha almeno un esempio con output commentato, testabile nel REPL.
- **Caratteri accentati nei listing:** usare forme apostrofate (`e'`, `puo'`, `perche'`) dentro `lstlisting`; usare UTF-8 nel testo normale.
- **Listing copy-paste safe:** i file usano `columns=fullflexible, keepspaces=true` — non rimuovere queste opzioni.
- **Priorità agli essenziali** nei box workbook: indicare sempre quali esercizi fare per primi.

### Da evitare
- **Ridondanza.** Non ripetere lo stesso concetto in testo + box + esempio se uno basta.
- **Prolissità.** Se superi 5 righe di testo continuo senza break visivo, è troppo.
- **Cripticità.** Terminologia senza spiegazione, codice senza commenti inline su cosa restituisce.
- **Pesantezza grafica.** Box colorati ravvicinati senza respiro; box che si spezzano a metà pagina (usare `\Needspace`).
- **Uniformità tipografica dentro i box.** Usare `\keyline` per frasi-chiave e `\detail` per contorno.
- **Unicode problematico** (stelle ★, caratteri apice ⁿ, emoji): usare sempre le macro LaTeX equivalenti.

---

## Coerenza tra i volumi — checklist

Prima di ogni modifica significativa verificare:

1. Se si cambia un esempio nel workbook, controllare se lo stesso esempio appare nella teoria.
2. Se si aggiunge/rimuove un esercizio, aggiornare i rimandi nei capitoli della teoria.
3. Se si modifica la numerazione degli esercizi, aggiornare la tabella Cap.→Esercizi qui sopra.
4. I percorsi dichiarati in `manuale/main.tex` devono corrispondere ai conteggi reali di `essbox`/`stdbox`/`colbox`.
5. Gli output degli esempi nel workbook devono corrispondere a quelli delle soluzioni in `04_soluzioni.tex`.
