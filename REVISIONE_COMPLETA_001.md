# Revisione Completa: Common Lisp — Fondamenti e Workbook

**Data revisione:** Settembre 2026  
**Revisore:** Kiro AI  
**Scope:** Analisi completa di entrambi i volumi, verifica contenuti, coerenza, riferimenti incrociati

---

## Sommario Esecutivo

I due volumi rappresentano un progetto didattico **di alta qualità** per l'insegnamento del Common Lisp a studenti universitari con background imperativo. La struttura è solida, la progressione pedagogica coerente, e il materiale copre in modo esaustivo i concetti fondamentali fino ad argomenti avanzati.

**Punti di forza principali:**

- Filosofia pedagogica chiara e consistente ("funzionale prima, tutto il resto dopo")
- Eccellente sistema di percorsi differenziati (minimo/standard/completo)
- Qualità tecnica del codice LaTeX e degli esempi Lisp
- Collegamento bidirezionale efficace tra teoria e pratica

**Aree di miglioramento:**

- Alcune ridondanze tra i due volumi
- Pochi esercizi con suggerimenti mancanti nella fascia ★★★
- Minor inconsistenze tipografiche isolate

---

## Parte I: Valutazione del Testo Teorico (Fondamenti)

### Capitolo 1: Il modello mentale di Lisp

| Criterio      | Voto | Note                                                           |
| ------------- | ---- | -------------------------------------------------------------- |
| Idea          | 9/10 | Approccio originale: partire dal "perché" prima del "come"     |
| Struttura     | 9/10 | Progressione logica eccellente                                 |
| Realizzazione | 8/10 | Alcuni passaggi potrebbero essere più concisi                  |
| Chiarezza     | 9/10 | Linguaggio accessibile, analogie efficaci                      |
| Precisione    | 9/10 | Tecnicamente accurato                                          |
| Esaustività   | 8/10 | Copre i fondamenti, rimanda correttamente agli approfondimenti |

**Punti di forza:**

- L'analogia REPL/calcolatrice è molto efficace
- La spiegazione delle S-expression come "alberi con parentesi" è illuminante
- Il confronto con linguaggi imperativi è ben calibrato

**Suggerimenti:**

- Il box "intuizione" sulla valutazione potrebbe includere un diagramma visivo
- La sezione sui simboli potrebbe anticipare brevemente il namespace separato per funzioni

---

### Capitolo 2: Funzioni e dati fondamentali

| Criterio      | Voto | Note                                 |
| ------------- | ---- | ------------------------------------ |
| Idea          | 9/10 | Consolidamento naturale dopo cap. 1  |
| Struttura     | 9/10 | Organizzazione chiara per argomento  |
| Realizzazione | 9/10 | Esempi ben scelti e progressivi      |
| Chiarezza     | 9/10 | Spiegazioni limpide                  |
| Precisione    | 9/10 | Corretto e completo                  |
| Esaustività   | 9/10 | Copertura appropriata per il livello |

**Punti di forza:**

- La distinzione `defun`/`defparameter`/`defvar` è spiegata con precisione
- Gli esempi di `let`/`let*` chiariscono bene la differenza
- Il trattamento di `cond` vs `if` è pedagogicamente valido

**Suggerimenti:**

- Aggiungere un esempio di `multiple-value-bind` anticipato (anche solo come "preview")
- Il box sui numeri razionali potrebbe menzionare le implicazioni per la precisione

---

### Capitolo 3: Liste e ricorsione

| Criterio      | Voto  | Note                                             |
| ------------- | ----- | ------------------------------------------------ |
| Idea          | 10/10 | Cuore del libro, ben concepito                   |
| Struttura     | 9/10  | Progressione da cons-cell a ricorsione complessa |
| Realizzazione | 9/10  | Esempi canonici ben presentati                   |
| Chiarezza     | 9/10  | Diagrammi delle cons-cell molto utili            |
| Precisione    | 10/10 | Tecnicamente impeccabile                         |
| Esaustività   | 9/10  | Copre tutti i pattern fondamentali               |

**Punti di forza:**

- I diagrammi box-and-pointer sono eccellenti
- La progressione "ricorsione semplice → con accumulatore → tail-recursive" è perfetta
- Il pattern "caso base + caso ricorsivo" è martellato nel modo giusto

