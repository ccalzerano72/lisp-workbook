# COMMON LISP
## Quick Reference

---

## 1. REPL e S-expression

Common Lisp utilizza **S-expression**:

```lisp
(+ 2 3)
(* 4 5)
(+ (* 2 3) 4)
```

Forma generale:

```lisp
(funzione argomento1 argomento2 ...)
```

Il primo elemento viene valutato come operatore/funzione; gli altri come argomenti.

```lisp
(+ 1 2 3)          ; → 6
(* 2 (+ 3 4))      ; → 14
```

Commento:

```lisp
; commento su una riga
```

```lisp
#| commento
   multilinea |#
```

---

# 2. Valori fondamentali

### Numeri

```lisp
42
-7
3.14
1/3
```

Operatori:

```lisp
(+ a b)
(- a b)
(* a b)
(/ a b)
(1+ x)
(1- x)
(mod a b)
(rem a b)
```

Confronti numerici:

```lisp
(= a b)
(/= a b)
(< a b)
(> a b)
(<= a b)
(>= a b)
```

---

### Booleani

Common Lisp usa:

```lisp
T       ; vero
NIL     ; falso
```

`NIL` è anche la lista vuota.

```lisp
(null '())        ; → T
(null '(1 2))     ; → NIL
```

---

### Simboli

```lisp
'foo
'hello
'my-symbol
```

Quote abbreviata:

```lisp
'foo
```

equivale a:

```lisp
(quote foo)
```

---

### Stringhe e caratteri

```lisp
"hello"
#\A
#\Space
#\Newline
```

```lisp
(length "hello")          ; → 5
(char "hello" 0)          ; → #\h
```

---

# 3. Variabili

```lisp
(defparameter *x* 10)
```

Convenzione comune: variabili globali dinamiche tra `*...*`.

```lisp
* x *    ; NON usare gli spazi: esempio concettuale
```

Corretto:

```lisp
*x*
```

Variabile locale:

```lisp
(let ((x 10)
      (y 20))
  (+ x y))
; → 30
```

`let*` permette riferimenti tra variabili:

```lisp
(let* ((x 10)
       (y (* x 2)))
  y)
; → 20
```

Assegnamento:

```lisp
(setf x 20)
```

---

# 4. Funzioni

Definizione:

```lisp
(defun square (x)
  (* x x))
```

Chiamata:

```lisp
(square 5)
; → 25
```

Più argomenti:

```lisp
(defun add (a b)
  (+ a b))
```

Il valore restituito è normalmente quello dell'ultima espressione:

```lisp
(defun abs-value (x)
  (if (< x 0)
      (- x)
      x))
```

`return-from` permette un'uscita esplicita:

```lisp
(return-from nome valore)
```

---

# 5. Funzioni anonime

```lisp
(lambda (x)
  (* x x))
```

Uso:

```lisp
(funcall
  (lambda (x) (* x x))
  5)
; → 25
```

Una funzione può essere passata come valore:

```lisp
(defun apply-twice (f x)
  (funcall f (funcall f x)))
```

```lisp
(apply-twice #'1+ 10)
; → 12
```

`#'` ottiene l'oggetto funzione:

```lisp
#'square
```

---

# 6. Condizioni

### `if`

```lisp
(if condizione
    espressione-true
    espressione-false)
```

```lisp
(if (> x 0)
    'positive
    'non-positive)
```

### `when`

```lisp
(when (> x 0)
  ...
  ...)
```

Esegue il corpo solo se vero.

### `unless`

```lisp
(unless (null x)
  ...)
```

Esegue il corpo solo se falso.

### `cond`

```lisp
(cond
  ((< x 0) 'negative)
  ((= x 0) 'zero)
  (t       'positive))
```

`t` è il caso predefinito.

---

# 7. Operatori logici

```lisp
(and a b c)
(or a b c)
(not x)
```

Esempio:

```lisp
(and (> x 0)
     (< x 100))
```

`and` e `or` utilizzano **short-circuit evaluation**.

---

# 8. Liste

Lista letterale:

```lisp
'(a b c)
```

Lista vuota:

```lisp
'()
```

Costruzione:

```lisp
(cons 'a '(b c))
; → (A B C)
```

Accesso:

```lisp
(car '(a b c))
; → A

(cdr '(a b c))
; → (B C)
```

Convenzioni equivalenti:

```lisp
(first '(a b c))
(rest  '(a b c))
```

Elementi:

```lisp
(second '(a b c))        ; → B
(third  '(a b c))        ; → C
(nth 1 '(a b c))         ; → B
```

