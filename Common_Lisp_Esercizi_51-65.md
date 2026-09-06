# Common Lisp
## Esercizi 51–65

**Legenda:** ★ facile · ★★ medio · ★★★ difficile · ★★★★ avanzato · ★★★★★ progetto

---

# 4. Higher-order e programmazione funzionale

Da questo punto le funzioni vengono trattate anche come **dati**: possono essere passate come argomenti, restituite da altre funzioni e combinate.

---

## Esercizio 51 — Quadrato degli elementi ★

Implementare:

```lisp
(square-list lst)
```

che restituisce una nuova lista contenente il quadrato di ogni elemento.

```lisp
(square-list '(1 2 3 4))
; → (1 4 9 16)
```

**Vincolo:** utilizzare `mapcar`.

---

## Esercizio 52 — Filtra i pari ★

Implementare:

```lisp
(even-list lst)
```

che restituisce soltanto i numeri pari.

```lisp
(even-list '(1 2 3 4 5 6))
; → (2 4 6)
```

**Vincolo:** utilizzare `remove-if-not` e `evenp`.

---

## Esercizio 53 — Filtro generico ★★

Implementare:

```lisp
(filter-list predicate lst)
```

che restituisce gli elementi per i quali `predicate` è vero.

```lisp
(filter-list #'evenp '(1 2 3 4 5))
; → (2 4)
```

**Vincolo:** utilizzare una funzione di ordine superiore della libreria standard.

---

## Esercizio 54 — Conta con predicato ★★

Implementare:

```lisp
(count-matching predicate lst)
```

che conta gli elementi che soddisfano `predicate`.

```lisp
(count-matching #'evenp '(1 2 3 4 5))
; → 2
```

**Vincolo:** utilizzare `count-if`.

---

## Esercizio 55 — Cerca con predicato ★★

Implementare:

```lisp
(find-matching predicate lst)
```

che restituisce il primo elemento che soddisfa `predicate`, oppure `NIL`.

```lisp
(find-matching #'evenp '(1 3 5 8 10))
; → 8
```

**Vincolo:** utilizzare `find-if`.

---

## Esercizio 56 — Trasforma e filtra ★★

Implementare:

```lisp
(square-even-numbers lst)
```

che:

1. seleziona i numeri pari;
2. ne calcola il quadrato.

```lisp
(square-even-numbers '(1 2 3 4 5))
; → (4 16)
```

**Vincolo:** utilizzare almeno `remove-if-not` e `mapcar`.

---

## Esercizio 57 — Somma con reduce ★★

Implementare:

```lisp
(sum-reduce lst)
```

utilizzando `reduce`.

```lisp
(sum-reduce '(1 2 3 4))
; → 10

(sum-reduce '())
; → 0
```

---

## Esercizio 58 — Prodotto con reduce ★★

Implementare:

```lisp
(product-reduce lst)
```

utilizzando `reduce`.

```lisp
(product-reduce '(2 3 4))
; → 24

(product-reduce '())
; → 1
```

---

## Esercizio 59 — Minimo e massimo generici ★★★

Implementare:

```lisp
(reduce-min lst)
(reduce-max lst)
```

utilizzando `reduce`.

```lisp
(reduce-min '(8 3 5 1 9))
; → 1

(reduce-max '(8 3 5 1 9))
; → 9
```

Gestire il caso della lista vuota.

---

## Esercizio 60 — Composizione di funzioni ★★★

Implementare:

```lisp
(compose f g)
```

che restituisce una funzione equivalente a:

```text
x → f(g(x))
```

Esempio:

```lisp
(defparameter *f*
  (compose #'1+ #'1+))

(funcall *f* 10)
; → 12
```

La funzione restituita deve essere una **closure**.

---

## Esercizio 61 — Map generalizzato ★★★

Implementare:

```lisp
(map-list* function lst)
```

che applica `function` a tutti gli elementi della lista.

Esempio:

```lisp
(map-list* #'square '(1 2 3))
; → (1 4 9)
```

**Vincolo:** utilizzare `mapcar`.

L'obiettivo è creare una piccola astrazione sopra una funzione standard.

---

## Esercizio 62 — Pipeline ★★★

Implementare:

```lisp
(pipeline value functions)
```

che applica sequenzialmente una lista di funzioni.

Esempio:

```lisp
(pipeline 5
          (list #'1+
                #'1+
                (lambda (x) (* x 2))))
; → 14
```

Calcolo:

```text
5 → 6 → 7 → 14
```

**Vincolo:** utilizzare `funcall`.

---

## Esercizio 63 — Partial application ★★★

Implementare:

```lisp
(partial function &rest arguments)
```

che restituisce una nuova funzione con alcuni argomenti già fissati.

Esempio:

```lisp
(defparameter *add10*
  (partial #'+ 10))

(funcall *add10* 5)
; → 15

(funcall *add10* 20)
; → 30
```

La funzione restituita deve essere una closure.

---

## Esercizio 64 — Memoization ★★★★

Implementare:

```lisp
(memoize function)
```

che restituisce una nuova funzione che memorizza i risultati già calcolati.

Esempio:

```lisp
(defparameter *fib*
  (memoize #'fibonacci))
```

Chiamate successive con lo stesso argomento devono riutilizzare il risultato memorizzato.

**Vincoli:**

- utilizzare una hash table;
- la funzione originale non deve essere modificata;
- la cache deve appartenere alla closure restituita.

---

## Esercizio 65 — Mini libreria funzionale ★★★★

Realizzare una piccola libreria che contenga almeno:

```lisp
(map-list* function lst)
(filter-list predicate lst)
(count-matching predicate lst)
(find-matching predicate lst)
(compose f g)
(partial function &rest arguments)
```

Aggiungere almeno **tre** ulteriori funzioni a scelta.

### Requisiti

- ogni funzione deve avere una docstring;
- evitare stato globale non necessario;
- utilizzare le funzioni di ordine superiore della libreria standard quando appropriate;
- aggiungere almeno un test per ogni funzione.

Esempio:

```lisp
(map-list* #'1+ '(1 2 3))
; → (2 3 4)
```

**Obiettivo:** passare dalla risoluzione di singoli esercizi alla progettazione di una piccola API coerente.