**Suggerimenti:**

- Aggiungere un box "attenzione" sullo stack overflow per ricorsione non-tail
- Considerare un esempio di debugging con `trace`

---

### Capitolo 4: Higher-order e closure

| Criterio      | Voto  | Note                                             |
| ------------- | ----- | ------------------------------------------------ |
| Idea          | 10/10 | Passaggio cruciale, ben motivato                 |
| Struttura     | 9/10  | Da `mapcar` a closure con stato                  |
| Realizzazione | 9/10  | Esempi progressivi e illuminanti                 |
| Chiarezza     | 9/10  | Il concetto di closure è spiegato magistralmente |
| Precisione    | 10/10 | Corretto in ogni dettaglio                       |
| Esaustività   | 9/10  | Manca solo curry/partial (presente nel workbook) |

**Punti di forza:**

- L'esempio del contatore che "ricorda" è perfetto
- La distinzione `#'`, `funcall`, `apply` è cristallina
- Il confronto con i callback di JavaScript aiuta il target

**Suggerimenti:**

- Aggiungere un box su `labels` vs `flet` (solo `labels` permette ricorsione)
- Un esempio di "closure accidentale" (cattura di variabile non voluta) sarebbe utile

---

### Capitolo 5: Strutture dati

| Criterio      | Voto | Note                                                |
| ------------- | ---- | --------------------------------------------------- |
| Idea          | 9/10 | Transizione necessaria al pratico                   |
| Struttura     | 9/10 | Progressione alist → hash → array → struct → alberi |
| Realizzazione | 9/10 | Esempi concreti e utili                             |
| Chiarezza     | 8/10 | Alcune sezioni dense                                |
| Precisione    | 9/10 | Accurato                                            |
| Esaustività   | 9/10 | Copertura completa per il livello                   |

**Punti di forza:**

- Il confronto alist vs hash table con analisi di complessità è eccellente
- L'introduzione di `defstruct` è graduale e motivata
- Gli alberi binari preparano bene al backtracking

**Suggerimenti:**

- La sezione sui grafi potrebbe beneficiare di un diagramma
- Menzionare `with-hash-table-iterator` per completezza

---

### Capitolo 6: Macro

| Criterio      | Voto  | Note                                            |
| ------------- | ----- | ----------------------------------------------- |
| Idea          | 10/10 | Argomento distintivo di Lisp, ben motivato      |
| Struttura     | 9/10  | Da semplice a `gensym`                          |
| Realizzazione | 9/10  | Esempi canonici ben scelti                      |
| Chiarezza     | 8/10  | Argomento intrinsecamente complesso             |
| Precisione    | 10/10 | Tecnicamente impeccabile                        |
| Esaustività   | 8/10  | Copre l'essenziale, rimanda per approfondimenti |

**Punti di forza:**

- L'enfasi su `macroexpand-1` come strumento di debug è fondamentale
- Il problema della cattura di variabile è spiegato con un esempio concreto
- La regola "se una funzione basta, usa quella" è saggia

**Suggerimenti:**

- Aggiungere un esempio di macro che genera codice condizionalmente
- Un box sulle macro "anaphoric" (anche solo come menzione)

---

### Capitolo 7: Backtracking e algoritmi

| Criterio      | Voto | Note                                           |
| ------------- | ---- | ---------------------------------------------- |
| Idea          | 9/10 | Applicazione pratica dei concetti precedenti   |
| Struttura     | 9/10 | Progressione da subsets a N-queens             |
| Realizzazione | 9/10 | Algoritmi classici ben presentati              |
| Chiarezza     | 9/10 | Spiegazioni passo-passo efficaci               |
| Precisione    | 9/10 | Corretto                                       |
| Esaustività   | 8/10 | Manca dynamic programming (forse intenzionale) |

**Punti di forza:**

- Il pattern "genera e prova" è ben astratto
- L'euristica di Warnsdorff per il cavallo è un tocco di classe
- I box di ragionamento per le soluzioni sono molto utili

**Suggerimenti:**

- Aggiungere un accenno alla memoization come ponte verso DP
- Un esercizio su constraint propagation sarebbe interessante

