## Features Tree
Questo tipo di alberi sono caratterizzati da nodi che riguardano delle feature presenti all'interno dei dati di training, più si naviga l'albero più si vanno a cercare esempi specifici, nelle foglie dell'albero sono presenti l'insieme delle istanza che verificano tutte le ipotesi poste fino a quel momento.
Questa tipologia di alberi possono anche essere utilizzati come classificatori, la differenza principale è che le foglie ora determinano la classe di appartenenza delle istanze e non mantengono più le statistiche delle classi.
![[Pasted image 20250324084305.png]]
L'apprendimento che viene fatto su una struttura ad albero è lo studio dello spazio delle ipotesi e vie via vengono inseriti o eliminati nodi di split per arrivare all'obiettivo atteso, è possibile addestrare anche in parallelo così da testare i dati su più alberi e su split diversi.
L'addestramento degli alberi è molto simile per ogni task che deve servire.
![[Pasted image 20250324085720.png]]
Descrizione delle funzioni:
- **Homogeneous(D)**, ritorna vero se le istanze in D sono abbastanza omogenee da essere etichettate in una sola label.
- **Label(D)**, ritorna la label da assegnare al nodo foglia.
- **BestSplit(D,F)**, ritorna la migliore feature per essere inserita come nodo e la lista delle istanze rimanenti.
Queste funzioni variano leggermente in base a quale è il task obiettivo.
### Decision Tree
Lo scopo di un albero di questo tipo è il cercare di creare delle foglie più omogenee possibili, ovvero dove l'entropia sulle foglie è la minore possibile.
Per riuscire a valutare quale delle opzioni che mi si presentano è la migliore posso utilizzare delle metriche di impurità, le più popolari sono:
- Minority class, ovvero la quantità di errore che commetterei se classificassi tutti gli esempi della foglia con la classe di maggioranza $min\{p,1-p\}$
- Gini index, ovvero l'errore che c'è da aspettarsi se un'instanza fosse classificata a caso $2p(1-p)$
- Entropy, ovvero la quantità di informazioni attesa contenuta in un messaggio che ci comunica la classe di un'instanza che appartiene alla foglia $-p\log_2(p)-(1-p)\log_2(1-p)$
Attraverso il calcolo dell'impurità posso individuare quale split risulta il migliore da eseguire date le Feature possibili e il Dataset con gli esempi, grazie a questa metrica, infatti, possiamo andare a implementare la funzione *BestSplit(D,F)*, che ha il seguente pseudocodice:
![[Pasted image 20250327083711.png]]
### Ranking and probability estimation tree
Lo scopo di questi alberi è la divisione in segmenti del dominio degli esempi e il loro ordinamento in base alla classificazione fatta partendo dagli esempi ricaduti nelle foglie, è possibile anche variare il peso delle istanze che sono state classificate non correttamente per andare a variare quello che è il ranking generato.
Questa tipologia di alberi viene fatta crescere, ovvero il nodo padre conterrà tutti gli elementi che sono contenuti nei nodi figli, di conseguenza quello che si va a prendere in considerazione sono solo le foglie, in quanto i nodi servono solo da split e non mantengono informazioni importanti per la classificazione.
Per il ranking si parte quindi dalle foglie e si analizza la composizione di queste tenendo anche in considerazione un eventuale costo aggiuntivo nel caso di istanze classificate male, successivamente si ordinano le foglie il che determina il ranking.
È, inoltre, possibile anche la visualizzazione dell'abero in uno spazio ROC per andare a confrontare i modelli in maniera grafica.
![[Pasted image 20250327084932.png]]
Per la classificazione delle foglie in classe positiva o negativa si vanno a vedere le istanze presenti e il costo da applicare e successivamente si va a vedere quale delle classi risulta la migliore.
Come vediamo dall'immagine a variare del costo potrebbe accadere che viene totalmente trascurata la popolazione della foglia, è quindi necessario andare ad individuare un costo corretto che non vada a far perdere di significato l'albero costruito.
![[Pasted image 20250327085209.png]]