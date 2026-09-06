# Common Lisp — Guida Pratica

Manuale LaTeX con 148 esercizi graduali, quick reference, suggerimenti e soluzioni.

## Struttura

```
manuale/
├── main.tex              # documento radice
├── preamble.tex          # pacchetti, stili, macro
├── parts/
│   ├── 00_cheatsheet.tex # cheat sheet (1-2 pagine)
│   ├── 01_reference.tex  # quick reference dettagliata
│   ├── 02_esercizi.tex   # 148 esercizi in 10 capitoli
│   ├── 03_suggerimenti.tex # hint per esercizi ★★★+
│   └── 04_soluzioni.tex  # soluzioni commentate
└── main.pdf              # PDF compilato
```

## Compilazione

Richiede MiKTeX o TeX Live con i pacchetti standard.

```
pdflatex main   # prima passata
pdflatex main   # seconda passata (stabilizza riferimenti incrociati)
```

Due passate sono necessarie per:
- Indice dei contenuti
- Hyperlink interni (esercizi ↔ suggerimenti ↔ soluzioni)
- Numerazione pagine negli header

## Contenuto

| Sezione | Contenuto |
|---|---|
| Cheat sheet | 2 pagine, tabelle compatte, link interni |
| Quick reference | ~25 sezioni su tutti i costrutti CL |
| Esercizi cap. 1 | Fondamenti (defun, if, cond, let, loop) |
| Esercizi cap. 2 | Liste e ricorsione |
| Esercizi cap. 3 | Ricorsione avanzata |
| Esercizi cap. 4 | Higher-order e closure |
| Esercizi cap. 5 | Strutture dati (alist, hash, array, BST) |
| Esercizi cap. 6 | Macro |
| Esercizi cap. 7 | Backtracking e algoritmi |
| Esercizi cap. 8 | Stringhe e I/O |
| Esercizi cap. 9 | Parsing e interprete |
| Esercizi cap. 10 | Progetti |
| Suggerimenti | ~60 hint per esercizi ★★★+ |
| Soluzioni | 148 soluzioni (commenti proporzionali alla difficoltà) |

## Legenda

- ◆ Esercizio essenziale (bordo pieno blu) — da fare sempre
- ○ Esercizio collaterale (bordo tratteggiato grigio) — consolidamento
- ★ Facile · ★★ Medio · ★★★ Difficile · ★★★★ Avanzato · ★★★★★ Progetto

## Note tecniche

- Standard: ANSI Common Lisp
- Ambiente testato: Allegro CL Free Express Edition
- Accentati italiani nei listing usano ASCII (es. `identita'`, `gia'`)
  per compatibilità con il pacchetto `listings`