---

### Capitolo 8: Stringhe e I/O

| Criterio      | Voto | Note                        |
| ------------- | ---- | --------------------------- |
| Idea          | 8/10 | Necessario ma meno centrale |
| Struttura     | 8/10 | Organizzazione funzionale   |
| Realizzazione | 8/10 | Esempi pratici              |
| Chiarezza     | 9/10 | Diretto e comprensibile     |
| Precisione    | 9/10 | Corretto                    |
| Esaustività   | 7/10 | Copertura essenziale        |

**Punti di forza:**

- L'esempio del palindromo robusto è didatticamente valido
- La calcolatrice RPN è un classico ben presentato

**Suggerimenti:**

- Espandere la sezione su `format` (è molto potente)
- Aggiungere esempi di parsing con `read-from-string`
- Un box su `with-input-from-string` e `with-output-to-string`

---

### Capitolo 9: Stile e professione

| Criterio      | Voto | Note                          |
| ------------- | ---- | ----------------------------- |
| Idea          | 9/10 | Chiusura appropriata          |
| Struttura     | 8/10 | Miscellanea utile             |
| Realizzazione | 8/10 | Consigli pratici              |
| Chiarezza     | 9/10 | Diretto                       |
| Precisione    | 9/10 | Basato su best practice reali |
| Esaustività   | 7/10 | Potrebbe essere espanso       |

**Punti di forza:**

- Le convenzioni di naming sono spiegate con motivazione
- Il consiglio su docstring è importante
- I link a risorse esterne sono utili

**Suggerimenti:**

- Aggiungere una sezione su testing (anche informale)
- Menzionare strumenti come SLIME/SLY per lo sviluppo
- Un box su come leggere la documentazione HyperSpec

---

### Appendice A: Lo stack delle chiamate

| Criterio      | Voto  | Note                                              |
| ------------- | ----- | ------------------------------------------------- |
| Idea          | 10/10 | Fondamentale per capire la ricorsione             |
| Struttura     | 9/10  | Progressione chiara                               |
| Realizzazione | 9/10  | Diagrammi efficaci                                |
| Chiarezza     | 9/10  | Accessibile anche a chi non ha fatto architettura |
| Precisione    | 10/10 | Tecnicamente corretto                             |
| Esaustività   | 9/10  | Copre ciò che serve                               |

**Punti di forza:**

- I diagrammi dello stack sono esemplari
- Il collegamento con tail-call optimization è chiaro
- Utile riferimento per gli esercizi di ricorsione

---

### Appendice B: ADT (Abstract Data Types)

| Criterio      | Voto | Note                              |
| ------------- | ---- | --------------------------------- |
| Idea          | 8/10 | Complemento utile                 |
| Struttura     | 8/10 | Organizzata per struttura dati    |
| Realizzazione | 8/10 | Implementazioni pulite            |
| Chiarezza     | 8/10 | Assume familiarità con i concetti |
| Precisione    | 9/10 | Corretto                          |
| Esaustività   | 8/10 | Copre stack, queue, BST           |

---

## Parte II: Valutazione del Workbook

### Struttura generale

| Criterio      | Voto  | Note                              |
| ------------- | ----- | --------------------------------- |
| Idea          | 10/10 | Sistema di percorsi brillante     |
| Struttura     | 9/10  | Progressione graduata efficace    |
| Realizzazione | 9/10  | 148 esercizi ben calibrati        |
| Chiarezza     | 9/10  | Testi degli esercizi chiari       |
| Precisione    | 9/10  | Output attesi corretti            |
| Esaustività   | 9/10  | Copertura completa del curriculum |

**Distribuzione difficoltà:**

- ★: 28 esercizi (introduttivi)
- ★★: 45 esercizi (consolidamento)
- ★★★: 42 esercizi (applicazione)
- ★★★★: 26 esercizi (avanzati)
- ★★★★★: 7 esercizi (sfida)

**Percorsi:**

- Minimo (25 ◆): Ben selezionati, coprono i concetti essenziali
- Standard (79 ◆+■): Equilibrio ottimale teoria/pratica
- Completo (148): Per chi vuole padronanza

---

### Sezione Esercizi per Capitolo

#### Cap. 1-2: Fondamenti (es. 1-21)

