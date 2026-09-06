# Common Lisp
## Esercizi 1–30

**Legenda:** ★ facile · ★★ medio · ★★★ difficile · ★★★★ avanzato · ★★★★★ progetto

---

# 1. Fondamenti

## Esercizio 1 — Somma ★

Implementare:

```lisp
(add a b)
```

che restituisce la somma di `a` e `b`.

Esempi:

```lisp
(add 3 5)       ; → 8
(add -2 7)      ; → 5
(add 1.5 2.5)   ; → 4.0
```

---

## Esercizio 2 — Geometria ★

Implementare:

```lisp
(circle-area radius)
(circle-circumference radius)
```

Usare `pi` come valore di π.

Esempio:

```lisp
(circle-area 2)
; → 12.566...
```

---

## Esercizio 3 — Conversione Celsius/Fahrenheit ★

Implementare:

```lisp
(celsius-to-fahrenheit c)
(fahrenheit-to-celsius f)
```

Formule:

```text
F = C × 9/5 + 32
C = (F − 32) × 5/9
```

---

## Esercizio 4 — Pari o dispari ★

Implementare:

```lisp
(even-number-p n)
(odd-number-p n)
```

che restituiscono `T` o `NIL`.

Esempi:

```lisp
(even-number-p 8)   ; → T
(even-number-p 7)   ; → NIL
```

---

## Esercizio 5 — Massimo di due numeri ★

Implementare:

```lisp
(max2 a b)
```

senza utilizzare la funzione built-in `max`.

```lisp
(max2 7 3)    ; → 7
(max2 2 9)    ; → 9
(max2 5 5)    ; → 5
```

---

## Esercizio 6 — Massimo di tre numeri ★

Implementare:

```lisp
(max3 a b c)
```

**Vincolo:** utilizzare `cond`.

---

## Esercizio 7 — Segno ★

Implementare:

```lisp
(sign-of n)
```

Risultato:

```text
-1    se n < 0
 0    se n = 0
 1    se n > 0
```

Esempi:

```lisp
(sign-of -7)   ; → -1
(sign-of 0)    ; → 0
(sign-of 12)   ; → 1
```

---

## Esercizio 8 — Valore assoluto ★

Implementare:

```lisp
(abs-value n)
```

senza utilizzare `abs`.

---

## Esercizio 9 — Potenza ★★

Implementare:

```lisp
(power base exponent)
```

con `exponent ≥ 0`.

```lisp
(power 2 10)   ; → 1024
(power 5 0)    ; → 1
```

**Vincolo:** utilizzare la ricorsione.

---

## Esercizio 10 — Fattoriale ★★

Implementare:

```lisp
(factorial n)
```

con `n ≥ 0`.

```lisp
(factorial 0)   ; → 1
(factorial 5)   ; → 120
```

**Vincolo:** soluzione ricorsiva.

---

## Esercizio 11 — Fibonacci ★★

Implementare:

```lisp
(fibonacci n)
```

definita da:

```text
F(0) = 0
F(1) = 1
F(n) = F(n-1) + F(n-2)
```

Esempio:

```lisp
(fibonacci 10)   ; → 55
```

**Vincolo:** soluzione ricorsiva diretta.

---

## Esercizio 12 — MCD ★★

Implementare:

```lisp
(gcd* a b)
```

utilizzando l'algoritmo di Euclide:

```text
gcd(a,b) = gcd(b, a mod b)
```

Esempio:

```lisp
(gcd* 48 18)   ; → 6
```

---

## Esercizio 13 — Numero primo ★★

Implementare:

```lisp
(prime-p n)
```

che restituisce `T` se `n` è primo.

```lisp
(prime-p 2)    ; → T
(prime-p 17)   ; → T
(prime-p 18)   ; → NIL
```

Gestire correttamente `0` e `1`.

---

## Esercizio 14 — Fattori primi ★★★

Implementare:

```lisp
(prime-factors n)
```

che restituisce la lista dei fattori primi di `n`.

```lisp
(prime-factors 60)
; → (2 2 3 5)
```

**Vincoli:**

- `n > 1`;
- risultato ordinato;
- utilizzare una soluzione iterativa o ricorsiva.

---

## Esercizio 15 — Calcolatrice interattiva ★★

Realizzare una funzione:

```lisp
(calculator)
```

che:

1. legge due numeri;
2. legge un operatore (`+`, `-`, `*`, `/`);
3. visualizza il risultato.

