## Classification
Un classificatore è un modello che dato un insieme di dati restituisce per ogni stanza una classe al quale il dato appartiene, ovvero cerca di creare un insieme $\hat{c}$ quanto più vicino all'insieme $c$ .
### Binary Classification
Un classificatore binario è un classificatore che deve distinguere 2 classi.
#### Valutazione
Un modo per la creazione di un classificatore binario è l'utilizzo del **feature tree**, ovvero un albero in cui i nodi sono le feature per il quale si dividono le istanze e nelle foglie ci sono le istanze delle classi, si vuole creare l'albero che riesca ad avere nelle foglie il minor numero di errori.
![[Pasted image 20250222103554.png]]
Un **decision tree** è l'evoluzione del feature tree in cui nelle foglie ho la classe che assegnerò alle istanze che compongono la popolazione della foglia, per la creazione del decision tree ci si basa su quello che viene individuato dal feature tree, molto spesso infatti si da come classe quella con più istanze nella foglia, ma non è detto, per esempio nel caso in cui voglia dare un costo maggiore ai falsi positivi piuttosto che ai falsi negativi, il basarsi solamente sulla classe con la popolazione maggiore potrebbe non essere abbastanza.
![[Pasted image 20250222103856.png]]
Alla base di tutto possiamo individuare la contingency table, ovvero una tabella in cui vengono inseriti l'insieme delle classificazioni, ovvero TP (True Positives), TN (True Negatives), FP (False Positives), FN (False Negatives).
![[Pasted image 20250222104114.png]]

La valutazione del modello può essere fatta su varie metriche in base a quello che si vuole andare a misurare, le metriche più utilizzate sono la **precision** e la **recall**, ma non sono le uniche.
![[Pasted image 20250222104308.png]]

Per la valutazione dei modelli in maniera grafica, si può utilizzare il **ROC plot**, ovvero un diagramma sul quale posiziono i modelli e attraverso cui posso riuscire a individuare quale è il migliore andando a tenere in considerazione le diagonali del diagramma.![[Pasted image 20250222104538.png]]

Utilizzando la combinazione tra feature tree e ROC plot, posso inoltre andare a individuare quale insieme di feature individuate nell'albero genera il modello migliore.
Per esempio, a partire dall'albero introdotto precedentemente, possiamo andare a creare vari tagli basandoci sulle feature individuate, una volta ordinate queste in base al criterio di valutazione in ordine decrescente, possiamo andare a inserire i punti all'intero del ROC plot e attraverso l'utilizzo delle diagonali, possiamo andare ad individuare quale dei modelli risulta il migliore.
![[Pasted image 20250222104837.png]]
Nell'esempio esposto il costo degli errori è uguale (FP e FN sono trattati nello stesso modo), nel caso in cui si voglia variare questa cosa, basta andare a variare la diagonale che utilizziamo per andare a individuare quale è il modello migliore.
![[Pasted image 20250222105040.png]]