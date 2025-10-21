# Blatt1

Aufgabe 1:

Der reguläre Ausdruck a+a(a+b)*a beschreibt eine Sprache über dem Alphabet {a, b}. 

Die Sprache besteht aus allen Wörtern, die entweder: Nur aus mindestens einem a bestehen  durch den Teil a+ z. B.: a, aa, aaa, … oder Mit a beginnen, mit a enden, und dazwischen eine beliebige Folge von a und b haben (durch den Teil a(a+b)*a), z.B: abba , ababa .. 


Aufgabe 2:
2.a.

^(V|v|P|p|[a-zA-Z])[a-zA-Z0-9_]+(?<!_)$

2.b

Start: Muss mit V, v, P, p oder anderen Buchstaben a-zA-Z beginnen. 

Folge: Darf Buchstaben, Ziffern oder _ enthalten. 

Ende: Darf nicht mit _ enden. 

Länge: Mindestens zwei Zeichen.

DFA:

q0 : Startzustand

q1 : Nach erstem gültigen Buchstaben

q2 : Gültige Zeichenkette (endet nicht mit _). 

q3 : Letztes Zeichen war _ 

Beispiel 1: P_param2

q0 – P → q1 

q1 – _ → q3

q3 – p → q2 

q2 – a → q2, r → q2, a → q2, m → q2, 2 → q2 

Akzeptiert (q2).

Beispiel 2 : va1_

q0 – v → q1 

q1 – 1 → q2 

q2 – a → q2, _ → q3 

Nicht akzeptiert (endet in q3 mit _) 

2.c.

S → aA | bA | .... | zA | AA | BA | .... | ZA | VA | vA | PA | pA  

A → aA | bA | .... | zA | AA | .... | ZA | 0A | 1A | .... | 9A | _B | a | b | .... | z | A | B | .... | Z | 0 | 1 | .... | 9 

B → aA | bA | .... | zA | AA | .... | ZA | 0A | 1A | .... | 9A    

Beispiel 1: Fx2

S ->F A

  -> F x A
  
  ->F x 2

Beispiel 2 : p_car

S ->P A

  -> P _ B
  
  ->p _ c A
  
  -> p _ c a A
  
  -> p _ c a r



Aufgabe 3:

1.a Allgemeiner Aufbauin Python

   [+|-] (Ziffern)? . Ziffern (e|E [+|-]? Ziffern)?
   
1.b Allgemeiner Aufbauin Java:

   [+|-] (Ziffern)? . Ziffern (e|E [+|-]? Ziffern)? [fFdD]?
   
2. Reguläre Ausdrücke:
   
   2.a Python: ^[+-]?(\d*\.\d+|\d+\.\d*)([eE][+-]?\d+)?$
   
   2.b. Java:^[+-]?(\d*\.\d+|\d+\.\d*)([eE][+-]?\d+)?[fFdD]?$
    
3.DFA:



Aufgabe 4:

4.a

-->Falsche Zeichenklassen-Syntax:

Die Angabe (a-z) ist falsch, da sie nicht für alle Buchstaben von a bis z steht, sondern genau die Zeichenfolge a minus z beschreibt. Um alle Buchstaben zwischen a und z zuzulassen, muss eine Zeichenklasse mit eckigen Klammern verwendet werden: [a-z].

-->Nicht nur Kleinbuchstaben erlaubt:

E-Mail-Adressen können neben Kleinbuchstaben auch Großbuchstaben, Ziffern und bestimmte Sonderzeichen enthalten. Der gegebene Ausdruck berücksichtigt diese nicht und schließt daher viele gültige Adressen aus.

-->Punkte im Domain-Teil:

Domains können aus mehreren Teilen bestehen, zum Beispiel example.co.uk. Der ursprüngliche Regex erlaubt jedoch nur genau einen Punkt und danach einen einzelnen Buchstaben, wodurch viele reale Domains nicht erkannt werden.

-->Länge der Domain-Endung:

Top-Level-Domains (TLDs) wie .com, .de, .info oder .org bestehen aus mehreren Buchstaben. Der gegebene Ausdruck akzeptiert aber nur genau einen Buchstaben nach dem Punkt und ist somit zu restriktiv.

-->Fehlende Sonderzeichen im lokalen Teil:

Im lokalen Teil einer E-Mail-Adresse (vor dem @) sind Zeichen wie Punkte, Unterstriche, Pluszeichen oder Bindestriche erlaubt. Der Regex lässt jedoch nur Buchstaben zu und erkennt deshalb viele gültige E-Mail-Adressen nicht.

4.b:

a+b+c+c+......z auch nicht ganz richtig, weil:

Sie erlaubt nur Buchstaben, keine Ziffern oder Sonderzeichen.

Sie enthält immer noch den nicht-escaped Punkt ., der für jedes Zeichen steht.

Sie erlaubt nur eine einzige Domain-Ebene (z. B. @fsbi.de), aber keine mehrstufigen Domains (@info.fsbi.de).
   
4.c :

[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}


Aufgabe 5:


Aufgabe 6:

S->aA 

A-> dB | bA | cA 

B-> aC | bC | cA 

C-> ϵ 

Jedes Wort beginnt mit a.Danach kommt eine (möglicherweise leere) Folge aus b und c bis zum ersten d. Nach einem d kann entweder sofort das Wort mit a oder b enden  oder es folgt ein c und die Konstruktion wiederholt sich (über B -> cA), d. h. es müssen später erneut beliebig viele b/c bis zu einem weiteren d kommen.Am Ende steht genau ein a oder b (wenn die Ableitung über B -> aC oder B -> bC endet).

Regulären Ausdruck:

a (b|c)* d ( c (b|c)* d )* (a|b)  





