# Common Lisp
## Esercizi 66–100

**Legenda:** ★ facile · ★★ medio · ★★★ difficile · ★★★★ avanzato · ★★★★★ progetto

---

# 5. Associazioni, hash table e dati strutturati

## Esercizio 66 — Association list ★★

Implementare:

```lisp
(lookup key alist)
```

che restituisce il valore associato a `key`.

```lisp
(lookup 'age '((name . "Mario") (age . 23)))
; → 23
```

Se la chiave non esiste, restituire `NIL`.

**Vincolo:** utilizzare `assoc`.

---

## Esercizio 67 — Aggiornamento di una association list ★★

Implementare:

```lisp
(set-key key value alist)
```

che aggiorna il valore di una chiave oppure la aggiunge.

```lisp
(set-key 'age 24 '((name . "Mario") (age . 23)))
; → ((NAME . "Mario") (AGE . 24))
```

Non modificare la lista originale.

---

## Esercizio 68 — Frequenza degli elementi ★★★

Implementare:

```lisp
(frequencies lst)
```

che restituisce una association list contenente il numero di occorrenze di ogni elemento.

```lisp
(frequencies '(a b a c b a))
; → ((A . 3) (B . 2) (C . 1))
```

---

## Esercizio 69 — Frequenze con hash table ★★★

Riscrivere l'esercizio precedente utilizzando una hash table.

Implementare:

```lisp
(frequencies-hash lst)
```

**Obiettivo:** confrontare l'approccio con association list e hash table.

---

## Esercizio 70 — Rubrica ★★★

Realizzare una rubrica utilizzando una hash table.

Implementare almeno:

```lisp
(add-contact name phone)
(find-contact name)
(remove-contact name)
(list-contacts)
```

Esempio:

```lisp
(add-contact "Mario" "3331234567")
(find-contact "Mario")
; → "3331234567"
```

---

# 6. Stringhe

## Esercizio 71 — Inverti una stringa ★★

Implementare:

```lisp
(reverse-string string)
```

```lisp
(reverse-string "hello")
; → "olleh"
```

**Vincolo:** non utilizzare `reverse` direttamente sulla stringa.

---

## Esercizio 72 — Palindromo ★★

Implementare:

```lisp
(palindrome-p string)
```

```lisp
(palindrome-p "anna")
; → T

(palindrome-p "casa")
; → NIL
```

---

## Esercizio 73 — Palindromo robusto ★★★

Estendere l'esercizio precedente:

- ignorare maiuscole/minuscole;
- ignorare spazi;
- ignorare la punteggiatura.

```lisp
(palindrome-p* "I topi non avevano nipoti")
; → T
```

---

## Esercizio 74 — Conta caratteri ★★

Implementare:

```lisp
(count-char char string)
```

che conta quante volte compare `char`.

```lisp
(count-char #\a "banana")
; → 3
```

---

## Esercizio 75 — Anagrammi ★★★

Implementare:

```lisp
(anagram-p string1 string2)
```

che verifica se due stringhe sono anagrammi.

```lisp
(anagram-p "roma" "amor")
; → T
```

Ignorare maiuscole/minuscole.

---

# 7. Funzioni e closure

## Esercizio 76 — Contatore ★★★

Implementare:

```lisp
(make-counter)
```

che restituisce una funzione.

Esempio:

```lisp
(defparameter *counter* (make-counter))

(funcall *counter*)  ; → 1
(funcall *counter*)  ; → 2
(funcall *counter*)  ; → 3
```

**Obiettivo:** comprendere le closure e lo stato incapsulato.

---

## Esercizio 77 — Contatore configurabile ★★★

Implementare:

```lisp
(make-counter &optional start step)
```

Esempio:

```lisp
(defparameter *counter*
  (make-counter 10 5))

(funcall *counter*)  ; → 10
(funcall *counter*)  ; → 15
(funcall *counter*)  ; → 20
```

---

## Esercizio 78 — Generatore di ID ★★★

