# Common Lisp
## Esercizi 31–50

---

# 2. Liste — continua

## Esercizio 31 — Sostituzione di un elemento ★★

Implementare:

```lisp
(replace-first old new lst)
```

che sostituisce la prima occorrenza di `old` con `new`.

```lisp
(replace-first 'b 'x '(a b c b))
; → (A X C B)
```

Se `old` non è presente, restituire una lista equivalente all'originale.

**Vincoli:**

- non utilizzare `subst`;
- non modificare la lista originale;
- usare ricorsione.

---

## Esercizio 32 — Filtraggio ★★

Implementare:

```lisp
(filter-list predicate lst)
```

che restituisce gli elementi per i quali `predicate` restituisce vero.

```lisp
(filter-list #'evenp '(1 2 3 4 5 6))
; → (2 4 6)
```

**Vincoli:**

- non utilizzare `remove-if`;
- `predicate` deve essere una funzione passata come argomento;
- usare ricorsione.

---

## Esercizio 33 — Trasformazione ★★

Implementare:

```lisp
(map-list function lst)
```

che applica `function` a ogni elemento.

```lisp
(map-list #'1+ '(1 2 3))
; → (2 3 4)
```

**Vincoli:**

- non utilizzare `mapcar`;
- usare ricorsione.

---

## Esercizio 34 — Rimozione dei duplicati ★★★

Implementare:

```lisp
(remove-duplicates* lst)
```

che elimina le occorrenze duplicate mantenendo l'ordine della prima occorrenza.

```lisp
(remove-duplicates* '(a b a c b a))
; → (A B C)
```

**Vincoli:**

- non utilizzare `remove-duplicates`;
- non modificare la lista originale.

---

## Esercizio 35 — Pari e dispari ★★

Implementare:

```lisp
split-even-odd(lst)
```

che restituisce due liste:

```text
(even-list odd-list)
```

Esempio:

```lisp
(split-even-odd '(1 2 3 4 5 6))
; → ((2 4 6) (1 3 5))
```

**Vincolo:** effettuare una sola scansione della lista.

---

# 3. Liste annidate e ricorsione

## Esercizio 36 — Flatten ★★★

Una lista può contenere altre liste arbitrariamente annidate.

Implementare:

```lisp
(flatten* tree)
```

che restituisce una lista contenente tutti gli atomi nell'ordine originale.

```lisp
(flatten* '(a (b (c d) e) f))
; → (A B C D E F)
```

```lisp
(flatten* '((1 2) (3 (4 5))))
; → (1 2 3 4 5)
```

**Vincolo:** usare ricorsione.

---

## Esercizio 37 — Profondità ★★★

Implementare:

```lisp
(tree-depth tree)
```

che restituisce la profondità massima di una struttura annidata.

Esempi:

```lisp
(tree-depth '())             ; → 0
(tree-depth '(a b c))        ; → 1
(tree-depth '(a (b c)))      ; → 2
(tree-depth '(a (b (c d))))  ; → 3
```

---

## Esercizio 38 — Conta gli atomi ★★

Implementare:

```lisp
(count-atoms tree)
```

che conta tutti gli atomi presenti in una struttura arbitrariamente annidata.

```lisp
(count-atoms '(a (b c) ((d))))
; → 4
```

---

## Esercizio 39 — Somma di una struttura ★★

Implementare:

```lisp
(sum-tree tree)
```

che somma tutti gli elementi numerici contenuti nella struttura.

```lisp
(sum-tree '(1 (2 3) ((4 5))))
; → 15
```

**Assunzione:** la struttura contiene soltanto numeri e liste.

---

## Esercizio 40 — Ricerca in una struttura ★★★

Implementare:

```lisp
(tree-member-p item tree)
```

che verifica se `item` compare in una struttura arbitrariamente annidata.

```lisp
(tree-member-p 'c '(a (b c) d))
; → T

(tree-member-p 'x '(a (b c) d))
; → NIL
```

**Vincolo:** non utilizzare `tree-member` o equivalenti built-in.

---

# 4. Ricorsione avanzata

## Esercizio 41 — Potenza efficiente ★★★

Riscrivere:

```lisp
(power base exponent)
```

