# Rilassamenti
Uno dei punti fondamentali per riuscire a risolvere un problema di OC è individuare un upper bound in grado di guidarci nel successivo raffinamento della soluzione e di stimare la bontà di una soluzione.
Un rilassamento di un problema consiste nel rimuovere dei vincoli per far si che sia possibile trovare più facilmente una soluzione, fornendo una soluzione che però molto spesso risulta non del tutto compatibile con il problema iniziale, fornisce comunque delle informazioni molto importanti per poi riuscire e guidare la soluzione verso una accettabile.
Esistono vari tipi di rilassamenti:
- Rilassamento continuo
- Rilassamento per eliminazione di vincoli (o combinatorio)
- Rilassamento Lagrangiano
- Rilassamento surrogato
I rilassamenti si basano tutti su un trade-off tra efficacia ed efficienza:
- **Efficacia**, qualità della soluzione prodotta (in un mondo ideale vorremmo che la soluzione data dal rilassamento sia la stessa che otterrei senza)
- **Efficienza**, tempo necessario per ottenere la soluzione
Per ogni istanza dobbiamo valutare quale delle due caratteristiche risulta quella più importante così da decidere che approccio prendere (preferire una risoluzione veloce a scapito della qualità della soluzione oppure preferire la qualità della soluzione aspettando molto tempo per ottenerla?)
## Rilassamento continuo
Il rilassamento continuo è un rilassamento che lavora sull'eliminazione del vincolo di continuità andando ad accettare anche soluzione non intere, ovvero, dato un problema del tipo: $$P=max(cx:Ax\le b, x \in \mathbb{Z}^n_+)$$
Lo vado a rilassare, trasformandolo in un problema del tipo: $$P=max(cx:Ax\le b, x \ge 0)$$
La soluzione una volta ottenuto il rilassamento è molto *efficiente* e semplice da ottenere ma molto spesso l'*efficacia è pessima*.
Molto spesso la soluzione ottenuta con questo rilassamento risulta essere quasi inutilizzabile in quanto il vincolo sull'interezza è molto importante, quello che otteniamo però con la soluzione di questo rilassamento è una soluzione ottima del problema primale e del problema duale, utilizzando queste soluzioni ottime come guide per dei metodi di arrotondamento posso ottenere delle soluzioni più buone rispetto a quella di partenza.
## Rilassamento per eliminazione di vincoli
Questa tipologia di rilassamento semplifica il problema iniziale andando a studiare i vincoli presenti, individuando quelli semplici, che permetterebbero di risolvere il problema in modo molto efficiente, e quelli difficili che non rendono possibile l'applicazione degli algoritmi di risoluzione classici.
La formulazione del problema diventa quindi la seguente: $$max\{ cx : Ax ≤ b , Ex ≤ d , x ∈ \mathbb{Z}^n \}$$
Dove i vincoli $Ax ≤ b$ sono quelli complicati, mentre i vincoli $Ex ≤ d$ sono quelli ritenuti semplici.
Il rilassamento quindi elimina i rilassamenti complessi, mantenendo unicamente quelli ritenuti semplici, ottenendo una nuova formulazione del tipo: $$max\{ cx :  Ex ≤ d , x ∈ \mathbb{Z}^n \}$$
## Rilassamento Lagrangiano
Il rilassamento Lagrangiano è un rilassamento che mette in funzione obiettivo i vincoli complessi moltiplicati per un coefficiente. Questo serve per poter permettere che i vincoli non siano rispettati, ma quando questo avviene viene data una penalità.
Partendo da un problema della forma $$max\{ cx : Ax ≤ b , Ex ≤ d , x ∈ \mathbb{Z}^n \}$$
Il rilassamento Lagrangiano lo trasforma in $$max\{ cx + u(b-Ax) : Ex ≤ d , x ∈ \mathbb{Z}^n \}$$
Come si può notare, quindi, è stata rotta la prima disequazione portando a sinistra tutte le variabili e moltiplicandole per uno scalare $u$, è da tenere in considerazione che se la disequazione cambia di segno anche lo scalare lo deve fare per mantenere delle soluzioni ammissibili.
## Rilassamento surrogato
Questa tipologia di rilassamento lavora sui vincoli complessi andandoli a raggruppare in un solo vincolo attraverso dei moltiplicatori $u$.
In problema di partenza $$max\{ cx : Ax ≤ b , Ex ≤ d , x ∈ \mathbb{Z}^n \}$$
Viene riformulato come $$max\{ cx : (uA)x ≤ (ub) , Ex ≤ d , x ∈ \mathbb{Z}^n \}$$
Questo rilassamento quindi agisce sui vincoli complessi andandoli a riunire in un solo vincolo che però molte volte continua ad essere complesso, in queste situazioni non ho un grande vantaggio nell'utilizzo di questo rilassamento, proprio per questo non trova molta applicazione nella pratica in confronto al rilassamento Lagrangiano visto prima
## Scomposizione di Bender
La scomposizione di Bender è un altro approccio per riuscire a semplificare un problema a cui non riusciamo a dare una soluzione a causa della grande complessità.
A differenza dei rilassamenti visti fino ad ora, questa scomposizione, agisce direttamente sulle variabili ritenute complesse piuttosto che sui vincoli.
Il funzionamento di questo approccio si basa sull'individuazione di un problema master e uno slave.
Il master serve per trovare una soluzione attraverso l'eliminazione di vincoli, cercando di mantenere solo quelli che hanno una risoluzione immediata.
Il problema slave invece sarà quello formato da tutti i vincoli che erano stati scartati dal problema master e verrà risolto utilizzando il duale.
Successivamente, in base al risultato ottenuto applico dei tagli e ripeto gli step precedenti fino ad arrivare ad avere la soluzione ottima del problema di partenza.
![[Pasted image 20240817161411.png]]