Esempio d'interazione:

```text
First number: 12
Operator: *
Second number: 4
Result: 48
```

Gestire almeno la divisione per zero.

---

# 2. Liste

Da questo punto **non utilizzare le funzioni built-in che risolvono direttamente l'esercizio**, salvo diversa indicazione.

---

## Esercizio 16 — Primo elemento ★

Implementare:

```lisp
(first-element lst)
```

senza utilizzare `first`.

```lisp
(first-element '(a b c))   ; → A
```

Gestire la lista vuota.

---

## Esercizio 17 — Resto della lista ★

Implementare:

```lisp
(rest-elements lst)
```

senza utilizzare `rest`.

```lisp
(rest-elements '(a b c))   ; → (B C)
```

---

## Esercizio 18 — Inserimento in testa ★

Implementare:

```lisp
(prepend item lst)
```

senza utilizzare direttamente `cons`.

Esempio:

```lisp
(prepend 'a '(b c))
; → (A B C)
```

**Obiettivo:** capire la rappresentazione delle liste e il ruolo di `cons`.

---

## Esercizio 19 — Lunghezza di una lista ★★

Implementare:

```lisp
(length* lst)
```

senza utilizzare `length`.

```lisp
(length* '())       ; → 0
(length* '(a b c))  ; → 3
```

**Vincolo:** ricorsione.

---

## Esercizio 20 — Somma degli elementi ★★

Implementare:

```lisp
(sum-list lst)
```

```lisp
(sum-list '(1 2 3 4))   ; → 10
(sum-list '())          ; → 0
```

**Vincolo:** ricorsione.

---

## Esercizio 21 — Prodotto degli elementi ★★

Implementare:

```lisp
(product-list lst)
```

```lisp
(product-list '(2 3 4))   ; → 24
(product-list '())        ; → 1
```

---

## Esercizio 22 — Massimo di una lista ★★

Implementare:

```lisp
(max-list lst)
```

Esempio:

```lisp
(max-list '(4 8 2 9 1))
; → 9
```

Specificare il comportamento per la lista vuota.

---

## Esercizio 23 — Conta occorrenze ★★

Implementare:

```lisp
(count-element item lst)
```

```lisp
(count-element 'a '(a b a c a))
; → 3
```

**Vincolo:** non utilizzare `count`.

---

## Esercizio 24 — Appartenenza ★★

Implementare:

```lisp
(member* item lst)
```

che restituisce `T` se `item` appartiene alla lista.

```lisp
(member* 'b '(a b c))   ; → T
(member* 'x '(a b c))   ; → NIL
```

**Vincolo:** non utilizzare `member`.

---

## Esercizio 25 — Posizione ★★

Implementare:

```lisp
(position* item lst)
```

che restituisce l'indice della prima occorrenza oppure `NIL`.

```lisp
(position* 'c '(a b c d))   ; → 2
(position* 'x '(a b c d))   ; → NIL
```

Gli indici partono da `0`.

---

## Esercizio 26 — Ultimo elemento ★★

Implementare:

```lisp
(last-element lst)
```

senza utilizzare `last`.

```lisp
(last-element '(a b c))
; → C
```

Definire il comportamento per `NIL`.

---

## Esercizio 27 — Penultimo elemento ★★

Implementare:

```lisp
(penultimate lst)
```

```lisp
(penultimate '(a b c d))
; → C
```

Gestire liste troppo corte.

---

## Esercizio 28 — Reverse ★★

Implementare:

```lisp
(reverse* lst)
```

senza utilizzare `reverse`.

```lisp
(reverse* '(a b c d))
; → (D C B A)
```

Prima realizzare una versione ricorsiva semplice.

---

## Esercizio 29 — Append ★★★

Implementare:

```lisp
(append* lst1 lst2)
```

senza utilizzare `append`.

```lisp
(append* '(a b) '(c d))
; → (A B C D)
```

**Vincolo:** non modificare le liste originali.

---

## Esercizio 30 — Rimozione di un elemento ★★★

Implementare:

```lisp
(remove-first item lst)
```

che elimina **soltanto la prima occorrenza** di `item`.

```lisp
(remove-first 'b '(a b c b d))
; → (A C B D)
```

Se l'elemento non è presente, restituire una lista equivalente all'originale.

**Vincoli:**

- non utilizzare `remove`;
- non modificare la lista originale;
- usare ricorsione.
