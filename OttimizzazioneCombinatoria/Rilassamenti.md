Rilassamento continuo:
	Per ottenerlo basta rimuovere il vincolo di integralità delle variabili.
	Il rilassamento che si ottiene risulta mediamente non una buona soluzione del problema, infatti si può sbagliare fino al 100% delle volte, ma può dare informazioni molto utili per quanto riguarda l'upper bound possibile della soluzione, oltre a garantire una soluzione del primale e del duale ottime.
	
Eliminazione dei vincoli:
	Questo rilassamento parte dalla riscrittura del problema iniziale nella forma
	$max\{ cx : Ax ≤ b , Ex ≤ d , x ∈ Zn \}$
	Ovvero vengono separati i vincoli semplici (Ex) da quelli più complessi (Ax).
	Una volta individuati i vincoli complessi vengono semplicemente rimossi, andando a creare un rilassamento del tipo
	$max\{ cx : Ex ≤ d , x ∈ Zn \}$
	Il rilassamento ottenuto risulta migliore in termini di difficoltà di risoluzione ma non è detto che la soluzione sia polinomiale.
	
Rilassamento Lagrangiano:
	In questo rilassamento viene aggiunta una costante che ha il compito di penalizzare le soluzioni che non rispettano i vincoli posti dalla condizione complessa nel problema (Ax).
	Nel rilassamento in questione, i vincoli difficili vengono inseriti nella funzione obiettivo moltiplicati per un coefficiente u.
	Per esempio:
		$min X \sum_{(i,j)∈A} cijxij$
		$t.c. \sum_{(j,i)∈BS(i)} xji − \sum_{(i,j)∈F S(i)} xij = bi , i ∈ N,$
		$\sum_{(i,j)∈A} lijxij ≤ L,$
		$xij ∈ \{0, 1\}, ∀(i, j) ∈ A,$

Si ottiene un rilassamento del tipo
	$min X \sum_{(i,j)∈A} cijxij + u(L-\sum_{(i,j)∈A} lijxij) = uL+\sum_{(i,j)∈A}(cij-ulij)xij$
		$t.c. \sum_{(j,i)∈BS(i)} xji − \sum_{(i,j)∈F S(i)} xij = bi , i ∈ N,$
		$xij ∈ \{0, 1\}, ∀(i, j) ∈ A,$

Solitamente la soluzione fornita dal rilassamento Lagrangiano risulta essere più efficace ma meno efficiente dei rilassamenti precedenti.

Rilassamento Surrogato:
Questo rilassamento prevede di semplificare tutti i vincoli complessi in un solo vincolo moltiplicato per un vettore y.
Il rilassamento ottenuto non sempre risulta più semplice, infatti, molte volte anche il problema rilassato risulta molto complesso da risolvere.
Solitamente il problema surrogato non viene molto utilizzato in quanto il suo rilassamento può rimanere comunque difficile da risolvere, di conseguenza viene preferito il rilassamento lagrangiano.
La riformulazione del problema secondo questo rilassamento diventa:
$max\{ cx : (yA)x ≤ (yb) , Ex ≤ d , x ∈ Zn \} .$

Decomposizione di Bender:
Questa decomposizione viene fatta sulle variabili e non sulla matrice dei coefficienti, 