| Aspetto      | Voto | Note                               |
| ------------ | ---- | ---------------------------------- |
| Progressione | 9/10 | Da somma a equazioni quadratiche   |
| Varietà      | 9/10 | Aritmetica, condizioni, cicli base |
| Difficoltà   | 9/10 | Calibrata per principianti         |

#### Cap. 3: Liste (es. 22-65)

| Aspetto      | Voto  | Note                              |
| ------------ | ----- | --------------------------------- |
| Progressione | 10/10 | Da car/cdr a ricorsione su alberi |
| Varietà      | 10/10 | Tutti i pattern canonici          |
| Difficoltà   | 9/10  | Graduata con precisione           |

**Esercizi particolarmente efficaci:**

- Es. 39 (reverse con accumulatore): Perfetto per capire tail-recursion
- Es. 49 (RLE): Sfida appropriata, hint utile
- Es. 55 (flatten): Passaggio chiave alla ricorsione su alberi

#### Cap. 4: Higher-order (es. 69-92)

| Aspetto      | Voto | Note                                     |
| ------------ | ---- | ---------------------------------------- |
| Progressione | 9/10 | Da mapcar a memoization                  |
| Varietà      | 9/10 | Copre tutti i costrutti standard         |
| Difficoltà   | 9/10 | Es. 91 (memoize) è sfidante ma fattibile |

#### Cap. 5: Strutture dati (es. 93-120)

| Aspetto      | Voto  | Note                                           |
| ------------ | ----- | ---------------------------------------------- |
| Progressione | 9/10  | Alist → hash → array → struct → alberi → grafi |
| Varietà      | 10/10 | Eccellente copertura                           |
| Difficoltà   | 9/10  | BST e grafi adeguatamente sfidanti             |

#### Cap. 6: Macro (es. 121-123)

| Aspetto      | Voto | Note                                  |
| ------------ | ---- | ------------------------------------- |
| Progressione | 8/10 | Solo 3 esercizi, ma ben scelti        |
| Varietà      | 8/10 | quando, while, for                    |
| Difficoltà   | 9/10 | gensym in es. 123 è il punto cruciale |

**Suggerimento:** Aggiungere 2-3 esercizi di macro (es. `unless`, `dolist*`, `with-gensyms`)

#### Cap. 7: Backtracking (es. 124-136)

| Aspetto      | Voto  | Note                        |
| ------------ | ----- | --------------------------- |
| Progressione | 9/10  | Da subsets a Sudoku         |
| Varietà      | 10/10 | Classici dell'informatica   |
| Difficoltà   | 9/10  | Es. 134-136 sono vere sfide |

#### Cap. 8: Stringhe e I/O (es. 137-144)

| Aspetto      | Voto | Note                               |
| ------------ | ---- | ---------------------------------- |
| Progressione | 8/10 | Più breve degli altri              |
| Varietà      | 8/10 | Palindromi, anagrammi, parsing     |
| Difficoltà   | 9/10 | Es. 144 (mini-interprete) è ottimo |

#### Cap. 9: Progetti (es. 145-148)

| Aspetto      | Voto | Note                                                   |
| ------------ | ---- | ------------------------------------------------------ |
| Progressione | 9/10 | Da semplice (indovina numero) a complesso (gestionale) |
| Varietà      | 9/10 | Giochi, simulazioni, CRUD                              |
| Difficoltà   | 9/10 | Es. 148 è un progetto vero                             |

---

### Sezione Suggerimenti

| Criterio  | Voto | Note                    |
| --------- | ---- | ----------------------- |
| Copertura | 8/10 | ~60 hint per es. ★★★+   |
| Qualità   | 9/10 | Guidano senza rivelare  |
| Utilità   | 9/10 | Sbloccano efficacemente |

**Osservazioni:**

- Tutti gli esercizi ★★★★ e ★★★★★ hanno suggerimenti ✓
- Alcuni ★★★ mancano di hint (es. 56, 60 hanno hint; altri no)

**Suggerimento:** Verificare che TUTTI gli esercizi ★★★ abbiano almeno un hint minimo

---

### Sezione Soluzioni

