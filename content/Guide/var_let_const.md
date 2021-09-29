---
title: "var, let e const"
draft: false
---
***Scritto da [Andrea Manzini](https://ilmanzo.github.io/)***

questo articolo è stato tradotto da [Nim by Example](https://nim-by-example.github.io/)


### var: variabili mutabili

{{< highlight nim >}}
var
  a = "pippo"
  b = 0
  # se non viene specificato nessun valore, e' inizializzato a 0
  c: int

# funziona, le variabili sono mutable
a.add("pluto")
b += 1
c = 3

echo a,b,c
{{< / highlight >}}

### let: variabili immutabili

{{< highlight nim >}}
let
  d = "tizio"
  e = 5
  # f: float   # errore di compilazione, la variabile deve assumere un valore

# assegnare nuovi valori a queste variabili, `d` and `e`, causerebbe errore di compilazione
#d.add("caio")
#e += 1
{{< / highlight >}}

### const: costanti 
{{< highlight nim >}}
const PI = 3.14159265

proc getAlphabet(): string =
  for letter in 'A'..'Z':
    result.add(letter)

# una caratteristica molto potente di Nim è che può eseguire del codice questo causa l'esecuzione della proc a tempo di compilazione
const alphabet = getAlphabet()

echo alphabet

#alphabet = "abc" # questo genera un errore di compilazione, era stata dichiarata come costante 
{{< / highlight >}}

per curiosità, se sbirci nel codice C generato, troverai una riga del tipo 

{{< highlight c >}}
STRING_LITERAL(TM__wIAuO6fGZn7Wh9cwbqAvZtw_9, "ABCDEFGHIJKLMNOPQRSTUVWXYZ", 26);
{{< / highlight >}}

generata dal compilatore Nim, che esegue il codice indicato durante la compilazione e crea la costante.