Lunghezza:

```lisp
(length '(a b c))
; → 3
```

Concatenazione:

```lisp
(append '(a b) '(c d))
; → (A B C D)
```

Reverse:

```lisp
(reverse '(a b c))
; → (C B A)
```

---

# 9. Predicati

```lisp
(null x)
(listp x)
(atom x)
(numberp x)
(integerp x)
(stringp x)
(symbolp x)
(functionp x)
```

Confronto generico:

```lisp
(eq a b)
(eql a b)
(equal a b)
(equalp a b)
```

Regola pratica:

```text
EQ     → identità di simboli
EQL    → identità + numeri/caratteri
EQUAL  → uguaglianza strutturale
EQUALP → uguaglianza strutturale più permissiva
```

Per numeri, usare normalmente:

```lisp
=
```

---

# 10. Ricorsione

Schema tipico:

```lisp
(defun length* (lst)
  (if (null lst)
      0
      (1+ (length* (cdr lst)))))
```

Struttura:

```text
caso base
   ↓
caso ricorsivo
   ↓
problema più piccolo
```

Ogni ricorsione deve avere una condizione di terminazione.

---

# 11. Iterazione

### `dolist`

```lisp
(dolist (x '(1 2 3))
  (print x))
```

### `dotimes`

```lisp
(dotimes (i 10)
  (print i))
```

### `loop`

```lisp
(loop for x in '(1 2 3)
      do (print x))
```

Raccogliere risultati:

```lisp
(loop for x in '(1 2 3)
      collect (* x x))
; → (1 4 9)
```

Somma:

```lisp
(loop for x in '(1 2 3)
      sum x)
; → 6
```

---

# 12. Sequence

Le principali funzioni:

```lisp
(length seq)

(first seq)
(last seq)

(elt seq n)

(map ...)
```

Funzioni molto usate:

```lisp
(mapcar #'f list)

(remove-if #'predicate list)

(remove-if-not #'predicate list)

(find-if #'predicate list)

(count-if #'predicate list)

(some #'predicate list)

(every #'predicate list)

(reduce #'f sequence)
```

Esempio:

```lisp
(mapcar #'square '(1 2 3 4))
; → (1 4 9 16)
```

```lisp
(remove-if #'evenp '(1 2 3 4 5))
; → (1 3 5)
```

---

# 13. Associazioni

### Association list

```lisp
'((name . "Mario")
  (age  . 23))
```

Ricerca:

```lisp
(assoc 'name data)
```

### Property list

```lisp
(list :name "Mario"
      :age 23)
```

Accesso:

```lisp
(getf plist :name)
```

Le keyword sono simboli preceduti da `:`:

```lisp
:name
:age
:red
```

---

# 14. Hash table

Creazione:

```lisp
(defparameter *table*
  (make-hash-table))
```

Inserimento:

```lisp
(setf (gethash 'foo *table*) 42)
```

Lettura:

```lisp
(gethash 'foo *table*)
```

Eliminazione:

```lisp
(remhash 'foo *table*)
```

Iterazione:

```lisp
(maphash
  (lambda (key value)
    (format t "~A = ~A~%" key value))
  *table*)
```

---

# 15. Vector e Array

Vector:

```lisp
#(10 20 30)
```

Accesso:

```lisp
(aref #(10 20 30) 1)
; → 20
```

Array:

```lisp
(make-array '(3 3))
```

Accesso:

```lisp
(aref matrix row column)
```

---

# 16. Strutture

Definizione:

```lisp
(defstruct person
  name
  age)
```

Creazione:

```lisp
(make-person :name "Mario"
             :age 23)
```

Accesso:

```lisp
(person-name p)
(person-age p)
```

---

# 17. Multiple values

Restituire più valori:

```lisp
(values quotient remainder)
```

Riceverli:

```lisp
(multiple-value-bind (q r)
    (floor 17 5)
  ...)
```

---

# 18. Input / Output

Input:

```lisp
(read)
```

Output:

```lisp
(print x)

(princ x)

(format t "~A~%" x)
```

`format`:

```lisp
(format t "Name: ~A~%" name)
(format t "Value: ~D~%" n)
(format t "Float: ~,2F~%" x)
```

Principali direttive:

```text
~A    stampa generica
~D    intero decimale
~F    floating point
~%    newline
~~    carattere ~
```

---

# 19. File

Apertura:

```lisp
(with-open-file (stream "data.txt"
                        :direction :input)
  ...)
```

Lettura:

```lisp
(read-line stream)
```