| Criterio       | Voto  | Note                            |
| -------------- | ----- | ------------------------------- |
| Completezza    | 10/10 | Tutte le 148 soluzioni presenti |
| Qualità codice | 9/10  | Idiomatico e ben commentato     |
| Spiegazioni    | 9/10  | Box ragionamento per ★★★★+      |
| Correttezza    | 9/10  | Verificate, output coerenti     |

**Punti di forza:**

- I "ragionamentoBox" per esercizi complessi sono eccellenti
- Il codice segue le convenzioni stabilite nel testo
- I commenti inline spiegano i passaggi chiave

**Issue minori rilevati:**

1. Es. 76 (`appiattisci-un-livello`): La soluzione usa `reduce #'append` che è O(n²). Menzionare `mapcan` come alternativa O(n).
2. Es. 83 (`raggruppa-per`): L'uso di `append` nel loop interno è inefficiente per liste lunghe.

---

## Parte III: Coerenza tra i Volumi

### Allineamento Contenuti ✓

| Teoria Cap. | Esercizi Workbook | Allineamento                |
| ----------- | ----------------- | --------------------------- |
| 1-2         | 1-21              | ✓ Perfetto                  |
| 3           | 22-68             | ✓ Perfetto                  |
| 4           | 69-92             | ✓ Perfetto                  |
| 5           | 93-120            | ✓ Perfetto                  |
| 6           | 121-123           | ✓ Corretto (pochi esercizi) |
| 7           | 124-136           | ✓ Perfetto                  |
| 8           | 137-144           | ✓ Corretto                  |
| 9           | 145-148           | ✓ Progetti integrativi      |

### Riferimenti Incrociati ✓

- **Teoria → Workbook:** I box `\workbox` rimandano correttamente agli esercizi
- **Workbook → Teoria:** Le note introduttive di ogni sezione rimandano al capitolo teorico

### Stile e Terminologia ✓

- Terminologia consistente tra i due volumi
- Convenzioni di codice identiche
- Uso coerente dei box colorati

### Discrepanze Minori Rilevate

1. **Teoria Cap. 3** menziona `labels` ma non `flet`; **Workbook** usa solo `labels` → OK, coerente con la scelta didattica
2. **Teoria Cap. 5** introduce `maphash` con sintassi `(maphash #'funzione ht)`; alcune soluzioni nel workbook usano `(maphash (lambda ...) ht)` → OK, equivalenti
3. **Quick Reference** nel workbook elenca funzioni non tutte usate negli esercizi → OK, è materiale di consultazione

---

## Parte IV: Verifica Tecnica

### Codice LaTeX

- **Preamble:** Ben strutturato, macro personalizzate utili
- **Box types:** Usati consistentemente (concetto, esempio, attenzione, intuizione, confronto)
- **Listing:** `columns=fullflexible, keepspaces=true` garantisce copy-paste
- **Caratteri:** Uso corretto di forme apostrofate nei listing

### Codice Lisp (campione verificato)

| Esercizio           | Correttezza | Output | Note                          |
| ------------------- | ----------- | ------ | ----------------------------- |
| 17 (somma-cifre)    | ✓           | ✓      | Ricorsione corretta           |
| 39 (reverse\*)      | ✓           | ✓      | Entrambe le versioni corrette |
| 54 (fibonacci-fast) | ✓           | ✓      | O(n) come richiesto           |
| 85 (compose)        | ✓           | ✓      | Closure corretta              |
| 91 (memoize)        | ✓           | ✓      | Uso corretto di m-v-b         |
| 108 (BST)           | ✓           | ✓      | Persistenza funzionale        |
| 125 (permutations)  | ✓           | ✓      | Gestisce duplicati            |
| 134 (n-queens)      | ✓           | ✓      | 92 soluzioni per n=8          |

---

## Parte V: Voti Complessivi

### Testo Teorico (Fondamenti)

| Dimensione             | Voto       |
| ---------------------- | ---------- |
| **Idea complessiva**   | 9.5/10     |
| **Struttura**          | 9/10       |
| **Realizzazione**      | 9/10       |
| **Chiarezza**          | 9/10       |
| **Precisione tecnica** | 9.5/10     |
| **Esaustività**        | 8.5/10     |
| **MEDIA**              | **9.1/10** |

### Workbook

