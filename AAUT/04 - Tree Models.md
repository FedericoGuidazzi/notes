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