Implementare:

```lisp
(make-id-generator prefix)
```

che restituisce una funzione capace di generare identificativi progressivi.

Esempio:

```lisp
(defparameter *id*
  (make-id-generator "USER"))

(funcall *id*)  ; → "USER-1"
(funcall *id*)  ; → "USER-2"
(funcall *id*)  ; → "USER-3"
```

---

## Esercizio 79 — Validatore ★★★

Implementare:

```lisp
(make-validator predicate message)
```

che restituisce una funzione di validazione.

Esempio:

```lisp
(defparameter *positive*
  (make-validator #'plusp "Must be positive"))

(funcall *positive* 10)
; → T

(funcall *positive* -2)
; → NIL
```

---

## Esercizio 80 — Composizione multipla ★★★★

Implementare:

```lisp
(compose-many functions)
```

che compone una lista arbitraria di funzioni.

```lisp
(defparameter *f*
  (compose-many
    (list #'1+
          (lambda (x) (* x 2))
          #'1+)))

(funcall *f* 3)
; → 9
```

Definire chiaramente l'ordine di applicazione.

---

# 8. Alberi

## Esercizio 81 — Albero binario ★★★

Definire:

```lisp
(defstruct tree
  value
  left
  right)
```

e implementare:

```lisp
(make-leaf value)
(make-node value left right)
```

Costruire manualmente un piccolo albero.

---

## Esercizio 82 — Attraversamento preorder ★★★

Implementare:

```lisp
(preorder tree)
```

Esempio:

```text
       A
      / \
     B   C
    / \
   D   E
```

Risultato:

```lisp
(A B D E C)
```

---

## Esercizio 83 — Inorder ★★★

Implementare:

```lisp
(inorder tree)
```

Per l'albero precedente:

```lisp
(D B E A C)
```

---

## Esercizio 84 — Postorder ★★★

Implementare:

```lisp
(postorder tree)
```

Per l'albero precedente:

```lisp
(D E B C A)
```

---

## Esercizio 85 — Altezza dell'albero ★★★

Implementare:

```lisp
(tree-height tree)
```

Esempio:

```text
       A
      / \
     B   C
    /
   D
```

Risultato:

```text
3
```

---

## Esercizio 86 — Albero binario di ricerca ★★★★

Implementare:

```lisp
(bst-insert value tree)
(bst-find value tree)
```

utilizzando un **Binary Search Tree**.

Per ogni nodo:

```text
sinistra < nodo < destra
```

Esempio:

```lisp
(bst-find 7 tree)
; → T
```

---

## Esercizio 87 — Ordinamento tramite BST ★★★★

Implementare:

```lisp
(tree-sort lst)
```

1. inserire tutti gli elementi in un BST;
2. eseguire un attraversamento inorder.

```lisp
(tree-sort '(7 2 9 1 5 3))
; → (1 2 3 5 7 9)
```

---

# 9. Backtracking e ricerca

## Esercizio 88 — Sottoinsiemi ★★★

Implementare:

```lisp
(subsets lst)
```

che genera tutti i sottoinsiemi di una lista.

```lisp
(subsets '(a b))
; → (() (B) (A) (A B))
```

L'ordine non è vincolante.

---

## Esercizio 89 — Permutazioni ★★★★

Implementare:

```lisp
(permutations lst)
```

che genera tutte le permutazioni.

```lisp
(permutations '(a b c))
```

deve produrre 6 permutazioni.

---

## Esercizio 90 — Problema dello zaino ★★★★

Dato un insieme di oggetti:

```text
peso      valore
2         3
3         4
4         5
5         8
```

e una capacità massima, implementare:

```lisp
(knapsack items capacity)
```

che restituisce una soluzione di valore massimo.

Per la prima versione è ammessa una soluzione tramite ricerca esaustiva.

---

## Esercizio 91 — Labirinto ★★★★

Rappresentare un labirinto come matrice.

Implementare:

```lisp
(find-path maze start goal)
```