| Dimensione                  | Voto       |
| --------------------------- | ---------- |
| **Idea complessiva**        | 10/10      |
| **Struttura**               | 9.5/10     |
| **Realizzazione**           | 9/10       |
| **Chiarezza**               | 9/10       |
| **Progressione difficoltà** | 9.5/10     |
| **Qualità soluzioni**       | 9/10       |
| **MEDIA**                   | **9.3/10** |

### Progetto Complessivo

| Dimensione                | Voto       |
| ------------------------- | ---------- |
| **Coerenza tra volumi**   | 9.5/10     |
| **Valore pedagogico**     | 9.5/10     |
| **Originalità approccio** | 9/10       |
| **Completezza**           | 9/10       |
| **Qualità tecnica**       | 9/10       |
| **VOTO FINALE**           | **9.2/10** |

---

## Parte VI: Raccomandazioni

### Priorità Alta (da fare)

1. **Aggiungere hint mancanti per esercizi ★★★**
   - Verificare sistematicamente che ogni ★★★ abbia almeno un suggerimento minimo
2. **Menzionare inefficienze nelle soluzioni dove rilevante**
   - Es. 76: nota su `mapcan` vs `reduce #'append`
   - Es. 83: nota sulla complessità

3. **Espandere Cap. 6 (Macro)**
   - Aggiungere 2-3 esercizi: `unless`, `aif` (anaphoric if), `with-gensyms`

### Priorità Media (consigliato)

4. **Aggiungere diagrammi dove mancano**
   - Grafo in Cap. 5 (strutture dati)
   - Albero di decisione per backtracking in Cap. 7

5. **Espandere Cap. 8 (Stringhe e I/O)**
   - Più esempi di `format`
   - Sezione su stream e file I/O

6. **Aggiungere sezione testing in Cap. 9**
   - Pattern semplice per unit test
   - Esempio con `assert`

### Priorità Bassa (nice to have)

7. **Appendice: Common pitfalls**
   - Lista degli errori più comuni dei principianti
   - Es: confusione `eq`/`eql`/`equal`, dimenticare `#'`, etc.

8. **Appendice: Setup ambiente**
   - Guida SBCL + Emacs/SLIME
   - Guida Allegro CL (già presente nel workbook, espandere)

9. **Indice analitico**
   - Per entrambi i volumi

---

## Parte VII: Errori/Imprecisioni Specifiche

### Teoria

| File                    | Linea circa | Issue                                                      | Severità |
| ----------------------- | ----------- | ---------------------------------------------------------- | -------- |
| 03_liste_ricorsione.tex | ~200        | "ricorrere su car e cdr separatamente" potrebbe confondere | Bassa    |
| 05_strutture_dati.tex   | ~150        | Manca menzione di `:test` default per `make-hash-table`    | Media    |

### Workbook

| File                | Esercizio | Issue                                | Severità |
| ------------------- | --------- | ------------------------------------ | -------- |
| 02_esercizi.tex     | 76        | Soluzione O(n²), non menzionato      | Bassa    |
| 04_soluzioni.tex    | 83        | Uso inefficiente di `append` in loop | Bassa    |
| 03_suggerimenti.tex | -         | Alcuni ★★★ senza hint                | Media    |

---

## Conclusioni

Il progetto **Common Lisp — Fondamenti + Workbook** è un lavoro didattico di **eccellente qualità**, superiore a molti testi commerciali sul tema.

**Punti distintivi:**

- La filosofia "funzionale prima" è applicata con coerenza
- Il sistema di percorsi ◆/■/○ è innovativo e utile
- La qualità del codice Lisp è professionale
- I box di ragionamento nelle soluzioni sono un valore aggiunto raro

**Per chi è adatto:**

- Studenti universitari di informatica (target dichiarato) ✓
- Autodidatti con basi di programmazione ✓
- Programmatori esperti che vogliono imparare Lisp ✓

**Giudizio finale:** Un testo che merita pubblicazione. Con le modifiche suggerite (priorità alta), potrebbe diventare il riferimento italiano per l'insegnamento del Common Lisp.

---

_Documento generato da revisione sistematica di tutti i file sorgente LaTeX._
_Ultima verifica: Settembre 2026_