Scrittura:

```lisp
(with-open-file (stream "data.txt"
                        :direction :output
                        :if-exists :supersede)
  (format stream "Hello~%"))
```

---

# 20. Macro

Definizione:

```lisp
(defmacro twice (form)
  `(progn
     ,form
     ,form))
```

Uso:

```lisp
(twice (print "hello"))
```

Backquote:

```lisp
`(...)
```

Unquote:

```lisp
,...
```

Le macro trasformano codice **prima della valutazione**.

---

# 21. CLOS

Classe:

```lisp
(defclass person ()
  ((name :initarg :name
         :accessor person-name)
   (age  :initarg :age
         :accessor person-age)))
```

Istanza:

```lisp
(make-instance 'person
               :name "Mario"
               :age 23)
```

Generic function:

```lisp
(defgeneric describe-person (person))
```

Metodo:

```lisp
(defmethod describe-person ((p person))
  (format t "~A (~A)~%"
          (person-name p)
          (person-age p)))
```

---

# 22. Condizioni ed errori

Errore:

```lisp
(error "Invalid value")
```

Gestione semplice:

```lisp
(handler-case
    (dangerous-operation)
  (error (e)
    (format t "Error: ~A~%" e)))
```

Segnalazione non necessariamente fatale:

```lisp
(warn "Suspicious value")
```

---

# 23. Package

Definizione:

```lisp
(defpackage :my-app
  (:use :cl)
  (:export :foo))
```

Selezione:

```lisp
(in-package :my-app)
```

Uso dall'esterno:

```lisp
(my-app:foo)
```

Simbolo interno:

```lisp
my-app::internal-function
```

Preferire API pubbliche tramite `export`.

---

# 24. Tipi e dichiarazioni

Dichiarazione:

```lisp
(declare (type integer x))
```

Esempio:

```lisp
(defun square (x)
  (declare (type number x))
  (* x x))
```

Controllo esplicito:

```lisp
(typep x 'integer)
```

---

# 25. Compilazione

Una funzione può essere compilata:

```lisp
(compile 'square)
```

Oppure definita normalmente con:

```lisp
(defun ...)
```

e compilata dall'implementazione.

In generale:

```text
source
  ↓
reader
  ↓
S-expression
  ↓
compiler/interpreter
  ↓
execution
```

---

# 26. ASDF

ASDF gestisce sistemi/progetti Common Lisp.

Concettualmente:

```text
project/
├── project.asd
├── src/
│   └── package.lisp
│   └── main.lisp
└── test/
    └── tests.lisp
```

Un sistema definisce:

```lisp
(defsystem "my-project"
  :components
  ((:file "package")
   (:file "main")))
```

---

# 27. Regole pratiche

```text
• Preferire funzioni piccole e composabili.
• Evitare stato globale non necessario.
• Non modificare gli argomenti senza motivo.
• Separare logica, I/O e presentazione.
• Gestire esplicitamente i casi limite.
• Testare le funzioni indipendentemente.
• Usare nomi descrittivi.
• Documentare le API pubbliche.
• Misurare le prestazioni prima di ottimizzare.
• Usare il debugger: non averne paura.
```

---

# 28. Pattern essenziali

### Elaborare una lista

```lisp
(defun process (lst)
  (if (null lst)
      ...
      (cons
        ...
        (process (cdr lst)))))
```

### Accumulatore

```lisp
(defun sum (lst)
  (labels ((iter (lst acc)
             (if (null lst)
                 acc
                 (iter (cdr lst)
                       (+ acc (car lst))))))
    (iter lst 0)))
```

### Higher-order

```lisp
(mapcar #'function sequence)
```

### Filtro

```lisp
(remove-if-not #'predicate sequence)
```

### Riduzione

```lisp
(reduce #'function sequence)
```

### Ricerca

```lisp
(find-if #'predicate sequence)
```

### Hash table

```lisp
(gethash key table)
```

### Iterazione

```lisp
(loop for x in sequence
      ...)
```

### Backtracking

```text
solve(state):
    if goal(state):
        return solution

    for each possible move:
        if valid(move):
            apply move
            recursively solve
            undo move
```

---

# 29. Regola fondamentale

In Common Lisp, imparare la sintassi non è l'obiettivo.

L'obiettivo è saper trasformare:

```text
problema
   ↓
modello
   ↓
funzioni / dati
   ↓
algoritmo
   ↓
codice
   ↓
test
   ↓
debugging
```

Gli esercizi del manuale seguiranno esattamente questa progressione.