che trova un percorso tra `start` e `goal`.

Restituire la sequenza delle coordinate visitate.

**Vincoli:**

- evitare celle già visitate;
- non attraversare muri;
- utilizzare backtracking.

---

## Esercizio 92 — Sudoku ★★★★★

Implementare un risolutore di Sudoku 9×9.

```lisp
(solve-sudoku board)
```

Il programma deve:

1. trovare una cella vuota;
2. provare i valori possibili;
3. verificare i vincoli;
4. procedere ricorsivamente;
5. tornare indietro in caso di conflitto.

---

## Esercizio 93 — N regine ★★★★★

Implementare:

```lisp
(n-queens n)
```

che restituisce tutte le configurazioni valide per `n` regine.

Esempio:

```lisp
(n-queens 4)
```

deve produrre 2 soluzioni.

**Vincoli:**

- utilizzare backtracking;
- non provare configurazioni già chiaramente impossibili;
- rappresentare una soluzione in modo compatto.

---

# 10. Grafi

## Esercizio 94 — Grafo come adjacency list ★★★

Rappresentare un grafo tramite association list:

```lisp
'((a b c)
  (b a d)
  (c a d)
  (d b c))
```

Implementare:

```lisp
(neighbors node graph)
```

---

## Esercizio 95 — DFS ★★★★

Implementare:

```lisp
(dfs graph start)
```

che visita il grafo in profondità.

Restituire la lista dei nodi visitati.

Gestire i cicli tramite un insieme di nodi già visitati.

---

## Esercizio 96 — BFS ★★★★

Implementare:

```lisp
(bfs graph start)
```

che visita il grafo in ampiezza.

**Vincolo:** utilizzare una coda.

---

## Esercizio 97 — Percorso minimo non pesato ★★★★

Implementare:

```lisp
(shortest-path graph start goal)
```

utilizzando BFS.

Restituire il percorso:

```lisp
(A B D F)
```

e non soltanto la distanza.

---

# 11. Parsing e interprete

## Esercizio 98 — Calcolatore di espressioni ★★★★

Implementare:

```lisp
(evaluate-expression expression)
```

per valutare espressioni aritmetiche rappresentate come liste:

```lisp
'(+ 2 3)
'(* 4 (+ 2 3))
'(- 10 4)
'(/ 20 5)
```

Esempio:

```lisp
(evaluate-expression '(* 4 (+ 2 3)))
; → 20
```

**Vincolo:** non utilizzare `eval`.

---

## Esercizio 99 — Mini-interprete ★★★★★

Estendere l'esercizio precedente introducendo:

```text
+  -  *  /
```

variabili:

```lisp
(set x 10)
```

e riferimenti:

```lisp
(+ x 5)
```

Implementare un ambiente separato dal normale ambiente Lisp.

**Vincolo:** non utilizzare `eval`.

---

# 12. Progetto finale

## Esercizio 100 — Mini sistema gestionale ★★★★★

Realizzare un piccolo programma completo in Common Lisp.

Il programma deve gestire una collezione di entità a scelta, ad esempio:

- studenti;
- libri;
- prodotti;
- film;
- contatti.

### Requisiti minimi

Utilizzare:

- `defstruct` o CLOS;
- liste o hash table;
- funzioni di ricerca;
- inserimento;
- modifica;
- eliminazione;
- filtraggio;
- ordinamento;
- input/output;
- gestione degli errori;
- salvataggio su file;
- caricamento da file.

### Requisiti progettuali

Separare almeno:

```text
MODEL
  ↓
LOGICA
  ↓
INPUT / OUTPUT
```

Il programma deve essere suddiviso in più funzioni coerenti.

Ogni funzione pubblica deve avere una docstring.

Aggiungere una piccola suite di test.

### Obiettivo

Non è richiesta un'interfaccia grafica.

Il risultato deve essere un piccolo programma **funzionante, organizzato e manutenibile**, non una semplice soluzione dimostrativa.
