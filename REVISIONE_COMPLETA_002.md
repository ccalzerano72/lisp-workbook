# Revisione completa — Common Lisp: Fondamenti + Workbook

**Data:** settembre 2026  
**Revisore:** Kiro (AI)  
**Versione esaminata:** Prima edizione, settembre 2026

---

## Indice

1. [Giudizio complessivo](#1-giudizio-complessivo)
2. [Voti numerici](#2-voti-numerici)
3. [Teoria — analisi capitolo per capitolo](#3-teoria--analisi-capitolo-per-capitolo)
4. [Workbook — analisi sezione per sezione](#4-workbook--analisi-sezione-per-sezione)
5. [Coerenza incrociata teoria/workbook](#5-coerenza-incrociata-teorieworkbook)
6. [Correttezza tecnica](#6-correttezza-tecnica)
7. [Problemi stilistici e tipografici](#7-problemi-stilistici-e-tipografici)
8. [Omissioni e gap pedagogici](#8-omissioni-e-gap-pedagogici)
9. [Ridondanze](#9-ridondanze)
10. [Priorità di intervento](#10-priorità-di-intervento)

---

## 1. Giudizio complessivo

Il progetto è solido e ben strutturato. Il filo conduttore pedagogico è chiaro e coerente: partire dal funzionale, introdurre la mutabilità quando ne emerge la necessità concreta, e avere sempre la pratica al passo con la teoria. La qualità della scrittura è alta, la terminologia è precisa e la progressione è pensata bene.

I problemi che ho trovato sono quasi tutti di secondo livello: imprecisioni locali, riferimenti incrociati mancanti o sbagliati, alcune discordanze tra esercizio e soluzione, e qualche sbilanciamento nella distribuzione di dettaglio tra capitoli. Non ci sono errori gravi di contenuto. Il progetto è pubblicabile nella forma attuale, ma con le correzioni elencate sarebbe significativamente più rigoroso.

---

## 2. Voti numerici

### 2.1 Valutazione per volume

| Criterio                    | Teoria | Workbook |
| --------------------------- | ------ | -------- |
| **Idea e concezione**       | 9/10   | 9/10     |
| **Struttura**               | 8/10   | 8/10     |
| **Realizzazione**           | 7/10   | 7/10     |
| **Chiarezza**               | 8/10   | 8/10     |
| **Precisione tecnica**      | 7/10   | 7/10     |
| **Esaustività**             | 6/10   | 7/10     |
| **Progressione pedagogica** | 8/10   | 8/10     |
| **Coerenza interna**        | 7/10   | 7/10     |
| **Coerenza inter-volume**   | 7/10   | 7/10     |

### 2.2 Valutazione per capitolo (teoria)

| Cap.       | Titolo                       | Idea | Struttura | Realizzazione | Note sintetiche                                                   |
| ---------- | ---------------------------- | ---- | --------- | ------------- | ----------------------------------------------------------------- |
| 1          | Il modello mentale           | 9    | 8         | 8             | Ottimo avvio, piccola imprecisione sui workbook-rimandi           |
| 2          | Funzioni e dati fondamentali | 9    | 8         | 8             | Buono, manca trattamento `char-digit-p`                           |
| 3          | Liste e ricorsione           | 9    | 8         | 7             | Eccellente struttura, file troncato in lettura (no tail del cap.) |
| 4          | Higher-order e closure       | 9    | 9         | 8             | Il migliore del volume                                            |
| 5          | Strutture dati               | 8    | 8         | 7             | Buono ma la sezione defstruct/CLOS è debolissima                  |
| 6          | Macro                        | 8    | 8         | 7             | Corretto, manca sezione su `define-condition`                     |
| 7          | Backtracking                 | 8    | 9         | 8             | Struttura esemplare, rimandi workbook accurati                    |
| 8          | Stringhe, I/O e parsing      | 7    | 8         | 7             | Buono ma la nota su `ignore-errors` è fuori posto                 |
| 9          | Stile e professione          | 7    | 7         | 7             | Solido ma sottile rispetto all'ambizione del titolo               |
| App. Stack | —                            | 8    | —         | —             | Non letto in dettaglio (file disponibile)                         |
| App. ADT   | —                            | 8    | —         | —             | Non letto in dettaglio                                            |

---

## 3. Teoria — analisi capitolo per capitolo

### Capitolo 1 — Il modello mentale di Lisp

**Punti di forza**

- Il box intuizione iniziale è efficace: stabilisce subito il cambio di paradigma.
- Il trattamento di S-expression è chiaro e sufficientemente formale.
- La sezione sul ciclo di sviluppo professionale (`:trace`, `:ld`) è concreta e utile, rara nei libri introduttivi.
- La bussola sul funzionale ("partire dal funzionale, non dall'assegnazione") è posizionata correttamente.

**Problemi**

1. **Rimando workbook sezione 5 (es. 5–11) impreciso.** Il testo dice "questi esercizi richiedono `let`, `cond` e `mod` — leggi la sezione Condizioni nel Capitolo 2". Ma l'es. 6 (Pari o dispari, essenziale) richiede solo `mod`, che compare già in cap. 1 nell'esempio aritmetica. Il vincolo alla lettura del cap. 2 è eccessivo per quell'esercizio specifico.

2. **La sezione sui simboli (§1.5) cita `defconstant +max-iter+ 1000`** come esempio di costante ma questo simbolo non viene più usato nel libro. Sarebbe più coerente usare un nome che appare altrove (es. `+max-n+`).

3. **Manca un cenno a `nil` come simbolo speciale** nella sezione di valutazione. Nel box concetto sulla valutazione si dice "simbolo: viene cercato nell'ambiente corrente" — ma `nil` è un simbolo che non si cerca nell'ambiente, si auto-valuta. Questo è un dettaglio che il cap. 2 correggerà, ma lascia una piccola incoerenza non segnalata.

4. **Nessun box `workbook` dopo la sezione sul trace (§1.7).** Il capitolo termina con il box workbook principale, ma la sezione sul trace non ha un riferimento esplicito ai corrispondenti esercizi. Il cap. 3 usa `:trace` estensivamente: un rimando proattivo qui sarebbe utile.

---

### Capitolo 2 — Funzioni e dati fondamentali

**Punti di forza**

- La distinzione `let` / `let*` con l'esempio del `let` che fallisce è didatticamente precisa.
- Gli idiomi `or` per default e `and` per guard clause sono eccellenti: concrete, immediatamente riusabili.
- L'esempio `format` con tutte le direttive essenziali copre l'80% dei casi reali.
- Il box workbook finale specifica correttamente "se hai già fatto 1–11 dopo il Cap. 1, ora completa 12–21".

**Problemi**

1. **`char-digit-p` citato nella soluzione es. 97 ma non introdotto nel capitolo.** Nel capitolo 2 si parla di `char-alphabetic-p` e `char-code`, ma `char-digit-p` (usato nel cap. 8 e nelle soluzioni) non viene spiegato mai esplicitamente nel testo teorico. Va aggiunto o nel cap. 2 (§ "Caratteri") o nel cap. 8.

2. **Il trattamento di `integer` è incompleto.** Si dice "interi a precisione arbitraria" ma non si menziona la distinzione pratica `fixnum`/`bignum` che emerge nell'output `(type-of 42)` → `FIXNUM`. Lo studente che prova l'esempio nel REPL riceve `FIXNUM` e non capisce perché l'output differisce da quello mostrato (`INTEGER`). O si corregge l'output nel listing, o si aggiunge una nota.

3. **`rem` vs `mod` non abbastanza enfatizzato.** Il listing mostra `(rem -7 3) ; => -1` ma non spiega che questo è il comportamento atteso e che `mod` ha semantica diversa. Per lo studente che viene da C, dove `%` si comporta come `rem`, questa è una trappola reale. Meriterebbe un box `attenzione`.

4. **La sezione sui valori multipli (§2.4)** introduce `values`/`multiple-value-bind` ma non dice che `floor` con due argomenti li usa (compare nell'esempio ma non viene esplicitamente collegato alla sezione). Questo crea confusione perché lo studente ha già visto `floor` in §2.1 con semantica diversa.

5. **Nel riepilogo finale**, gli essenziali sono elencati come "1, 4, 6, 8, 11, 15, 17, 18" — ma nel workbook `essbox` (◆) corrispondono a 1, 4, 6, 8, 11, 15, 17, 18: corrispondenza verificata ✓. Tuttavia nel riepilogo del cap. 1 gli essenziali indicati erano "1, 6" e qui si citano "1, 4, 6, 8, 11, 15, 17, 18". Non è un errore, ma sarebbe utile indicare esplicitamente che quelli nuovi rispetto al cap. 1 sono 4, 8, 11, 15, 17, 18.

---

### Capitolo 3 — Liste e ricorsione

**Punti di forza**

- Il diagramma TikZ delle cons-cell è un punto di forza del libro: visuale, preciso, e ben annotato.
- I tre pattern (reduce/map/filter) sono introdotti prima degli higher-order: la progressione è didatticamente corretta.
- Il box confronto "Map, Reduce, Filter — da dove vengono i nomi" è ottimo: situa Lisp storicamente e motiva lo studio.
- La sezione sul reverse naif vs accumulatore è esemplare.

**Problemi**

1. **Nota sulle liste improprie ("dotted list")** inserita nel box concetto sullo schema ricorsivo: correttamente avverte che il libro lavora solo con liste proprie, ma il termine "lista impropria" non è stato ancora introdotto. Meriterebbe un box `nota` separato con un breve esempio `'(a b . c)` per dare concretezza.

2. **Il workbook box dopo §3.3 (cons vs append)** rimanda all'es. 40 ma non all'es. 48 (intercala), che usa `cons` in modo analogo. Non è un errore critico ma è un'omissione nell'orientamento.

3. **Nella sezione "Funzioni utili sulle liste"** si dice "`remove-duplicates` tiene l'ultima occorrenza". Questa affermazione è corretta ma può sorprendere: è il comportamento di default `:from-end nil`. Il book mostra anche la variante `:from-end t`, ma la formulazione iniziale è talmente assertiva che lo studente potrebbe generalizzare erroneamente. Sarebbe più preciso scrivere "per default rimuove le occorrenze iniziali, mantenendo l'ultima".

4. **Il Crivello di Eratostene (es. 64) viene presentato nel cap. 3** (Ricorsione avanzata) ma usa `make-array` e `setf`/`aref` che sono introdotti formalmente solo nel cap. 5 (Strutture dati). Il testo del cap. 3 include una spiegazione inline degli array (il riquadro grigio "Cosa è un array in Common Lisp"), ma questo crea uno sfasamento: si tratta di un mini-capitolo sugli array dentro un capitolo sulla ricorsione. Valutare se spostare il crivello al cap. 5, oppure se tenere la spiegazione ma indicare esplicitamente "qui anticipiamo gli array; vedremo la struttura completa nel cap. 5".

5. **`setf` come generalized place** (§3, riquadro grigio con `\label{sec:setf-places}`) viene introdotto qui per la prima volta in modo formale. Ma il cap. 2 usa già `setf` in vari esempi senza questa spiegazione. Ci vuole un rimando retroattivo o lo spostamento dell'approfondimento al cap. 2.

---

### Capitolo 4 — Higher-order e closure

**Punti di forza**

- Struttura impeccabile: prima la teoria delle funzioni di prima classe, poi la libreria standard, poi lambda, poi closure.
- Il riquadro grigio sulla cattura lessicale ("Come funziona la cattura") con lo stesso esempio in Java/C++/JavaScript è eccellente.
- L'avviso su `mapcan` distruttivo è corretto e importante.
- La sezione composizione/parziale è completa e gli esempi sono eleganti.

**Problemi**

1. **Il rimando workbook finale** indica come priorità "69, 70, 72, 78, 85, 87" ma nel box workbook successivo a §4.3 (closure) indica "85–88" come "il cuore del capitolo" e come essenziali "85, 87". C'è una leggera incoerenza: 78 è indicato come prioritario nel riepilogo ma non in quello locale. Non grave, ma da allineare.

2. **`mapcan` con nota "è distruttivo"** — il testo spiega che usa `nconc` internamente. Ma poi non dice come costruire liste "fresche" in modo sistematico. La soluzione suggerita ("usare `list`, `copy-list`") è corretta ma potrebbe essere più concreta con un esempio che mostra il problema e la correzione.

3. **Nessuna menzione di `funcall` vs applicazione diretta** in implementazioni che supportano `(fn arg)` direttamente (Common Lisp moderno accetta `(funcall #'f x)` ma anche `(#'f x)` in SBCL/Allegro). Questo non è un errore ma è una semplificazione che può creare confusione quando lo studente legge codice reale.

---

### Capitolo 5 — Strutture dati

**Punti di forza**

- Il percorso "lista → alist → hash → array → defstruct → BST → stack/queue" come progressione motivata da limitazioni concrete è pedagogicamente eccellente.
- Il box `attenzione` su `:test #'equal` per le hash table con chiavi stringa è fondamentale e ben posizionato.

**Problemi (capitolo con più criticità)**

1. **La sezione su `defstruct` è molto sottile.** Il capitolo introduce `defstruct` nell'es. 105 del workbook ma il testo teorico non ha una sezione dedicata con i costrutti: `make-persona`, `persona-nome`, `persona-p`, `copy-persona`. Lo studente che si trova davanti all'esercizio senza aver letto il workbook note manca di riferimento teorico. Serve una sezione §5.x sul defstruct con tutti gli accessor generati automaticamente.

2. **CLOS non è trattato.** Il capitolo 9 (Stile) cita CLOS come opzione per l'esercizio 148, e la workbook box del cap. 5 lo cita, ma nel testo teorico non c'è nessuna introduzione. Dato che il libro dichiara "Common Lisp è multi-paradigma" e che l'esercizio finale richiede esplicitamente "defstruct o CLOS", l'assenza di anche solo un paragrafo su `defclass`/`defmethod` è una lacuna significativa.

3. **Le sezioni BST, stack e queue del cap. 5** sono presentate come "implementate negli esercizi" ma il testo teorico non le discute. Questo è coerente con la filosofia "pratica prima", ma crea un vuoto: il lettore che non fa gli esercizi non ha mai visto questi concetti spiegati. Quantomeno un paragrafo di inquadramento concettuale sarebbe utile.

4. **Il box `mnota` sulla `setf` dei generalized places** (con cross-reference a `\label{sec:setf-places}`) nel cap. 5 rimanda alla definizione nel cap. 3 — corretto. Tuttavia la nota appare prima che lo studente abbia visto l'esempio concreto nella hash table. L'ordine di presentazione potrebbe essere migliorato.

5. **L'esempio di `hash->alist` e `alist->hash`** nel cap. 5 usa `setf result (acons ...)` dentro `maphash`. Questo funziona ma usa `setf` su una variabile legata da `let`, che è stile imperativo. Un commento esplicito che giustifica la scelta ("qui `setf` è la soluzione naturale per accumulare risultati in `maphash`, che non restituisce un valore utile") è già presente come `\detail{}` ma è meno visibile di quanto meriterebbe.

---

### Capitolo 6 — Macro

**Punti di forza**

- La spiegazione del perché le funzioni non bastano (esempio `mio-and-fn` con `(/ 1 0)`) è la migliore nei libri introduttivi Common Lisp che abbia letto.
- Il trattamento del backquote è chiaro e completo.
- `macroexpand-1` posizionato come strumento di debug obbligatorio: corretto.
- La sezione "Quando usarle / Non usarle" è bilanciata e concreta.

**Problemi**

1. **`define-condition` non è mai menzionato.** Il cap. 9 parla di `error`/`handler-case` ma le condizioni personalizzate compaiono solo in un punto del testo come "Da qui in avanti" suggerimento facoltativo. Dato che `with-open-file` viene usato come esempio di macro giustificata proprio per il cleanup in caso di errore, un paragrafo sulle condizioni custom qui o nel cap. 9 colmerebbe il gap.

2. **Il codice di esempio `swap!-bug`** mostra il problema della cattura di variabile, ma nella versione corretta con `gensym` l'output dell'espansione è `(LET ((#:G1234 X)) ...)`. Non tutti gli studenti sanno cosa significa `#:G1234`. Un dettaglio su "i simboli non interned (#:) non possono interferire con nessun simbolo user-visible" renderebbe l'esempio più completo.

3. **`&body` vs `&rest`**: il testo dice "la differenza è solo di indentazione automatica". Questa affermazione è quasi vera ma non del tutto: `&body` indica anche che il corpo è una sequenza di form, non necessariamente un numero variabile di argomenti. In alcuni strumenti e debugger la distinzione è rilevante.

---

### Capitolo 7 — Backtracking e algoritmi

**Punti di forza**

- Struttura del capitolo esemplare: generate-and-test → stato/scelta/vincolo → pruning → esempi canonici.
- Il confronto "backtrack in Lisp è il ritorno dalla chiamata ricorsiva" vs stack esplicito Java è preciso e importante.
- N-Queens spiegato bene: prima il modello, poi il predicato, poi la funzione principale.
- Corretta l'osservazione su `some` come idioma "prima soluzione trovata".

**Problemi**

1. **L'es. 136 (Knight's Tour)** è citato nel testo come "applica lo stesso schema" ma il Knight's Tour con backtracking puro su una scacchiera 8×8 è intrattabile senza l'euristica di Warnsdorff. Il testo dice "lo stesso schema" senza avvertire che per N=8 il backtracking puro sarà lentissimo. Un box `nota` su questo sarebbe onesto.

2. **L'esempio `coppie-con-somma`** in §7.1 usa `push` e `nreverse`, che sono pattern imperativi. Il testo non commenta questa scelta. Per coerenza con la filosofia "funzionale prima", un commento come "qui usiamo accumulo imperativo perché il doppio `dolist` è naturalmente imperativo; la versione funzionale userebbe `loop collect`" sarebbe appropriato.

3. **Il `memoization` appare nell'esempio del Sudoku** come "non si applica al backtracking" ma viene poi rimandato all'Appendice ADT. Questo collegamento è debole: `memoize` è già stato introdotto nell'es. 91 del workbook (cap. 4) con implementazione completa. Il rimando qui dovrebbe puntare a quello, non all'appendice.

4. **Esercizi 129–130 non esplicitamente menzionati** nel box workbook del cap. 7. Il box finale elenca come priorità 124, 125, 126, 127, 134 ma gli es. 129–130 (palindromi vs backtracking? verificare numerazione completa degli esercizi) non sono citati. Questo potrebbe essere semplicemente il risultato di non aver letto i listing completi degli esercizi 129–133 — ma andrebbe verificato.

---

### Capitolo 8 — Stringhe, I/O e parsing

**Punti di forza**

- La catena di astrazione (char → string → stream → read/write → tokenizer → RPN → evaluator) è ben articolata.
- Il mini-evaluator è il punto più alto del libro: spiega strutturalmente come funziona un interprete Lisp, non solo come implementarne uno minimale.
- Il warning su `*read-eval*` è corretto e importante (sicurezza).
- L'estensione dell'ambiente con `acons` nell'ultimo esempio è elegante.

**Problemi**

1. **La nota su `ignore-errors` è fuori posto.** Appare alla fine della sezione sul parser RPN come "Nota: `ignore-errors` esegue il corpo e...". Ma `ignore-errors` non viene usato nell'esempio mostrato in quella sezione. La nota sembra un residuo di una versione precedente dove l'implementazione RPN includeva la gestione degli errori con `ignore-errors`. Va rimossa o spostata al cap. 9 dove `ignore-errors` viene effettivamente trattato.

2. **`coerce` non è mai formalmente introdotto.** Viene usato nella funzione `tokenizza` con `(coerce (nreverse corrente) 'string)` e menzionato in §8.2 per convertire stringa in lista, ma non esiste un box o sezione che ne spieghi la sintassi generale. In un volume teorico, questo merita almeno una riga.

3. **La funzione `tokenizza` del cap. 8** usa `map nil` spiegato come "come `mapcar` ma scarta i risultati". In realtà `map nil` è equivalente a `mapc` per le liste. `mapc` è più idiomatico in Common Lisp e andrebbe almeno menzionato come alternativa.

4. **Il box workbook dopo §8.3 (stream/file)** dice "non ci sono esercizi dedicati in questo capitolo; li userai nell'esercizio 148". Ma l'es. 140 (anagram-p) e 141 (count-char) sono citati nel paragrafo workbook della sezione sulle stringhe, e non c'è nessun esercizio di I/O su file prima del 148. Un esercizio specifico su `with-open-file` (leggere/scrivere un file semplice) sarebbe utile tra gli es. 137–148.

---

### Capitolo 9 — Stile e professione

**Punti di forza**

- La sezione sul refactoring (funzione monolitica → tre funzioni con responsabilità separate) è il miglior esempio pratico del capitolo.
- L'esempio ASDF minimale è funzionale e sufficiente per un progetto piccolo.
- La sezione testing con entrambi gli approcci (assert e fiveam) è equilibrata.
- Il paragrafo conclusivo "dalla prima valutazione all'esercizio 148" è efficace.

**Problemi**

1. **Il capitolo è debolissimo sulle performance.** La sezione profiling mostra `time` e `declare optimize`, ma non menziona concetti fondamentali come: evitare ricorsione non-tail su liste lunghe, quando usare `the` per type hints, il costo della creazione di cons-cell vs array. Per un capitolo intitolato "Stile e professione" questo è un vuoto rilevante.

2. **`fiveam` è citato come libreria di testing ma non `parachute`**, citato nel riquadro concetto. Questa incoerenza interna (il concetto dice "fiveam o parachute", l'esempio usa solo fiveam) andrebbe risolta scegliendo uno dei due come esempio principale.

3. **La sezione package** è corretta ma non menziona l'idioma `:use :cl` che è presente in quasi ogni defpackage reale — viene mostrato nell'esempio ma non esplicitato nel testo introduttivo. Manca anche la gestione dei conflitti tra package (se due package esportano lo stesso simbolo), che pure compare in un box `attenzione` ma senza esempio concreto.

4. **`handler-bind` non è mai introdotto**, solo `handler-case`. Per un libro che parla di "programmazione professionale" e menziona i restart come vantaggio di CL rispetto a Java, l'assenza di anche solo un paragrafo su `handler-bind` è una lacuna.

---

## 4. Workbook — analisi sezione per sezione

### Struttura generale

La struttura in 10 capitoli con 148 esercizi è solida. La distribuzione per tipo (25 ◆ essenziali, 54 ■ standard, 69 ○ collaterali) è ragionevole. I percorsi dichiarati (minimo/standard/completo) sono ben motivati.

### Cap. 1 — Fondamenti (es. 1–21)

**Punti di forza**

- La progressione da aritmetica pura (1–4) a condizionali (8–11) a loop (17–19) è precisa.
- Il vincolo su `let` nell'es. 4 e `let*` nell'es. 15 è pedagogicamente corretto.
- L'es. 11 (anno bisestile) con il vincolo `and`/`or` senza `cond` è un esercizio intelligente.

**Problemi**

1. **Es. 16 (calcolatrice simbolica) è in sezione `stdbox` ma usa `case`** che non è stato introdotto formalmente nel cap. 1. La soluzione usa `case` correttamente. Il problema è che la soluzione è corretta ma lo studente al cap. 1 non ha ancora visto `case` — viene introdotto nel cap. 2. Questo esercizio dovrebbe essere spostato dopo che `case` è stato trattato, o il cap. 1 dovrebbe anticiparne l'introduzione.

2. **L'es. 17 (somma delle cifre)** ha difficoltà ★★ ma il suggerimento richiede di capire `floor` usato come divisione intera (con un solo argomento). La soluzione usa `(floor n 10)` correttamente, ma il cap. 2 introduce `floor` con la nota "quando usato con due argomenti restituisce quoziente e resto". Qui `floor` viene usato con un argomento, che è un uso diverso. Il suggerimento non disambigua questo.

3. **Nessun esercizio su `and`/`or` come espressioni con valore** (non come condizionali booleani puri). Gli idiomi "default con `or`" e "guard con `and`" del cap. 2 teorico non hanno un esercizio corrispondente. L'es. 11 usa `and`/`or` ma solo per il valore booleano.

### Cap. 2 — Liste (es. 22–68)

**Punti di forza**

- Gli es. 35 e 36 (incrementa-tutti, filtra pari) con il vincolo "non usare mapcar/remove-if" sono pedagogicamente ottimi: costruiscono il pattern prima di darlo come primitiva.
- L'es. 39 (reverse con accumulatore) con la richiesta esplicita di scrivere prima la versione naif poi quella con accumulatore è eccellente.
- L'es. 49 (RLE encode/decode) è ben costruito come problema a due parti.

**Problemi**

1. **L'es. 46 (estrai chiavi da alist)** ha soluzione `(mapcar #'car alist)` che usa `mapcar` prima che sia stato introdotto formalmente (è nel cap. 4). La soluzione è corretta ma anticipa un costrutto del capitolo successivo. O si posticipa l'esercizio, o si richiede una soluzione ricorsiva esplicita coerente col capitolo.

2. **L'es. 62 (MCD e MCM)**: la soluzione `mcm*` calcola `(/ (* a b) (mcd* a b))` che per valori grandi può causare overflow intermedio in bignum. Non è un errore per Common Lisp (che ha bignum nativi), ma merita una nota.

3. **L'es. 64 (crivello di Eratostene)**: il suggerimento dice "il ciclo esterno va da 2 a `isqrt(n)`" ma nella soluzione il ciclo è `(loop for i from 2 to (isqrt n) ...)`. La funzione è `isqrt`, non `sqrt`. Il suggerimento usa la notazione matematica $\sqrt{n}$ senza specificare che si usa `isqrt` (radice intera). Per lo studente che non conosce `isqrt`, questo può causare confusione perché `sqrt` restituisce un float e il confronto `to` con un float potrebbe non funzionare come atteso.

4. **L'es. 66 (sublist)**: la soluzione usa `(loop for i from inizio below fine collect (nth i lst))` che è O(n²) per accesso ripetuto con `nth`. Una soluzione con `nthcdr` e poi un loop di lunghezza `(- fine inizio)` sarebbe O(n) ed è quella suggerita nella spiegazione dell'esercizio stesso. C'è **discordanza tra spiegazione e soluzione** nella scelta dell'algoritmo.

5. **L'es. 67 (raggruppa in blocchi)**: la soluzione usa un `loop` inside la `cons` che itera su `lst` ma raccoglie solo i primi `n` elementi. Questo è corretto ma l'implementazione con `(loop for x in lst for i below n collect x)` è insolita: il loop itera su `lst` ma termina quando `i` raggiunge `n`. Per lo studente che ha appena imparato il loop, questa forma può essere confusa. Una versione con `subseq` o `nthcdr` sarebbe più chiara.

### Cap. 3 — Ricorsione avanzata (es. 51–68 _note: numerazione sovrapposta con cap. 2_)

_Nota: I capitoli del workbook non sono numerati 1-based ma corrispondono alla progressione degli esercizi. Il cap. "Ricorsione avanzata" corrisponde agli es. 51–68 nella numerazione globale._

**Punti di forza**

- Gli es. 51–53 (fattoriale, reverse, somma-range in forma tail-recursive) come trittico su `labels` è ottimo.
- L'es. 54 (Fibonacci O(n)) con la spiegazione dei due accumulatori è il migliore esercizio del capitolo.
- L'es. 55 (flatten) con la distinzione tra caso `(atom tree)` e `(null tree)` come due casi base separati è pedagogicamente preciso.

**Problemi**

1. **La nota sulla tail recursion** (`\label{nota:tailrec}`) viene referenziata più volte negli esercizi (es. 39, 51, 52, 53) ma appare alla fine del capitolo, dopo gli esercizi stessi. Lo studente che fa l'es. 39 e trova il rimando "vedi nota sulla tail recursion in fondo al capitolo" deve scorrere avanti per trovarla. Considerare di spostare la nota prima degli esercizi che la referenziano, o di includere un breve riassunto inline nel primo esercizio che la cita.

2. **L'es. 52 ha nome funzione diverso dalla soluzione.** L'esercizio chiede di implementare `reverse*` (uguale all'es. 39), ma la soluzione nomina la funzione `reverse-tr`. Questa è una **incoerenza diretta esercizio/soluzione**: lo studente si aspetta `reverse*` e trova `reverse-tr`.

3. **L'es. 56 (tree-depth)**: il suggerimento dice di usare il massimo tra "profondità car +1" e "profondità cdr". La soluzione implementa esattamente questo. Ma la spiegazione dell'esercizio descrive la profondità come "profondità massima di nesting". Questa definizione è ambigua: `(a b c)` ha profondità 1, `(a (b c))` ha profondità 2. L'output atteso `(tree-depth '(a b c)) ; -> 1` e `(tree-depth '()) ; -> 0` è coerente con la soluzione, ma la definizione testuale dovrebbe essere più precisa.

### Cap. 4 — Higher-order e closure (es. 69–92)

**Punti di forza**

- La nota tecnica all'inizio del capitolo sugli higher-order, closure e funzioni di prima classe è ben strutturata.
- L'es. 85 (compose) e l'es. 87 (make-counter) sono i due esercizi più importanti e sono bene costruiti.
- L'es. 91 (memoization) è ambizioso per il livello ★★★★ ma la spiegazione è sufficiente.

**Problemi**

1. **L'es. 79 (`mapcan` per raddoppiare)**: la spiegazione è corretta e il contrasto con `mapcar` è esplicito. Ma l'avviso "mapcan è distruttivo" presente nel testo teorico non appare nell'esercizio. Lo studente potrebbe implementare `(mapcan #'(lambda (x) '(x x)) lst)` usando una lista quoted (condivisa), causando comportamento indefinito. Un vincolo esplicito "la lambda deve restituire una lista fresca (`list x x`), non una lista quoted" sarebbe necessario.

2. **L'es. 90 (pipeline)** rimanda al contrasto con `compose` es. 85 nella nota finale. Questo è utile. Ma la soluzione non è stata verificata nel materiale disponibile — occorre verificare che la soluzione usi `reduce` come richiesto.

3. **L'es. 92 (mini libreria funzionale)** è un esercizio ★★★★ che richiede di raccogliere varie funzioni con docstring. Non ha una soluzione nel workbook (solo codice, senza ragionamento). Dato che richiede scelte di design, un commento sulle scelte fatte sarebbe utile.

### Cap. 5 — Strutture dati (es. 93–120)

**Punti di forza**

- L'es. 96 con la nota "obiettivo: confrontare alist vs hash table" è un ottimo esempio di esercizio metacognitivo.
- Gli es. 106–112 (alberi con liste, BST, traversal) sono una progressione ben costruita.
- L'es. 114 (queue con due puntatori) con la spiegazione dell'efficienza O(1) è pedagogicamente preciso.
- L'es. 115 (valida parentesi con stack) è un classico ben calibrato.

**Problemi**

1. **L'es. 93 (association list)**: la funzione `set-key` aggiunge in testa con `acons` senza rimuovere la vecchia coppia. Questo è corretto come comportamento di shadowing, ma l'output atteso `((AGE . 24) (NAME . "Mario"))` mostra solo due elementi, non tre (non mostra che la vecchia coppia `(AGE . 23)` è ancora lì, sommersa). Un output più onesto sarebbe `((AGE . 24) (NAME . "Mario") (AGE . 23))` con una nota sul comportamento di `assoc` (legge la prima occorrenza). Questo non è un errore nella soluzione, ma l'output dell'esempio nel testo dell'esercizio è fuorviante.

2. **L'es. 105 (defstruct persona)** richiede una funzione `crea-persona` che valida l'età. La soluzione usa `error` direttamente. Non c'è menzione di `check-type` che sarebbe il modo idiomatico CL per questo. Un commento sulla distinzione sarebbe utile.

3. **Manca un esercizio su CLOS** (almeno base: `defclass`, `defmethod`, `make-instance`). Il cap. 9 e il progetto finale (es. 148) citano CLOS come opzione, ma non c'è nessun esercizio introduttivo. Uno stdbox su "definire una classe e un metodo" colmerebbe il gap.

### Cap. 6 — Macro (es. 121–123)

**Punti di forza**

- Solo tre esercizi ma ben calibrati: `quando` (quando), `mio-while`, `mio-for`.
- La progressione: implementa prima, poi studia l'espansione con `macroexpand-1`.

**Problemi**

1. **L'es. 123 (`mio-for`)** dice "leggilo con attenzione anche se non lo implementi". Questo suggerimento è ragionevole, ma l'esercizio è classificato `colbox` (○, collaterale). Se è importante per la comprensione di `gensym`, forse meriterebbe essere `stdbox`.

2. **Non c'è un esercizio su `define-condition`**. Data l'importanza delle condizioni personalizzate nel codice professionale CL, un esercizio base (es. 121.5 o un esercizio bonus) sarebbe utile.

### Cap. 7 — Backtracking (es. 124–136)

**Punti di forza**

- Progressione dagli es. 124 (subsets) a 134 (N-Queens) costruita perfettamente.
- L'es. 134 (N-Queens) con la verifica `(length (n-queens 8)) = 92` è un ottimo criterio di correttezza automatico.

**Problemi**

1. **L'es. 131 (Hanoi)**: non è un problema di backtracking ma di divide-and-conquer ricorsivo. La sua presenza nel capitolo "Backtracking" è fuorviante. Andrebbe spostato nel cap. 3 (Ricorsione avanzata) o accompagnato da una nota esplicita che chiarisca la distinzione.

2. **L'es. 128 (genera-parentesi)**: la spiegazione dice "pruning strutturale: le parentesi aperte non possono superare n". Questo è corretto. Ma la spiegazione non dice qual è la condizione di successo (stato completo: n aperte e n chiuse). Un esercizio di backtracking dovrebbe sempre rendere esplicito il predicato di completezza.

### Cap. 8 — Stringhe, I/O, parsing (es. 137–144)

**Punti di forza**

- L'es. 143 (evaluator semplice) + 144 (mio-eval con ambiente) è la progressione migliore del workbook.

**Problemi**

1. **Manca un esercizio su `with-open-file` prima dell'es. 148.** Come già osservato per la teoria: lo studente incontra I/O su file solo nell'esercizio finale. Un esercizio intermedio (leggere righe da un file, contare le parole, scrivere una lista su file) sarebbe necessario.

2. **L'es. 142 (rpn-eval)**: il vincolo dice "usare una pila". Ma la pila non è stata introdotta formalmente come ADT fino all'es. 113 (cap. 5). Se si arriva all'es. 142 seguendo il percorso lineare, la pila è già nota. Ma se si fa l'es. 142 prima dell'es. 113 (seguendo il capitolo tematico anziché la numerazione globale), il vincolo è opaco. Un rimando esplicito a es. 113 sarebbe utile.

### Cap. 9 — Algoritmi e progetto (es. 145–148)

_Nota: dalla numerazione degli esercizi vista nei workbook box del testo teorico, gli es. 145–148 non sono stati esaminati direttamente. Le osservazioni seguenti si basano su riferimenti nel testo._

1. **L'es. 148 (progetto gestionale)** è descritto nel cap. 9 del testo teorico come il punto di sintesi del percorso. I requisiti sono ben definiti (defstruct/CLOS, hash table, CRUD, file I/O, docstring, package, test). Il problema è che alcuni requisiti (CLOS, `handler-case`) fanno riferimento a concetti introdotti molto brevemente o mai nella teoria. Il progetto rischia di essere fattibile solo per chi ha già esperienza CL.

---

## 5. Coerenza incrociata teoria/workbook

### 5.1 Rimandi dalla teoria al workbook

| Capitolo teoria | Box workbook             | Esercizi citati                | Correttezza                                       |
| --------------- | ------------------------ | ------------------------------ | ------------------------------------------------- |
| Cap. 1          | Fine cap. (§1.5)         | 1–4                            | ✓                                                 |
| Cap. 1          | Fine cap. (§1.6)         | 5–11                           | ✓ (ma vedi nota)                                  |
| Cap. 1          | Riepilogo                | 1–11 (tutti)                   | ✓                                                 |
| Cap. 2          | §2.2 (let/let\*)         | 4–5                            | ✓                                                 |
| Cap. 2          | §2.3 (cond)              | 8–16                           | ✓                                                 |
| Cap. 2          | §2.4 (iterazione)        | 17–21                          | ✓                                                 |
| Cap. 2          | Riepilogo                | 1–21, ◆ = 1,4,6,8,11,15,17,18  | ✓                                                 |
| Cap. 3          | §3.1 (car/cdr)           | 22–26                          | ✓                                                 |
| Cap. 3          | §3.2 (pattern ricorsivo) | 27–38, ◆=27,31,35              | ✓                                                 |
| Cap. 3          | §3.3 (cons/append)       | 40                             | ✓                                                 |
| Cap. 3          | §3.4 (reverse/acc)       | 39, 51–53                      | ✓                                                 |
| Cap. 3          | §3.5 (tail rec)          | —                              | Manca rimando esplicito a 51–53 in questa sezione |
| Cap. 3          | §3.6 (alberi)            | 55–60                          | ✓                                                 |
| Cap. 4          | §4.2 (libreria HOF)      | 69–84, ◆=69,70,72,78,85        | Incoerenza: 85 è nel cap. closure, non HOF        |
| Cap. 4          | §4.4 (closure)           | 85–88                          | ✓                                                 |
| Cap. 4          | Riepilogo                | 69–92, ◆=69,70,72,78,85,87     | ✓                                                 |
| Cap. 5          | §5.1 (alist)             | 93–94, 100                     | ✓                                                 |
| Cap. 5          | §5.2 (hash)              | 95–100, 116, 120               | ✓                                                 |
| Cap. 6          | §6.3                     | 121–123                        | ✓                                                 |
| Cap. 7          | §7.1                     | 127                            | ✓                                                 |
| Cap. 7          | §7.2                     | 124–125                        | ✓                                                 |
| Cap. 7          | §7.3                     | 127–128                        | ✓                                                 |
| Cap. 7          | §7.4                     | 124–126                        | ✓                                                 |
| Cap. 7          | §7.5 (N-Queens)          | 134                            | ✓                                                 |
| Cap. 7          | §7.6 (Sudoku)            | 135–136                        | ✓                                                 |
| Cap. 7          | Riepilogo                | 124–135, ◆=124,125,126,127,134 | ✓                                                 |
| Cap. 8          | §8.2 (stringhe)          | 137–139                        | ✓                                                 |
| Cap. 8          | §8.3 (stream)            | nessuno esplicito              | Gap (vedi sopra)                                  |
| Cap. 8          | §8.6 (RPN)               | 142                            | ✓                                                 |
| Cap. 8          | §8.7 (mini-eval)         | 143–144                        | ✓                                                 |
| Cap. 8          | Riepilogo                | 137–144, ◆=137,138,142,143,144 | ✓                                                 |

### 5.2 Problemi di coerenza identificati

**CRITICO — Nomi di funzione discordanti tra esercizio e soluzione:**

- **Es. 52**: esercizio chiede `reverse*`, soluzione nomina la funzione `reverse-tr`. Il test `(reverse* '(a b c d)) ; -> (D C B A)` fallirebbe con la soluzione così com'è.

**POTENZIALMENTE PROBLEMATICO — Funzioni usate prima di essere introdotte:**

- Es. 46 usa `mapcar` prima che sia introdotto nel cap. 4.
- Es. 64 usa `isqrt` che non compare né nella teoria né in nessun suggerimento esplicito.
- Es. 66 soluzione usa `nth` in loop O(n²) mentre la spiegazione descrive un approccio diverso.

**LIEVI — Rimandi incrociati migliorabili:**

- Il testo teorico cap. 3 accenna al Crivello (es. 64) nella sezione degli array, ma il rimando non è nel box workbook di quella sezione.
- Il testo teorico cap. 7 parla di `memoize` rimandando all'Appendice ADT, ma la funzione è già negli es. 91.
- Nel testo teorico cap. 9, l'esercizio 148 viene descritta come usando concetti del cap. 8 (with-open-file, read, write), ma questi non hanno esercizi dedicati prima del 148.

### 5.3 Verifiche output esercizi/soluzioni

Gli output campionati corrispondono alle soluzioni:

| Esercizio                           | Output atteso           | Output soluzione            | Match                          |
| ----------------------------------- | ----------------------- | --------------------------- | ------------------------------ |
| 1: `(add 3 5)`                      | `8`                     | `(+ a b)` → 8               | ✓                              |
| 4: `(ipotenusa 3 4)`                | `5.0`                   | `(sqrt (+ a2 b2))` → 5.0    | ✓                              |
| 6: `(pari-p 8)`                     | `T`                     | `(= (mod n 2) 0)` → T       | ✓                              |
| 11: `(bisestile-p 1900)`            | `NIL`                   | logica `(or (and ...) ...)` | ✓                              |
| 15: `(radici-quadratiche 1 -5 6)`   | `(3.0 2.0)`             | formula corretta            | ✓                              |
| 27: `(length* '(a b c))`            | `3`                     | ricorsione                  | ✓                              |
| 31: `(member* 'b '(a b c))`         | `T`                     | restituisce `t` (non coda)  | ⚠ diverge da `member` built-in |
| 39: `(reverse* '(a b c d))`         | `(D C B A)`             | accumulatore                | ✓                              |
| 51: `(fattoriale 5)`                | `120`                   | labels + acc                | ✓                              |
| 54: `(fibonacci-fast 50)`           | `12586269025`           | doppio acc                  | ✓                              |
| 55: `(flatten* '(a (b (c d) e) f))` | `(A B C D E F)`         | ricorsione albero           | ✓                              |
| 64: `(crivello 20)`                 | `(2 3 5 7 11 13 17 19)` | loop sieve                  | ✓                              |

**Nota sull'es. 31**: `member*` restituisce `T` o `NIL` (booleano puro), mentre il built-in `member` restituisce la coda della lista o NIL. Questo è dichiarato nell'esercizio ("senza usare `member`") e nella nota della teoria ("member non restituisce T o NIL"). La soluzione è coerente con se stessa, ma diverge dalla semantica del built-in. Un commento esplicito nella soluzione sarebbe opportuno per chi poi usa `member` in codice reale.

---

## 6. Correttezza tecnica

### 6.1 Errori tecnici confermati

**ERRORE — Es. 52, nome funzione:**
La soluzione implementa `reverse-tr` ma l'esercizio chiede `reverse*`. Il test `(reverse* '(a b c d)) ; -> (D C B A)` fallirà. Da correggere.

**IMPRECISIONE — Cap. 2, output `type-of`:**
`(type-of 42) ; => INTEGER` — in quasi tutte le implementazioni CL concrete (incluso Allegro CL), il risultato è `FIXNUM` non `INTEGER`. La distinzione non è errata (FIXNUM è sottotipo di INTEGER) ma l'output come mostrato non corrisponde a quello che lo studente vede nel REPL.

**IMPRECISIONE — Cap. 2, `char-digit-p`:**
`(char-digit-p #\5) ; => 5` — questo è corretto (restituisce il valore numerico, non solo T), ma non è mai introdotto esplicitamente.

**INCOERENZA — Es. 46, soluzione con mapcar anticipato:**
La soluzione `(mapcar #'car alist)` usa `mapcar` prima della sua introduzione formale nel cap. 4. Non è un errore tecnico ma un'incoerenza pedagogica.

**PROBLEMA POTENZIALE — Es. 66, complessità della soluzione:**
La soluzione usa `(nth i lst)` in un loop, risultando O(n²). La spiegazione descrive un approccio O(n). Da allineare.

### 6.2 Punti tecnici corretti ma da segnalare

- Il `mcm*` correttamente usa `(/ (* a b) (mcd* a b))`. Per valori grandi i bignum CL gestiscono senza overflow. ✓
- Il crivello usa `(isqrt n)` non `(sqrt n)`. Corretto — `sqrt` restituisce float. ✓
- `sort` nei listing è sempre preceduto da `copy-list`. Corretto. ✓
- `mapcan` avverte sul comportamento distruttivo. Corretto. ✓
- `*read-eval*` impostato a `nil` per input non fidato. Corretto e importante. ✓
- La formula MCM = (a\*b)/MCD è corretta. ✓
- N-Queens: `(length (n-queens 8)) = 92` è verificabile. ✓
- Fibonacci-fast(50) = 12586269025 è corretto. ✓
- Crivello(20) = (2 3 5 7 11 13 17 19) è corretto. ✓

---

## 7. Problemi stilistici e tipografici

### 7.1 Violazioni delle regole del progetto

**Em-dash nel testo:**

Nel file `02_funzioni_dati.tex`, l'intestazione del capitolo usa `---` nella stringa di commento LaTeX (`% Capitolo 2 --- Funzioni e dati fondamentali`). Questo è solo un commento e non appare nel PDF, ma viola la convenzione del progetto. Va verificato se appare nelle versioni precedenti di altri capitoli.

**Più significativo:** nel `main.tex` del workbook si trova `Prima edizione — Settembre 2026` nella tabella crediti. L'em-dash qui è usato come separatore in una voce tabella, non come inciso, quindi è borderline — ma per coerenza assoluta con la regola "l'unico uso legittimo è in celle di tabella per indicare assenza di valore", va sostituito.

**Unicode problematico potenziale:**

Il documento teorico usa `$\bigstar$` nel box workbook finale del cap. 1 (`Se hai difficolta' con un esercizio $\bigstar\bigstar\bigstar$`) — questo è il modo corretto (macro LaTeX). ✓

### 7.2 Incoerenze tipografiche minori

1. **Capitolo 5**: l'intuizione iniziale usa font size `\large\bfseries` per la prima frase del box ("Perche' tante strutture dati?"). Nessun altro capitolo fa questo. È una scelta stilistica ma crea incoerenza.

2. **Box `mnota` e `\detail`**: nei capitoli 1–4 i `\detail{}` sono usati sistematicamente come contorno/approfondimento nei box `concetto`. Nel cap. 7 (backtracking) alcuni `\detail{}` appaiono come commenti standalone fuori dai box, diversamente dagli altri capitoli.

3. **Apostrofo in listings**: la regola del progetto è "usare forme apostrofate (`e'`, `puo'`, `perche'`) dentro `lstlisting`". Questa regola è rispettata nella maggior parte dei listing. Ho trovato alcune eccezioni nel cap. 9 (sezione `fiveam`) ma non sistematiche.

4. **Stile dei box workbook**: nel cap. 1 il box finale usa `\textbf{Esercizi 1--4}` in grassetto; nel cap. 3 usa solo `\textbf{Esercizi 22--26}` senza enfasi aggiuntiva. Non è un errore ma è leggermente inconsistente.

5. **La guida Allegro CL** (`00b_ambiente.tex`) non è stata esaminata in questa revisione. Da verificare separatamente per coerenza con la versione di Allegro CL Free Express disponibile al momento della pubblicazione.

---

## 8. Omissioni e gap pedagogici

### 8.1 Gap nella teoria

| Argomento                               | Dove manca                     | Gravità                           |
| --------------------------------------- | ------------------------------ | --------------------------------- |
| `defstruct` con accessor automatici     | Cap. 5 non ha sezione dedicata | Alta                              |
| CLOS base (`defclass`, `defmethod`)     | Non trattato                   | Alta (richiesto dal prog. finale) |
| `char-digit-p`                          | Cap. 2 o cap. 8                | Media                             |
| `coerce` come operazione generale       | Cap. 8                         | Media                             |
| `mapc` come alternativa a `map nil`     | Cap. 8                         | Bassa                             |
| `handler-bind` + restart                | Cap. 9                         | Media                             |
| `define-condition`                      | Cap. 6 o 9                     | Media                             |
| Esercizio I/O su file prima di es. 148  | Cap. 8                         | Alta                              |
| Costo computazionale cons vs array      | Cap. 9                         | Bassa                             |
| `the` per type hints                    | Cap. 9                         | Bassa                             |
| `let` con sole variabili (senza valori) | Cap. 2                         | Bassa                             |

### 8.2 Gap nel workbook

| Argomento                       | Gap                           | Gravità |
| ------------------------------- | ----------------------------- | ------- |
| `and`/`or` come valori (idiomi) | Nessun esercizio dedicato     | Media   |
| `case` introdotto con pratica   | Es. 16 anticipa il costrutto  | Media   |
| CLOS                            | Nessun esercizio              | Alta    |
| `with-open-file` standalone     | Nessun esercizio prima di 148 | Alta    |
| `define-condition`              | Nessun esercizio              | Media   |
| `values`/`multiple-value-bind`  | Nessun esercizio esplicito    | Bassa   |

---

## 9. Ridondanze

1. **L'es. 72 (somma con reduce) e l'es. 28 (somma degli elementi)** fanno la stessa cosa con strumenti diversi. Questo è intenzionale e didatticamente corretto (il confronto è il punto). Ma la nota nell'es. 72 non rimanda esplicitamente all'es. 28 per confronto. Un cross-reference avrebbe valore pedagogico.

2. **`circle-area` appare sia nell'es. 2 del workbook che come esempio nel cap. 2 della teoria** (nella sezione sulla tipizzazione dinamica si usa `pi`). Non è una ridondanza problematica, ma i due contesti dovrebbero usare lo stesso nome di funzione.

3. **Il concetto di `structural sharing`** (le liste condividono la coda) appare nel cap. 3 della teoria (box attenzione su cons) e viene implicitamente richiamato nell'es. 40 (append), ma non è esplicitato nella nota in fondo all'es. 40 né nel suggerimento. Poiché è un concetto chiave per capire perché `append` è O(n), andrebbe citato esplicitamente almeno una volta nel workbook.

4. **Il pattern "genera sequenza binaria"** appare nel cap. 7 (sezione Stato) e nell'es. 128 (genera-parentesi). Il collegamento non è esplicitato ma entrambi usano lo stesso schema "due scelte per passo". Non è una ridondanza problematica ma un'occasione di rinforzo perduta.

5. **La funzione `fibonacci-fast`** è implementata sia nel cap. 3 della teoria (sezione accumulatori avanzati) che nell'es. 54 del workbook. Corretto, ma il testo teorico mostra già la soluzione completa, riducendo la sfida dell'esercizio per chi legge la teoria prima. Un'alternativa: mostrare solo il concetto (i due accumulatori) nella teoria e lasciare l'implementazione all'esercizio. Ma questo è una scelta editoriale, non un errore.

---

## 10. Priorità di intervento

### Priorità 1 — Da correggere prima della pubblicazione

1. **Es. 52**: rinominare `reverse-tr` in `reverse*` nella soluzione (o viceversa, uniformando esercizio e soluzione).
2. **Es. 46**: la soluzione con `mapcar` anticipa il cap. 4. Richiedere una soluzione ricorsiva esplicita coerente col livello del capitolo, o spostare l'esercizio nel cap. 4.
3. **Cap. 2**: aggiungere nota su `(type-of 42)` → `FIXNUM` vs `INTEGER` o correggere l'output del listing.
4. **Es. 66 soluzione**: allineare l'approccio della soluzione (O(n) con `nthcdr`) con la descrizione dell'esercizio.
5. **Cap. 8**: rimuovere la nota "fuori posto" su `ignore-errors` nella sezione RPN.
6. **Es. 64 suggerimento**: esplicitare che si usa `isqrt` non `sqrt`.

### Priorità 2 — Da aggiungere prima della pubblicazione

1. **Cap. 5**: aggiungere sezione su `defstruct` con accessor generati, costruttore, predicato.
2. **Cap. 8 / workbook**: aggiungere almeno un esercizio su `with-open-file` (lettura/scrittura semplice) prima del progetto finale.
3. **Es. 79**: aggiungere vincolo esplicito "la lambda deve restituire liste fresche, non quoted".
4. **Cap. 3 / es. 64**: aggiungere nota esplicita che il crivello anticipa gli array del cap. 5.

### Priorità 3 — Miglioramenti significativi

1. **Cap. 5**: aggiungere almeno un paragrafo introduttivo su CLOS (o uno stdbox nell'esercizio 107).
2. **Cap. 7**: chiarire che l'es. 131 (Hanoi) è ricorsione divide-and-conquer, non backtracking.
3. **Cap. 9 teoria**: espandere la sezione su profiling e ottimizzazione con concetti di base (tail-call, costo cons, uso di `the`).
4. **Cross-reference es. 72 → es. 28**: aggiungere rimando esplicito per confronto reduce vs ricorsione esplicita.
5. **Nota tail recursion (workbook)**: spostare prima degli esercizi che la referenziano, non dopo.

### Priorità 4 — Desiderabili

1. CLOS con esercizio dedicato (almeno uno stdbox).
2. `define-condition` con esercizio.
3. `handler-bind` con rimando alla differenza da `handler-case`.
4. Esercizio su `values`/`multiple-value-bind`.
5. Note su `rem` vs `mod` (trappola per chi viene da C) nel cap. 2.

---

## Conclusioni

Il progetto è ben concepito e coraggioso nella sua ambizione: coprire Common Lisp dal modello mentale iniziale al progetto professionale in due volumi coordinati. La progressione pedagogica è solida e la filosofia "funzionale prima, poi il resto" è applicata in modo coerente e bilanciato (senza cadere nel dogmatismo).

I problemi rilevati sono quasi tutti locali e correggibili senza ristrutturare nulla. L'unica lacuna strutturale significativa è l'assenza di una trattazione anche minimale di CLOS, dato che il progetto finale la richiede esplicitamente.

La qualità tecnica del codice nei listing è alta: gli algoritmi sono corretti, gli output verificano, le soluzioni sono spesso idiomatiche (e segnalano quando scelgono uno stile imperativo e perché). L'unico errore tecnico diretto è il nome discordante nell'es. 52.

Il volume teorico eccelle nel capitolo 4 (Higher-order e closure) e nel capitolo 7 (Backtracking). Il capitolo 5 (Strutture dati) è il più debole per le lacune su defstruct e CLOS. Nel workbook, gli esercizi più riusciti sono 54 (Fibonacci O(n)), 85 (compose), 87 (make-counter) e 143–144 (evaluator).

Con le correzioni di priorità 1 e 2, il progetto è pronto per la pubblicazione. Le priorità 3 e 4 ne aumenterebbero significativamente la completezza per una seconda edizione.

---

_Fine documento — Kiro, settembre 2026_
