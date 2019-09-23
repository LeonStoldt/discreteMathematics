# Diskrete Mathematik 2

## 1.  Relationen
### 1.1 Allgemeine Relationen und deren Darstellung

-	Relationen stellen Beziehungen zwischen Objekten dar
-	kann zur Beschreibung von Ordnungen und Äquivalenzen genutzt werden
-	Relation ist eine Menge

> **Definition: Relation**
> Eine binäre Relation zwischen zwei Mengen ist eine Teilmenge des kartesischen Produkts:
> $R \subseteq M \times N$
> Für die Paare $(x,y) \in R$ gilt: $x$ steht in Relation zu $y$ (auch $x R y$)

#### Darstellung von Relationen
*Beispiel: $R = \{(1,a); (1,c); (2,b); (3,b); (3,c); (4,a)\}$*

`1.1.1 Pfeildiagramme`
```mermaid
graph LR
1((1)) --> a((a))
1 --> c((c))
2((2)) --> b((b))
3((3)) --> b
3 --> c
4((4)) --> a
```
`1.1.2 Matrixschreibweise (Adjazenzmatrix)`
|$M$ \ $N$| a | b | c |
|--|--|--|--|
| 1 | 1 | 0 | 1 |
| 2 | 0 | 1 | 0 |
| 3 | 0 | 1 | 1 |
| 4 | 1 | 0 | 0 |


`1.1.3 vereinfachtes Pfeildiagramm`
*Pfeildiagramm kann vereinfacht werden, wenn die beiden Mengen **identisch** sind.*

*Beispiel: $R = \{(1,2); (1,5); (1,6); (2,2); (2,4)\}$ci
```mermaid
graph LR
1((1)) --> 2((2))
1 --> 5((5))
1 --> 6((6))
2((2)) --> 2
2 --> 4((4))
```
---
Anzahl der möglichen Paare einer Menge am Beispiel: 
$$
M=\{1;2;3;4;5;6\}
$$$$
|M| = 6
$$
- Anzahl der Paare von $M = 6 \times 6 = 36$
- Anzahl der Relationen von $M = 2^{36} \approx 64 Milliarden$, da alle Teilmengen von $M$ Relationen sind

> **Definition: Inverse Relationen**
> Wenn $R$ eine Relation mit $R \subseteq M \times N$ ist, dann ist die Inverse Relation $R^{-1} \subseteq N \times M$.
> $R^{-1} = \{(y,x) | (x,y) \in R\}$

_Beispiel für inverse Relationen:_
$R = \{(r,l) \in M \times M | r$ "ist Mutter von" $l\}$
$R^{-1} = \{(l,r) \in M \times M | l$ "hat als Mutter" $r\}$

> **Rechenregeln inverser Relationen**
> 1. $(R_1 \circ R_2)^{-1} = R_2^{-1} \circ R_1^{-1}$
> 2. $(R_1^{-1})^{-1} = R_1$