utilizzando l'esponenziazione per quadratura:

```text
xⁿ = (xⁿ/²)²          se n è pari

xⁿ = x · xⁿ⁻¹         se n è dispari
```

Esempio:

```lisp
(power-fast 2 10)
; → 1024
```

**Obiettivo:** ridurre la complessità da `O(n)` a `O(log n)`.

---

## Esercizio 42 — Fibonacci con accumulatore ★★★

Implementare:

```lisp
(fibonacci-fast n)
```

utilizzando un accumulatore o una coppia di valori per evitare il ricalcolo dei risultati già ottenuti.

```lisp
(fibonacci-fast 10)
; → 55
```

**Obiettivo:** ottenere complessità temporale `O(n)`.

---

## Esercizio 43 — Merge di liste ordinate ★★★

Implementare:

```lisp
(merge-sorted lst1 lst2)
```

che fonde due liste ordinate in un'unica lista ordinata.

```lisp
(merge-sorted '(1 3 5) '(2 4 6))
; → (1 2 3 4 5 6)
```

**Vincoli:**

- non utilizzare `sort`;
- non modificare le liste originali;
- usare ricorsione.

---

## Esercizio 44 — Merge sort ★★★★

Implementare:

```lisp
(merge-sort* lst)
```

utilizzando il merge sort.

```lisp
(merge-sort* '(7 2 9 1 5 3))
; → (1 2 3 5 7 9)
```

**Vincoli:**

- utilizzare `merge-sorted` dell'esercizio precedente;
- non utilizzare `sort`.

**Complessità attesa:** `O(n log n)`.

---

## Esercizio 45 — Quicksort ★★★★

Implementare:

```lisp
(quicksort* lst)
```

utilizzando ricorsivamente:

1. un pivot;
2. gli elementi minori del pivot;
3. gli elementi maggiori o uguali al pivot.

```lisp
(quicksort* '(7 2 9 1 5 3))
; → (1 2 3 5 7 9)
```

**Vincoli:**

- non utilizzare `sort`;
- usare ricorsione.

---

## Esercizio 46 — Ricerca binaria ★★★

Implementare:

```lisp
(binary-search item vector)
```

che cerca `item` in un vettore ordinato.

Restituire l'indice dell'elemento oppure `NIL`.

```lisp
(binary-search 7 #(1 3 5 7 9))
; → 3

(binary-search 4 #(1 3 5 7 9))
; → NIL
```

**Complessità attesa:** `O(log n)`.

---

## Esercizio 47 — Conta foglie ★★★

Considerare una struttura ad albero rappresentata tramite liste.

Implementare:

```lisp
(count-leaves tree)
```

che conta le foglie, cioè gli atomi contenuti nell'albero.

```lisp
(count-leaves '(a (b c) (d (e f))))
; → 6
```

**Vincolo:** soluzione ricorsiva.

---

## Esercizio 48 — Mappa su un albero ★★★

Implementare:

```lisp
(tree-map function tree)
```

che applica `function` a tutti gli atomi di una struttura mantenendo la struttura delle liste.

```lisp
(tree-map #'1+
          '(1 (2 3) (4 (5))))
```

Risultato:

```lisp
(2 (3 4) (5 (6)))
```

**Vincolo:** non utilizzare una funzione di libreria equivalente.

---

## Esercizio 49 — Confronto di strutture ★★★

Implementare:

```lisp
(tree-equal* tree1 tree2)
```

che verifica ricorsivamente se due strutture hanno la stessa forma e gli stessi valori.

```lisp
(tree-equal* '(a (b c)) '(a (b c)))
; → T

(tree-equal* '(a (b c)) '(a (c b)))
; → NIL
```

**Vincolo:** non utilizzare `equal`.

---

## Esercizio 50 — Tree walk generico ★★★★

Implementare:

```lisp
(tree-walk function tree)
```

che visita ricorsivamente tutti gli atomi dell'albero e applica `function` a ciascuno.

Esempio:

```lisp
(tree-walk #'print
           '(a (b c) (d (e))))
```

deve visitare:

```text
A
B
C
D
E
```

**Obiettivo:** separare l'algoritmo di attraversamento dall'operazione eseguita sugli elementi.