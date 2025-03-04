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
#### Scoring and Ranking
Ogni scoring classifier ha una metrica chiamata **margin**, che indica quante istanze sono classificate in maniera corretta e quante in maniera non corretta.
![[Pasted image 20250302135650.png]]
Quindi il margin viene calcolato come il prodotto tra la classe (che può valere -1 o 1) e lo score (che assume valori maggiori di 0 se la classe è ritenuta positiva e minori di zero se la classe è ritenuta negativa), di conseguenza otterrò che se il margin è positivo allora l'istanza è classificata bene, mentre se è negativo c'è stato un errore.

Dal margin possiamo ricondurci alla **Loss Function**, ovvero una funzione che va a dare una penalizzazione al modello in caso compia degli errori, il funzionamento di queste funzioni si basano sul margin e associano grandi penalità a valori di margin molto negativi e penalità praticamente nulle a margin molto positivi.
Esistono molti tipi di loss function e non ne esiste una migliore, in base a quella che è l'applicazione bisogna andare a individuare quale può essere la più corretta.

È necessario, inoltre, individuare anche l'*error rate* dei modelli ottenuti, la formula per calcolarlo è
![[Pasted image 20250302140431.png]]
Ovvero per tutte le coppie di istanze positive e negative che posso creare in un dataset, analizzo la classificazione fatta e aggiungo un punto di penalità nel caso la classificazione della classe positiva sia inferiore a quella della classe negativa (il che vuol dire che un caso negativo è stato ritornato prima di un caso positivo) oppure aggiungo mezzo punto nel caso che entrambe le classi abbiano lo stesso posto, negli altri casi non aggiungo niente.
**ES:**
![[Pasted image 20250302140914.png]]

Nel caso dei classificatori probabilistici, ovvero quelli che ad ogni foglia dell'albero associano una probabilità di appartenere ad una classe, si può calcolare l'errore in una maniera più efficiente: il **Mean Squared Probability Error**, questo errore fa uso dello squared error per poi fare una media su tutte le istanze dei dati.
Lo squared error è calcolato come segue:
$$\frac{1}{2}||\hat{p}(x)-I_{c(x)}||_{2}^2$$
Ovvero (valore predetto - valore reale)² fratto 2.
![[Pasted image 20250302141720.png]]

La metrica di errore, come detto prima è il Mean Squared Error, che viene calcolato come:
$$MSE(Te)=\frac{1}{|Te|}\sum_{x\in{Te}}{SE(x)}$$
### MultiClass Classification
Oltre la classificazione binaria esiste anche la classificazione con più classi.
La classificazione multiclasse può avvenire in due modi diversi:
- one-vs-rest schema, ovvero una classe viene messa a confronto diretto con tutte le altre contemporaneamente.
- one-vs-one schema, ovvero una classe viene messa a confronto con tutte le altre ma in momenti diversi.
Questa tipologia di classificazione però può avere dei problemi in entrambi gli utilizzi in quanto nello schema one-vs-rest molto spesso c'è uno sbilanciamento tra classi, il che porta poi a dei problemi nell'apprendimento.
Mentre nello schema one-vs-one abbiamo il problema che andiamo a restringere molto il dominio dei dati rimanendo con troppi pochi esempi per ottenere dei buoni risultati.
## Regression
Nella regressione il dato da predirre è un reale, quindi non sono più presenti dei valori finiti da predirre come potevano essere le classi.
Questo problema, essendo molto più complesso della classificazione, è molto più prono al problema dell'overfitting, in quanto molto spesso, per cercare di ottenere dei buoni risultati, si tende a cercare di creare un modello troppo incentrato sui dati di training, il che lo porta a generalizzare con fatica.
Dall'altra parte però, se creiamo un modello che è troppo generale abbiamo il problema dell'underfitting, ovvero il modello non riesce ad estrarre la conoscenza dai dati di training e quindi poi non riesce a predirre con buoni risultati ne sul training ne sul validation set.

I due problemi sopra riportati sono alla base del **bias-variance dilemma**, ovvero:
Un modello con poca complessità soffre meno di varianza ma introduce dei problemi dovuti al bias in quanto non sono state catturate le feature in modo preciso, un modello con molta complessità invece soffre di poco bias perché riesce ad estrarre le caratteristiche dei dati ma soffre di varianza.
Il dilemma può anche essere scritto formalmente nel seguente modo:
![[Pasted image 20250304091736.png]]
## Clustering
I problemi di clustering consistono nell'individuare dei gruppi di dati con caratteristiche simili, questo task può essere sia supervised che unsupervised in base a se le classi vengono fornite oppure vengono individuate in maniera autonoma.
## Association rules
Il problema consiste nell'individuazione di regole di associazione.
ES:
Si vogliono individuare i prodotti che solitamente vengono acquistati insieme (quindi con una causalità) utilizzando gli scontrini.
Il modello che andrò ad addestrare quindi sarà in grado di dire che molto spesso se una persona compra il latte allora compra anche i biscotti (ma non è detto che se si comprano i biscotti allora si compri anche il latte).

Questo problema risulta molto complesso per sua natura perché per ogni istanza devo studiare tutti i rapporti con le altre istanze sia in maniera singola sia in gruppo, andando così a richiedere una complessità computazionale molto elevata.