> **Definition: Verkettung (=Komposition) von Relationen**
> Die Verkettung von den Relationen $R_1 \subseteq A \times B$ und $R_2 \subseteq B \times C$ wird folgendermaßen dargestellt: $R_1 \circ R_2 = M_1 \times M_3$
> $$R_1 \circ R_2 = \{(a,c) | (a \in A) \land (c \in C) \land (\exist y \in B: ((a,b) \in R_1) \land ((b,c) \in R_2))$$

_Beispiel für verkettete Relationen:_
$R_1 = \{(l,r) |l$ "hat als Mutter" $r\}$
$R_2 = \{(r,e) | r$ "war verheitatet mit" $e\}$
$R_1 \circ R_2 = \{(l,e) | l$ "hat als Vater" $e\}$

> **Assoziativgesetz bei der Verkettung von Relationen**
> $$(R_1 \circ R_2) \circ R_3 = R_1 \circ (R_2 \circ R_3)$$

### 1.2 Eigenschaften von Relationen

| Eigenschaft | Definition |
|:--|:--|
| 1. **identische** Relation | $I=\{(x,x)$\| $x \in M\}$ |
| 2. **reflexive** Relation | $\forall x \in M: (x,x) \in R$ |
| 3. **irreflexive** Relation | $\forall x \in M: (x,x) \notin R$ |
| 4. **symmetrische** Relation | $\forall x,y \in M: (x,y) \in R \implies (y,x) \in R$ |
| 5. **asymmetrische** Realtion | $\forall x,y \in M: (x,y) \in R \implies (y,x) \notin R$ |
| 6. **antisymmetrische** Relation | $\forall x,y \in M: (x,y) \in R\land  (y,x) \in R \implies x = y$ |
| 7. **transitive** Relation | $\forall x,y,z \in M: (x,y) \in R \land (y,z) \in R \implies (x,z) \in R$ |

_Beispiele:_
1. _identische Relationen_
```mermaid
graph LR
1((1)) --> 1
2((2)) --> 2
```
2. _reflexive Relationen_
```mermaid
graph LR
1((1)) --> 1
2((2)) --> 2
1 --> 2
```
3. _irreflexive Relationen_
```mermaid
graph LR
1((1)) --> 2((2))
```
4. _symmetrische Relationen_ 
```mermaid
graph LR
1((1)) --> 2
2((2)) --> 1
```
5. _asymmetrische Relationen_
```mermaid
graph LR
1((1)) --> 2((2))
2 --> 3((3))
3 --> 1
```
6. _antisymmetrische Relationen_
```mermaid
graph LR
1((1)) --> 2
2((2)) --> 2
```
7. _transitive Relationen_ 
```mermaid
graph LR
1((1)) --> 2
2((2)) --> 3((3))
1 --> 3
```

> **Zusammenhänge der Eigenschaften von Relationen**
> ```mermaid
> graph LR
> A((asymmetrisch)) --ist auch--> I((irreflexiv))
> I --ist nicht--> R((reflexiv))
> R --ist nicht--> I
> A --ist auch--> AN((antisymmetrisch))
> ```

> **Definition: Transitiv (reflexive) Hülle**
> Die **transitive Hülle** von der Relation $R$ wird gekennzeichnet durch $R^{+}$ und beinhaltet die Paare, die durch die Eigenschaft der Transitivität möglich werden.
> Die **reflexiv transitive Hülle** der Relation $R$ wird gekennzeichnet durch $R^{*}$ und beinhaltet zusätzlich zur transitiven Hülle die reflexiven Paare. Sie ist die kleinste transtitive und reflexive Relation, die $R$ umfasst.

_Beispiele_
_transitive Hülle (Praxisbeispiel: Organigramme in Unternehmen)_
```mermaid
graph LR
A((A)) --> B((B))
A --> C((C))
A --> D((D))
B --> D
C --> D
B --> C
```
_reflexiv transitive Hülle_
```mermaid
graph LR
A((A)) --> B((B))
A --> C((C))
A --> D((D))
B --> D
C --> D
A --> A
B --> B
C --> C
D --> D
B --> C
```
`Aufgaben dazu auf Seite 141f.`

### 1.3 Ordnungsrelationen 

> **Definition: (*strikte*) Ordnungsrelation**
> Die Ordnungsrelation ist eine Verallgemeinerung der "$\leq$"-Beziehung.
> Durch diese können Elemente einer Menge miteinander verglichen werden.
> 
> Eine **Ordnung** in $M$ existiert, wenn die Relation alle der folgenden Eigenschaften besitzt:
> -	reflexiv
> -	antisymmetrisch
> -	transitiv
> 
> Eine ***strikte* Ordnung** in $M$ existiert, wenn die Relation folgende Eigenschaften besitzt:
> -	asymmetrisch
> -	transitiv

*Beispiel einer Ordnungsrelation: Bsp. $\leq$*
```mermaid
graph LR
1((1)) --> 2
1 --> 1
1 --> 3
2((2)) --> 3((3))
2 --> 2
3 --> 3
```
*Beispiel einer strikten Ordnungsrelation: Bsp. $\lt$*
```mermaid
graph LR
1((1)) --> 2
1 --> 3
2((2)) --> 3((3))
```

> **Definition: *totale* Ordnungsrelation**
> Bei einer ***totalen* Ordnungerelation** sind je zwei Elemente von $M$ bezüglich der Relation $R$ vergleichbar:
> $\forall x, y \in M: (x,y) \in R \lor (y,x) \in R$
>
> Sollte diese Eigenschaft nicht gegeben sein, spricht man von einer ***partiellen* Ordnung / Teilordnung**

*Beispiel: totale Ordnungsrelation*
Die Ordnungsrelation $\leq$ ist eine totale Ordnungsrelation in $\N$, da zwei Zahlen immer vergleichbar sind (5 $\leq$ 3 $\lor$ 3 $\leq$ 5).

*Beispiel: partielle Ordnungsrelation*
Die Ordnung "$:$" (geteilt durch) ist eine partielle Ordnungsrelation in $\N$, da die Relation $\frac{2}{3}$ oder $\frac{3}{2}$ in $\N$ nicht vergleichbar ist.

> **Definition: Nachbarschaftsrelation**
> Bei einer strikten Ordnungsrelation $\lt$ in $M$ ist die Nachbarschaftsrelation gegeben durch:
> $x \lt^{N} y \iff (x \lt y) \land (\nexists z \in M: (x \lt z) \land (z \lt y))$
> Es existiert kein Wert der Menge $M$ der zwischen die Werte $x$ und $y$ passt.

*Beispiel: Nachbarschaftrelation*
Strikte Ordnungsrelation $\lt$ in $\N: x = 3, y = 4$
$3 \lt^{N} 4 \iff (3 \lt 4) \land (\nexists z \in \N: (3 \lt z) \land (z \lt 4))$ - wahre Aussage
$3 \lt^{N} 5 \iff (3 \lt 5) \land (\nexists z \in \N: (3 \lt z) \land (z \lt 5))$ - falsche Aussage, da $z = 4$ existiert.

> **Hasse Diagramm**
> Das Hasse Diagramm ist eine grafische Darstellung in Form eines Pfeildiagramms der Nachbarschaftsrelation. (Reflexive und Transitive Verbindungen werden hierbei weggelassen)

*Beispiel: Hasse Diagramm*
Betrachtet wird die Nachbarschaftsrelation von der Menger aller **Teiler** von 70 $T_{70}=\{1, 2, 5, 7, 10, 14, 35, 70\}$

```mermaid
graph TD
70((70)) --70/10 = 7--- 10((10))
70 --70/14 = 5--- 14((14))
70 --70/35 = 2--- 35((35))
10 --10/2 = 5--- 2((2))
10 --10/5 = 2--- 5((5))
14 --14/2 = 7--- 2
14 --14/7 = 2--- 7((7))
35 --35/5 = 7--- 5
35 --35/7 = 5--- 7
2 --2/1 = 2--- 1((1))
5 --5/1 = 5--- 1
7 --7/1 = 7--- 1
```

> **Informationserhaltungssatz für Hasse Diagramme**
> Wenn die Ordnungsrelation $\leq$ eine 
> -	**endliche Menge** ist, gilt: $(\leq^{N})^{*} = \leq$
> -	**beliebige Menge** ist, gilt: $(\leq^{N})^{*} \subseteq \leq$ 
> 
> Die Nachbarschaftsrelation ist also ausreichend zur Beschreibung der Ordnungsrelation, da mithilfe der transitiv-reflexiven Hülle dir Relation vollständig konstruiert werden kann.
> 
> *Für die Darstellung von Ordnungsrelationen in unendlichen Mengen (Bsp. $\R$) ist das Hasse Diagramm keine geeignete Darstellungsmethode, da hier ein Informationsverlust vorliegen kann*

### 1.4 Größte und Maximale Elemente, obere Schranken und Suprema

> **Definition: Größte - und Maximale Elemente**
> Sei $\leq$ eine Ordnungsrelation in $M$.
> **Größtes Element:**
> $größtesElement \in M \land \forall x \in M: x \leq größtesElement$ 
> 
> Eigenschaften:
> -	Größtes Element $\in M$
> -	Größtes Element ist mit allen Elementen aus $M$ vergleichbar
> -	Beim Vergleich zu den anderen Elementen in $M$, ist das größte Element $\leq$ alle anderen Elemente der Menge.
> -	Es gibt maximal ein größtes Element der Menge $M$
> -	Jedes größte Element ist auch ein maximales Element
> 
> **Maximales Element**
> $maximalesElement \in M \land \forall x \in M: maximalesElement \leq x \implies x = maximales Element$
> Eigenschaften:
> -	Maximales Element $\in M$
> -	Es ist nicht unbedingt mit allen Elementen vergleichbar
> -	Wenn es vergleichbar ist, dann ist es das größere

*Beispiel: $M=\{1,2,3,4,5,6,7,8\}, R=/$*
```mermaid
graph TD
8((8)) --- 4((4))
4 --- 2((2))
6((6)) --- 2
6 --- 3((3))
2 --- 1((1))
3 --- 1
5((5)) --- 1
7((7)) --- 1
```
| Teilmenge | maximale Elemente | größtes Elemente |
|--|--|--|
| $\{2,3,6\}$ | $\{6\}$ | 6 |
| $\{2,3\}$ | $\{2,3\}$ | $\{\}$ |
| $\{2,3,5,6\}$ | $\{5,6\}$ | $\{\}$ |
| $\{1,2,3,4,5,6,7,8\}$ | $\{5,6,7,8\}$ | $\{\}$ |

> **Definition: Supremum / Infimum**
> Ordnungsrelation $\leq$ in $M$ mit $T \subseteq M$
> 1.	$obereSchranke \in M$ von $T: \forall x \in T: x \leq obereSchranke$
>
> 2.	$untereSchranke \in M$ von $T: \forall x \in T: untereSchranke \leq x$
>
> 3.	$obereGrenze \in M$ von $T$ ist definiert durch das minimale Element der oberen Schranken
>
> 4.	$untereGrenze \in M$ von $T$ ist definiert durch das maximale Element der unteren Schranken
>
> 5.	$Supremum$ ist definiert durch das kleinste Element der Menge der oberen Schranken.
>
> 6.	$Infimum$ ist definiert durch das größte Element der Menge der unteren Schranken. 

*Beispiel: Supremum / Infimum*
| Teilmenge | Infimum | Supremum | minimalste Element | maximale Element |
|--|--|--|--|--|
| $\{2,3,6\}$ | $2$ | $6$ | $2$ | $6$ |
| $[0,8)\in \R$ | $0$ | $8$ | 0 | $\{\}$ |

*Beispiel: Obere Grenze:*
$\{3,4\} \in \{1,2,3,4,5,6,7\}$
-	Obere Schranken: $\{5,6,7\}$
-	Obere Grenze: $\{5,6\}$
-	kein Supremum

> **Definition: Existenzsatz Supremum**
> Eine Menge hat ein Supremum, wenn sie **nur eine** obere Grenze hat.
> 
> **Definition: Existenzsatz Infimum**
> Eine Menge hat ein Infimum, wenn sie **nur eine** untere Grenze hat.

`Beweis zur Übung: S. 156`


### 1.5 Verbände

> **Definition: Verband**
> Zu zwei Elementen $a,b\in M$ existiert das $Supremum$ und das $Infimum$:
> $a \sqcup b = sup\{a,b\}$
> $a \sqcap b = inf\{a,b\}$

### 1.6 Äquivalenzrelationen

> **Definition: Äquivalenzrelation**
> $R$ heißt Aquivalenzrelation, wenn
> -	$R$ ist reflexiv
> -	$R$ ist symmetrisch
> -	$R$ ist transitiv
> 
> Äquivalenzrelationen werden auch durch $\equiv$ dargestellt.

> **Definition: Äquivalenzklasse**
> Jedes Element der Äquivalenzrelation in $M$ ist in der Äquivalenzklasse $[x]$
> $[x] = \{y \in M: y \equiv x\}$

> **Eigenschaften von Äquivalenzklassen**
> 1.	Reflexivität: $x \in [x]$
> 2.	Symmetrie: $y \in [x] \implies x\in [y]$
> 3.	Transitivität: $(x \in [y] \land y \in [z]) \implies x \in [z]$
> 
> Außerdem gilt:
> Die Menge der Äquivalenzklassen von $M$ ergibt zusammengenommen die ganze Menge $M$. 
> $$\bigcup_{x \in M} [x] = M$$

### 1.7 Restklassen

> **Definition: Kongruenz modulo m**
> Zwei natürlichen Zahlen sind **kongruent modulo m** oder $\equiv_{m}$, wenn sie bei der Division durch die natürliche Zahl $m$ denselben Rest $r$ lassen.
> Hierbei entsteht folgende Äquivalenzrelation: $\equiv_{m} \subseteq \Z \times \Z$
> Die Aquivalenzklassen der Relation heißen **Restklassen modulo m**.

*Beispiele: Kongruenz modulo m*
-	Äquivalenzklassen von $\equiv_{2}$ sind gerade und ungerade Zahlen.
	-	ungerade zahlen $[1]_2$
	-	gerade Zahlen $[2]_2$
-	Äquivalenzklassen von $\equiv_{10}$
	-	$[0]_{10} = \{0, 10, 20, ...\}$
	-	$[1]_{10} = \{1, 11, 21, ...\}$
	-	$[2]_{10} = \{2, 12, 22, ...\}$
	-	$[3]_{10} = \{3, 13, 23, ...\}$
	-	$[4]_{10} = \{4, 14, 24, ...\}$
	-	$[5]_{10} = \{5, 15, 25, ...\}$
	-	$[6]_{10} = \{6, 16, 26, ...\}$
	-	$[7]_{10} = \{7, 17, 27, ...\}$
	-	$[8]_{10} = \{8, 18, 28, ...\}$
	-	$[9]_{10} = \{9, 19, 29, ...\}$

### 1.8 Abbildungen

> **Definition: Abbildung**
> Eine Abbildung beschreibt die Zuordnung von der Quell- zur Zielmenge.
> **Eigenschaften einer Abbildung**
> 1.	Existenz
> 2.	Eindeutigkeit

> **Definition: Links- / Rechtseindeutigkeit**
> **Linkseindeutigkeit**
> -	Jeder Punkt in der Zielmenge wird **max.** einmal aus der Quellmenge getroffen.
> -	Jedem Punkt in der Zielmenge ist **eindeutig** einem Punkt der Quellmenge zuzuordnen.
> $$\forall x,y \in A: \forall z \in B: (x,z) \in R \land (y,z) \in R \implies x = y$$
> 
> **Rechtseindeutigkeit**
> -	Jeder Punkt in der Quellmenge wird **max.** einmal aus der Zielmenge getroffen.
> -	Jedem Punkt in der Quellmenge ist **eindeutig** einem Punkt der Zielmenge zuzuordnen.
> $$\forall x,y \in B: \forall z \in A: (z,x) \in R \land (z,y) \in R \implies x = y$$
> 
> **Eigenschaften**
> -	Bei inversen Relationen $(R^{-1})$ wird die Eindeutigkeit umgedreht.
> *Beispielt: linkseindeutige Relation* $R \rightarrow$ *rechtseindeutige Relation* $R^{-1}$
> -	Bei Verkettung bleiben die Eigenschaften erhalten.
> *Beispiel: linkseindeutige Relationen* $R_1, R_2 \rightarrow R_1 \circ R_2$ bleibt linkseindeutig

*Beispiel Links-/Rechtseindeutigkeit:*
*Linkseindeutigkeit:*
``` mermaid
graph LR
a((a aus A)) --- x((x aus B))
a --- y((y aus B))
b((b aus A)) --würde Linkseindeutigkeit verletzen--- y
```

*Rechtseindeutigkeit:*
``` mermaid
graph RL
x((x aus B)) --- a((a aus A))
x --- b((b aus A))
y((y aus B)) --würde Rechtseindeutigkeit verletzen--- b
```

> **Definition: Links- und Rechtstotalität**
> **Linkstotalität**
> $\forall x \in A: \exists y \in B: (x,y) \in R$
> 
> **Rechtstotalität**
> $\forall y \in B: \exists x \in A: (x,y) \in R$
> 
> **Eigenschaften**
> -	Bei inversen Relationen $(R^{-1})$ wird die Totalität umgedreht.
> *Beispielt: linkstotale Relation* $R \rightarrow$ *rechtstotale Relation* $R^{-1}$
> -	Bei Verkettung bleiben die Eigenschaften erhalten.
> *Beispiel: linkstotale Relationen* $R_1, R_2 \rightarrow R_1 \circ R_2$ bleibt linkstotal

*Beispiel Links-/Rechtstotalität:*
*Linkstotalität*
``` mermaid
graph LR
a((a aus A)) --- x((x aus B))
b((b aus A)) --- x
c((c aus A)) --- y((y aus B))
d((d aus A)) --würde Linkstotalität verletzen--- d
```

*Rechtstotalität*
``` mermaid
graph RL
w((w aus B)) --- a((a aus A))
x((x aus B)) --- a
y((y aus B)) --- b((b aus A))
z((z aus B)) --würde Rechtstotalität verletzen--- z
```
> **Definition: Abbildung**
> Eine Relation heißt Abbildung oder Funktion, wenn sie 
> - **rechtseindeutig** und  (= Jeder X-Wert hat nur einen einzigen zugehörigen Y-Wert)
> - **linkstotal** ist. (= Jeder X-Wert hat einen Y-Wert)
> 
> Zu jedem $x \in A$ existiert **genau ein** $y \in B$, sodass $(x,y) \in R$
> 
> Schreibweise für eine Abbildung $R$ von $A$ nach $B$: $R: A \rightarrow B$
> 
> $A$ ist hierbei der Definitionsbereich oder auch Quellmenge
> $B$ ist hierbei das Bild oder auch Zielmenge

*Beispiel: Abbildung anhand der Funktion* $f(x) = 2x$
``` mermaid
graph LR
1((1)) --- y2((2))
2((2)) --- y4((4))
3((3)) --- y6((6))
```
*weitere Abbildung*
``` mermaid
graph RL
x((x)) --- a((a))
y((y)) --- b((b))
y --- c((c))
z((z))
```

> **Eigenschaften von Abbildungen**
> - **surjektiv**, wenn die Abbildung rechtstotal ist (= Jedem Y-Wert ist ein X-Wert zugeordnet)
> - **injektiv**, wenn die Abbildung linkseindeutig ist (= Jedem Y-Wert kann genau ein X-Wert zugeordnet werden Bsp. $f(x) = 2x$)
> - **bijektiv**, wenn die Abbildung linkseindeutig und rechtstotal ist


## 2. Algebraische Strukturen

### 2.1 Verknüpfungen

> **Definition: Verknüpfung**
> Die Verknüpfung einer nichtleeren Menge ist eine Abbildung.
> Das Ergebnis zweier verknüpfter Elemente wird dargestellt durch $x \circ y$
> 
> Das Paar $(M, \circ)$ wird algebraische Struktur genannt.

> **Kommutativgesetz**
> Eine algebraische Struktur ist kommutativ, falls 
> $\forall x,y \in M: x \circ y = y \circ x$
> 
> **Assoziativgesetz**
> Eine algebraische Struktur ist assoziativ, falls
> $\forall x,y,z \in M: (x \circ y) \circ z = x \circ (y \circ z)$

*Beispiele für algebraische Strukturen:*
-	Addition von natürlichen Zahlen: $(\N, +)$ [kommutativ und assoziativ]
-	Addition von ganzen Zahlen: $(\Z, +)$ [kommutativ und assoziativ]
-	Subtraktion von ganzen Zahlen: $(\Z, -)$ [nicht kommutativ und nicht assoziativ]

```
Bemerkung: Die Subtraktion von natürlichen Zahlen ist keine algebraische Struktur,
da bei negativen Ergebnissen der Bereich der narütlichen Zahlen verlassen wird
```

**Darstellungsform: Verknüpfungstafel**
*Beispiel: algebraische Struktur* $(\{1,2,3\}, +)$
| + | 1 | 2 | 3 |
|:--:|--|--|--|
| **1** | 2 | *3* | *4* |
| **2** | *3* | 4 | *5* |
| **3** | *4* | *5* | 6 |

```
Bemerkung: Die algebraische Struktur ist kommutativ, 
wenn die Verknüpfungstafel an der Diagonalen (hier 2,4,6) symmetrisch ist.
```
> **Existenzsatz**
> $\forall a,b \in M: \exists x \in M: a \circ x = b$
> 
> Angewendet auf die Verknüpfungstafel: Jedes Element kommt in jeder Zeile der Tabelle mind. einmal vor. (Bei $... x \circ a = b)$ kommt jedes Element in jeder Spalte mind. einmal vor.
> 
> **Eindeutigkeitssatz**
> $\forall a,b \in M: \forall x,y \in M: (a \circ x = b) \land (a \circ y = b) \implies x = y$
> 
> Angewendet auf die Verknüpfungstafel: Jedes Element kommt in jeder Zeile der Tabelle max. einmal vor. (Bei $... x \circ a = b \land y \circ a = b ...)$ kommt jedes Element in jeder Spalte max. einmal vor.


*Beispiel: Existenzsatz*
-   $(\Z, +)$: Existenzsatz gilt	
-	$(\N, +)$: Existenzsatz gilt nicht. Bsp. a = 20, b = 10

*Angewendet auf die Verknüpfungstafel:*
| $(\{-2, -1, 0, 1, 2\}, +)$ | -2 | -1 | 0 | 1 | 2 |
|:--:|--|--|--|--|--|
| **-2** | -4 | -3 | *-2* | *-1* | *0* |
| **-1** | -3 | *-2* | *-1* | *0* | *1* |
| **0** | *-2* | *-1* | *0* | *1* | *2* |
| **1** | *-1* | *0* | *1* | *2* | 3 |
| **2** | *0* | *1* | *2* | 3 | 4 |

*Beispiel: Eindeutigkeitssatz*
-	$(\N, +)$: Eindeutigkeitssatz gilt
-	$(\Z, *)$: Eindeutigkeitssatz gilt nicht. Bsp. $4*5 = 20$ und $2* 10 = 20$

*Angewendet auf die Verknüpfungstafel*
| $(\{1,2,3\}, +)$ | 1 | 2 | 3 |
|:--:|--|--|--|
| **1** | *2* | *3* | 4 |
| **2** | *3* | 4 | 5 |
| **3** | 4 | 5 | 6 |

> **Definition: Endliche Algebraische Strukturen**
> Eine endliche algebraische Struktur existiert, wenn Endlichkeit und Existenz gleichwertig sind.

`Seite 176 - Aufgaben`

### 2.2 Restklassenoperationen

> **Definition: Restklassenoperationen**
> **Restklassenaddition**
> $[a]_m \oplus [b]_m = [a + b]_m$
> 
> **Restklassenmultiplikation**
> $[a]_m \otimes [b]_m = [a * b]_m$

> **Unabhängigkeit vom Repräsentanten**
> Eigenschaften von Äquivalenzklassen, die anhand eines Repräsentanten festgelegt werden müssen bewiesen werden, dass die unabhängig vom Repräsentanten gelten.

*Beispiel: Beweis Unabhängigkeit vom Repräsentanten*
zu beweisen: $(\Z /m, \oplus)$
gegeben: $a,b, x, y \in \Z$ mit $[a]_m = [b]_m \land [x]_m = [y]_m$
zu zeigen: $[a+b]_m = [x+y]_m$
nach Voraussetzung: $o, p \in \Z$, so dass $a-x = o*m$ und $b-y = p*m$
dann gilt: 
$a + b - (x - y)$
$= a - x + b - y$
$= o * m + p * m$
$= m (o + p)$

```
Bemerkung: Rechnen mit Restklassenoperationen kann durch 
die korrekte Wahl des Repräsentanten vereinfacht werden.

Außerdem können bei Unabhängigkeit des Repräsentanten 
Kommutativ- und Assoziativgesetze angewendet werden.

Ab Seite 180. Aufgaben
```

### 2.3 Gruppen

> **Definition: Gruppe**
> Eine algebraische Struktur heißt Gruppe $G$, wenn folgendes gilt:
> -	Assoziativität
> -	Es gibt ein neutrales Element e der Gruppe mit	
>      - linksneutralem Element: $\forall a \in G: e \circ a = a$
>      - linksinversem Element: $\forall a \in G: \exists b \in G: b \circ a = e$
> 
> $oder$
> 
> -	Assoziativität
> -	Existenzsatz der algebraischen Struktur

> **Definition: Abelsche Gruppe**
> Eine Abelsche Gruppe hat zur Gruppe die zusätzliche Definition der Kommutativität. In diesem Fall wird $+$ anstatt von $\circ$ verwendet.

*Beispiel Neutrale und Inverse Elemente:*
-	Neutrales Element der Addition: **0** (Bsp. $5 + 0 = 5$)
-	Neutrales Element der Multiplikation: **1** (Bsp. $5 * 1 = 5$)
-	Inverses Element der Addition: Element $a$, Inverses- $-a$ (Bsp. $5 - 5 = 0$
-	Inverses Element der Multiplikation: Element $a$, Inverses Element $a^{-1}$ oder $\frac1a$

`Bemerkung: Es gibt genau ein Neutrales Element.`


> **Eindeutigkeit der Lösbarkeit von einer Gruppe**
> Für jede Gruppe gilt der Eindeutigkeitssatz. D.h. es gibt für jedes $a,b \in G$ höchstens eine Lösung $c \in G$ der Gleichung $a \circ c = b$

> **Ordnung einer Gruppe**
> Als Ordnung einer Gruppe wird die Anzahl der Elemente definiert.
> $$|G|$$

*Beispiel zur Ordnung einer Gruppe:*
$|(\{1,2,3\}, +)| = 3$


### 2.4 Restklassengruppen mit Multiplikation

*Beispiel: ggT durch Primfaktorzerlegung - ggT(240,420)*
240 = 2 * 2 * (2 * 2 * 3 * 5)
420 = (2 * 2 * 3 * 5) * 7
ggT(240,420) = 2 * 2 * 3 * 5 = 60

> **Definition: "div" und "mod"**
> $a = q * b + r$
> $q = a \: div \: b$ `Quotient der Division`
> $r = a \: mod \: b$ `Rest der Division`

*Beispiel: a = 68, b = 10*
$q = \frac{68}{10} = 6$
$r = 68 \: mod \: 10 = 8$
$68 = 6 * 10 + 8$

> **gemeinsame Teiler**
> $a = q * b + r$
> Die Menge $gT(a,b)$ der gemeinsamen Teiler ist gleich der Menge $gT(b,r)$
> Am Beispiel von oben: $gT(68, 10) = \{2\} = gT(10, 8)$

> **Euklidischer Algorithmus**
> Algorithmus zur Berechnung des $ggT$ zweier positiver ganzer Zahlen $a$ und $b$
> $ggT(a, b): (a > b)$ 
> $a = q * b + r_1$
> $b = q * r_1 + r_2$
> $r_1 = q * r_2 + r_3$
> $...$
> $r_{n-1} = q * r_n + 0$
> $ggT(a,b) = r_n$
> `Bemerkung: q ist der Quotient und Zeilenunabhängig`

> **Definition: Satz von Bézout**
> Für $a, b$ gibt es ein $a^{*} \in \N$ und $b^{*} \in \Z$, mit:
> $$a^{*}*a + b^{*} * b = ggT(a,b)$$

*Beispiel: Satz von Bézout:*

$a = 17, b = 5$
$ggT(17,5) = 1$
$a^{*} \in \N = 3$
$b^{*} \in \Z = -10$
$a^{*} * a + b^{*}*b = 3 * 17 + (- 10 * 5) = 1 = ggT(17,5)$

> **Existenzsatz: Multiplikative Inverse Restklasse**
> Eine Restklasse $[a]_m$ besitzt nach dem Satz von Bézout ein multiplikatives Inverses $[a^{*}]_m$:
> $$[a]_m \otimes [a^{*}]_m = [1]_m$$

*Beispiel: Multiplikatives Inverse*
$[3]_5 \otimes [2]_5 = [1]_5$
$[2]_5$ ist die multiplikativ Inverse Restklasse zu $[3]_5$.

>**Multiplikative Restklassengruppe**
> Wenn der modulo eine Primzahl ist, dann ist $\Z / m$ \ $\{[0]_m\}$ eine Gruppe.

>**Existenzsatz: Restklassengleichung**
> Wenn der $ggT(a,m)$ durch $b$ teilbar ist, gilt folgende Gleichung:
> $$[a]_m \otimes [x]_m = [b]_m$$

>**Vorgehen:**
> ``` mermaid
> graph TD
> 1((Euklid-Algorithmus)) --> 2((ggT von a, m teilt b))
> 2 --nein--> no((keine Lösung))
> 2 --ja--> yes((eine oder mehrere Lösungen))
> yes --> 3((Euklid-Algorithmus rückwärts))
> 3 --> 4((Ergebnis mit b/ggT multiplizieren))
> 4 --> 5((kleinsten Repräsentanten finden))
> 5 --> 6((Probe))
> ```

*Beispiel: Restklassengleichung*
$ggT(12,15) = 3$

$[12]_{15} \otimes [x]_{15} = [5]_{15}$
$3$ ist kein Teiler von $5 \rightarrow$ es gibt keine Lösung für die obige Gleichung.

$[12]_{15} \otimes [x]_{15} = [9]_{15}$
$3$ ist Teiler von $9$, da $9$ ein Vielfaches vom $ggT(12,15) = 3$ ist $\rightarrow$ die obige Gleichung besitzt Lösung(en):

Berechnung der Lösung:
1. Euklid-Algorithmus vorwärts: (evtl. einen höheren Repräsentanten wählen)
$[12]_{15} = [27]_{15}$
$27 = 1 * 15 + 12$
$15 = 1 * 12 + 3$ `hier für Euklid-Algorithmus rückwärts einsteigen`
$12 = 4 * 3 + 0$

2. Euklid-Alorithmus rückwärts:
$3 = 15 - 12$
$3 = 15 - (27 - 15)$
$3 = 2 * 15$ **- 1** $* 27$
$[-1]_{15} = [14]_{15}$
Daher ist das multiplikative Inverse von $[12]_{15}$ die Restklasse $[-1]_{15} = [14]_{15}$.
3. Multiplikator für das gesuchte $x$ identifizieren:
$b = 9, ggT(a,m) = 3 \implies \frac{9}{3} = 3$
4. Lösung finden:
$x = (Multiplikator * multiplikatives Inverse) \: mod \: m = (3 * 14) \: mod \: 15 = 12$

Ergebnis: $[12]_{15} \otimes [12]_{15} = [9]_{15}$

### 2.5 Untergruppen

> **Definition: Untergruppe**
> Wenn eine Gruppe $(G, \circ)$ eine nichtleere Teilmenge $U$ besitzt, heißt diese **Untergruppe**, wenn sie selbst eine Gruppe mit $\circ$ bildet.
> Die Kurzschreibwese ist $U \leq G$

*Beispiel: Untergruppe*
Die Gruppe $(\Z, +)$ ist eine Untergruppe der Gruppe $(\mathbb{Q}, +)$
Also kurzgeschrieben: $(\Z, +) \leq (\mathbb{Q}, +)$

> **Untergruppen, die von einem Element erzeugt werden:**
> Eine von $g \in (G, \circ)$ erzeugte Untergruppe ist definiert durch die Menge $\{\underbrace{g \circ ... \circ g}_{k - mal} | k \in \N\}$ und hat folgende Schreibweise $<g>$.

Wiederholungen von Gruppenelementen:
$g \in (G, \circ)$ und $k \in \Z$
$g^{k}=\left \{ 
\begin{array}{ll} 
\underbrace{g \circ ... \circ g}_{k-mal} & falls & k > 0
\\\\ e (\text{neutrales Element}) & falls & k = 0
\\\\ \underbrace{g^{-1} \circ ... \circ g^{-1}}_{-k-mal} & falls & k < 0
\end{array}\right.$

> **Ordnung eines Gruppenelements**
> Die Ordnung eines Gruppenelements schreibt man durch $ord(g)$ und bezeichnet die kleinste Zahl $k \in \N$ für die gilt: $g^{k} = e$.
> Sollte es kein $k \in \N$ geben, für das gilt $g^{k} = e$, dann hat $g$ die Ordnung $\infin$.

*Beispiel: Ordnung eines Gruppenelements*
$(\Z/6, \oplus)$
| $g$ | $ord(g)$ | $<g>$ |
|--|--|--|
| 0 | 1 | $[0]_6$ |
| 1 | 6 | $\{[1]_6, [2]_6, [3]_6, [4]_6, [5]_6, [0]_6\}$ |
| 2 | 3 | $\{[2]_6, [4]_6, [0]_6\}$ |
| 3 | 2 | $\{[3]_6, [0]_6\}$ |
| 4 | 3 | $\{[4]_6, [2]_6, [0]_6\}$ |
| 5 | 6 | $\{[5]_6, [4]_6, [3]_6, [2]_6, [1]_6, [0]_6\}$ |

*Erklärung anhand eines Beispiels der Tabelle:*
Durch $(\Z /6, \oplus)$ ergibt sich am Beispiel von $g=4$ folgendes $<g>$:
$[4]_6 + [4]_6 = [8]_6 = [2]_6$
$[4]_6 + [4]_6 + [4]_6 = [12]_6 = [0]_6$
$[4]_6 + [4]_6 + [4]_6 + [4]_6 = [16]_6 = [4]_6$

> **Ordnung der Untergruppe:**
> Für die Untergruppe $H \leq (G, \circ)$ gilt:
> $$ord(H) | ord(G)$$

> **Satz von Euler:**
> $$g^{ord(G)} = e$$
> Dieser Satz gilt, da $$g^{ord(G)} = g^{k * ord(g)} =(g^{ord(g)})^k = e^k = e$$


### 2.6 Isomorphismen

> **Gruppenisomorphismus**
> Ein Isomorphismus ist eine **Abbildung** $\phi: G \rightarrow H$ der beliebigen Gruppen $(G, \circ)$ und $(H, \otimes)$, die folgende Eigenschaften hat:
> -	die Abbildung ist **bijektiv**
> -	die Abbildung ist **strukturerhaltend**: $\forall g_1, g_2 \in G: \phi(g_1 \circ g_2) = \phi(g_1) \otimes \phi (g_2)$
> -	die beiden Gruppen $G$ und $H$ haben dieselbe Anzahl von Elementen
> 
> Wenn es einen Isomorphismus zwischen $G$ und $H$ gibt, nennt man die beiden Gruppen isomorph.
> 
> **Isomorph = Iso + morph = gleich + gestaltet**
> 
> ---
> 
> **Erhaltung der Gruppenstruktur:**
> -	$\phi(e_G) = e_H$ 
> `Die Abbildung des neutralen Elements von G zeigt auf das neutrale Element von H`
> -	$\forall g \in G: ord(g) = ord(\phi(g))$ 
> `Die Ordnung eines Elements aus G ist gleich die Ordnung des Elements der Abbildung auf H`
> $\forall g \in G: \phi (g^{-1}) = \phi (g)^{-1}$
> `Die Abbildung des inversen Elements ist das inverse Element der Abbildung`


# Kryptologie

### Einführung

$Kryptografie$
$= Krypto + grafie$ 
$= geheim + schreiben$
$\rightarrow$ Die Lehre vom geheimen Schreiben

**Kryptologie:**
- Kryptografie + Kryptoanalyse
- ist Teilgebiet der Informationssicherheit 

> **Schutzziele:**
> - Vertrauligkeit
> 	-	Nachricht für Unbefugte nicht lesbar
> - Integrität:
> 	-	Nachricht nicht unbemerkt veränderbar
> - Authentizität
> 	-	Nachricht stammt tatsächlich vom angegebenen Absender
> - Verbindlichkeit
> 	-	Versand / Empfang ist nicht abzustreiten
> - Anonymität
> 	-	Absender / Empfänger bleibt geheim

> **Kryptosystem:**
> -	$P$ - Menge aller Klartexte
> -	$C$ - Menge aller Geheimtexte
> -	$K$ - Menge aller Schlüssel
> 
> Es ergeben sich folgende Abbildungen:
> -	encrypt: $e: P \times K \rightarrow C$
> -	decrypt: $d: C \times K \rightarrow P$


#### Symmetrische Verschlüsselungsverfahren

- Der Entschlüsselungs-Key ist aus dem Verschlüsselungs-Key leicht ermittelbar **oder** sie sind identisch
- Sender und Empfänger besitzen dasselbe Geheimnis
- Jeder mit der Möglichkeit zu verschlüsseln, hat auch die Möglichkeit zu entschlüsseln


#### Asymmetrische Verschlüsselungsverfahren

- Der Entschlüsselungs-Key ist nicht (in angemessener Zeit) aus dem Verschlüsselungs-Key ermittelbar
- Der Verschlüsselungs-Key kann vom Empfänger öffentlich bekannt gegeben werden $\rightarrow$ **public-key**
- Sender und Empfänger müssen kein Geheimnis austauschen
- Wer verschlüsseln kann, kann nicht entschlüsseln


### Klassische Verfahren

#### Skytale
> -	Ein Papier wird wendelförmig um einen Stab gewickelt und entlang der Stabseite beschrieben.
> -	Schlüssel: Durchmesser des Stabs
> -	Verfahren: Transpositionsverfahren (Veränderung der Stelle des Buchstabens)

*Beispiel Skytale:*
$P = "diesisteinbeispiel"$
$K= 4$
| 1 | 2 | 3 | 4 |
|--|--|--|--|
| d | i | e | s |
| i | s | t | e |
| i | n | b | e |
| i | s | p | i |
| e | l |  |  |
$C=diiieisnsletbpseei$

---

#### Caesar
> Verschiebung des Alphabets um einen Schlüssel k
> -	Schlüssel: $k \in \Z_{26}$
> -	Verfahren: monoalphabetisches Substitutionsverfahren

*Beispiel Caesar:*
$P = "diesisteinbeispiel"$
$K= 4$
|  | Alphabet |
|--|--|
| alt | $ABCDEFGHIJKLMNOPQRSTUVWXYZ$ |
| neu | $EFGHIJKLMNOPQRSTUVWXYZABCD$

$C=hmiw mwx imr fimwtmip$

---

#### Permutations-Chiffren
> Permutationen = Anordnungsmöglichkeiten
> Jeder Buchstabe kann auf jeden anderen beliebigen weiteren Buchstaben abgebildet werden $\rightarrow$ $|K| = 26!$
> -	Verfahren: monoalphabetisches Substitutionsverfahren
> -	Permutation ist eine bijektive Abbildung von der Menge auf sich selbst

*Beispiel Permutations-Chiffren:*
$P = "diesisteinbeispiel"$
$K= [neues Alphabet]$
|  | Alphabet |
|--|--|
| alt | $ABCDEFGHIJKLMNOPQRSTUVWXYZ$ |
| neu | $OSBWGDJVZFNMAYTQLEPRCHKIUX$

$C=wzgp zpr gza sgzpqzgm$

---

#### Verfahren zur Entschlüsselung für `monoalphabetische` Substitutionsverfahren

#### Häufigkeitsanalyse
> -	Häufigkeitsverteilung der Buchstaben analysieren
> -	Zuverlässigkeit steigt mit der Länge des Textes
> -	Sprachspezifische Besonderheiten werden ausgenutzt
> 
> Bigrammanalyse
> Buchstabenkombinationen werden analysiert (Häufigkeit)
> Bsp. "en", "er", "ch", "ei" usw.

---

#### Vigenère-Chiffre
> -	Verwendung mehrerer Caesar-Chiffren
> -	$K = gewähltes \: Schlüsselwort$
> -	Verfahren: Polyalphabetisches Substitutionsverfahren
> -	Sicherheit: hängt von der Länge- und der Zufälligkeit des Schlüssels ab

![Vigenere Quadrat](https://bit.ly/2m3VwNp)

*Beispiel Vigenère-Chiffre:*
$P = "diesisteinbeispiel"$
$K= GEHEIM$
|  |  |
|--|--|
| P | $d i e s i s t e i n b e i s p i e l$ |
| K | $g e h e i m g e h e i m g e h e i m$

$C= jmlw qez ipr jqowwmmx$

---

#### Verfahren zur Entschlüsselung für `polyalphabetischen` Substitutionsverfahren

#### Kasiski-Test
> -	Idee: Wiederholungen einer Zeichenfolge im Klartext mit einem $n$-fachen Abstand der Schlüssellänge, spiegeln sich im verschlüsselten Text wieder
> -	Beachte: Wiederholungen können auch zufällig auftreten
> -	Vorgehen:
> 1.	wiederholende Zeichenketten im Geheimtext untersuchen
> 2.	Indizies der Zeichenketten notieren
> 3.	Abstände ermitteln
> 4.	Zerlegung des Abstands in Primfaktoren
> 5.	kleinster gemeinsamer Teiler ermitteln, der in **allen** Abständen vorkommt $\rightarrow$ Schlüssellänge
> 6.	Aufteilen des Geheimtexts in Teiltexte
> 7. Häufigkeitsanalyse
> 8.	Schlüssel herausfinden

---

#### Friedman-Test
> Mithilfe des Friedman-Tests kann die Größenordnung des Schlüssels abgeschätzt werden, mit dem ein Text durch polyalphabetische Substitution verschlüsselt wurde.
> Idee: Je länger das Schlüsselwort, desto regelmäßiger sind die Häufigkeiten verteilt
> 1.	Annahme der Schlüssellänge treffen $|k|$
> 2.	Text in $|k|$-Spalten untereinander aufschreiben
> 3.	Koinzidenz pro Spalte ausrechnen  
> $$
> \kappa(m) = \frac{1}{n * (n-1)} * \sum\limits_{j=1}^{26} h_i * (h_i - 1) \\
> n = \text{Länge des Text} \\
> h_i = \text{Häufigkeit des jeweiligen Buchstabens}
> $$
> 4.	Koinzidenzen auf bekannte Werte prüfen ($\kappa_{DE} (m) \approx 0,0762, \kappa_{RND} (m) \approx 0,0385$ )
> 5.	Bei passenden Koinzidenzen sind die Spalten jeweils monoalphabetisch verschlüsselt (da die wahrscheinliche Schlüssellänge bekannt ist)

> **Perfekte Sicherheit**
> *Sicherheit durch Ununterscheidbarkeit*
> 1.	Angreifer wählt zwei bel. gleichlange Klartexte
> 2.	Einer der Texte wird zufällig gewählt und verschlüsselt
> 3.	Wenn der Angreifer eine Wahrscheinlichkeit von 50% hat, gilt das Kryptosystem als sicher.

> **One Time Pad Verfahren**
> -	ist ein perfekt sicheres Kryptosystem
> -	basiert auf dem Vigenère Verfahren, mit folgenden Vorgaben:
>	-	Schlüssellänge = Klartextlänge
> 	-	Schlüsselbuchstaben sind **zufällig** gewählt
> 	-	Schlüssel darf nur einmal verwendet werden
> -	Schwierigkeiten:
> 	-	Zufälligkeit
> 	-	Schlüsselgröße
> 	-	Schlüsselübertragung


### Euler und Fermat

> **Eulersche Phi-Funktion**
> $$\phi(n) = |\{a \in \N | 1 \leq a \leq n \land ggT(a,n) = 1\}|$$
> $\phi(n)$ ist die Anzahl der teilerfremden, natürlichen Zahlen zu $n$ im Bereich $[1,n]$.
> 
> Berechnung der Phi-Funktion
> -	 Wenn $p \text{ ist Primzahl}$, dann $\phi(p) = p -1$
> -	Wenn $p^k \text{ p ist Primzahl und } k \in \N$, dann $\phi(p) = p^k (1 - \frac{1}{p})$
> -	Wenn $m, n \in \N$, dann $\phi(p) = \phi(m) * \phi(n)$

> **Satz von Euler**
> $$a^{\phi (n)} \equiv_n 1, \:\: (a,n \in \N \land ggT(a,n) = 1)$$
> 
> *Beispiel:*
> $7^{222} mod \: 10$
> 1.	$ggT(7,10) = 1, \phi (10) = 4$
> 2.	$7^4 \equiv 1 \: (mod \: 10)$
> 3.	$7^{222} = 7^{4*55 + 2} = (7^4)^{55} * 7^2 = 1^{55} * 7^2 \: (mod \: 10) =49 \: (mod \: 10) = 9$
> 
> **Satz von Fermat**
> $$a^{p-1} \equiv_p 1, \:\: (p \text{ ist Primzahl}, a \in \N, 1 \leq a \leq p-1)$$


### RSA-Verschlüsselung

> **RSA-Verschlüsselung - asymmetrisches Verschlüsselungsverfahren**
> -	Verwendung zur Verschlüsselung und digitaler Signatur
> -	Jeder Teilnehmer benötigt zwei Schlüssel
> 	-	private key (*Entschlüsseln* / *Signieren der Nachricht*)
> 	-	public key (*Verschlüsseln* / *Prüfen der Nachricht*)
>
> **Konstruktion des public key**
> 1.	Wähle zwei sehr große Primzahlen $p$ und $q$
> 2.	$n = p * q$
> 3.	$\phi (n) = (p-1) * (q-1)$ `// siehe Berechnung des Satzes von Euler`
> 4.	Wähle eine zu $\phi (n)$ teilerfremde Zahl $e$ ($ggT(e, \phi (n)) = 1$) mit $1 \lt e \lt \phi (n)$
> 5.	Das Tupel $(n, e)$ ist der public key
> 
> **Konstruktion des private key**
> 1.	Berechne $d$ in ($1 \lt d \lt \phi (n)$) als das multiplikative Inverse zu $e$ in $\Z_{\phi (n)} \rightarrow e * d \equiv_{\phi (n)} 1$ (Berechnung durch den erweiterten euklidischen Alogrithmus)
> 2.	Das Tupel $(n, d)$ ist der private key
> 
> **Verschlüsselung**
> $c$ = Geheimtext
> $m$ = Nachricht  
> $e$ = Teil des öffentlichen Schlüssels des Empfängers
> $n$ = Teil des öffentlichen Schlüssels des Empfängers
> $$c = m^e \: mod \: n$$
> 
> **Entschlüsselung**
> $c$ = Geheimtext
> $m$ = Nachricht  
> $d$ = Teil des privaten Schlüssels des Empfängers
> $n$ = Teil des privaten Schlüssels des Empfängers
> $$m = c^d \: mod \: n$$

*Beispiel Ver- und Entschlüsselung eines Texts mithilfe von RSA:*
1.	Bildung des öffentlichen Schlüssels:
$p = 17, q = 23 \\
n = p * q = 17 * 23 = 391 \\
\phi (n) = (p - 1) * (q - 1) = 16 * 22 = 352 \\
1 \lt e \lt 352$ mit $ggT(e, 352) = 1 \rightarrow$ Wähle $e = 43$

$publickey(391, 43)$

2.	Bildung des privaten Schlüssels:
multiplikatives Inverse:	
Euklidischer Algorithmus
$352 = 8 * 43 + 8 \\
43 = 5 * 8 + 3 \\
8 = 2 * 3 + 2 \\
3 = 1 * 2 + 1 \\
2 = 2 * 1 + 0$

Euklidischer Algorithmus rückwärts:
$1= 3 -2 \\
1 = 3 - (8 - 2*3) \\
1 = 3 * 3 - 8 \\
1 = 3 * (43 - 5 * 8) - 8 \\
1 = 3 * 43 - 16 * 8 \\
1 = 3 * 43 - 16 * (352 - 8 * 43) \\
1 = 131 * 43 - 16 * 352 \\
d = [131]_{352}$

$privatekey(391, 131)$


3.	Verschlüsselung der Nachricht:
$m = 27 \\
c = m^e \: mod \: n = 27^{43} \: mod \: 391= 323$ `missing: Square and multiply`

4.	Entschlüsselung der Nachricht:
$c = 323 \\
m = c^d \: mod \: n = 323^{131} \: mod \: 352 = 257$


### Primzahltests

### Diskreter Logarithmus

### Integrität und Authentizität von Nachrichten
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA4MzcyMzc2MCwtMTQyNTk3NjQ2MywtMT
gwOTM0OTc4NCwxNzM3NTY4MDA4LC0yMTM5MDc2NDk4LDIwNDU4
MjIxNDgsLTE0NzE2MjYyMjYsLTE2NjI2ODAzNTksLTIxMjA0Mz
k5MDIsLTE0MjQyNzI1MzAsMjAzNTEyNTEyLDg2NzE2NTcyNiwx
Njk5MDQwMTAsLTQ2ODQ4MzgyLC0xNzA3MzU2MCwtMTk3NzkxNT
AyOSwtNTQwNjE0MjAzLC0xODA2MDUzNTIxLDQ2NDg2MzkyMCw2
MDY5NzU1MjRdfQ==
-->