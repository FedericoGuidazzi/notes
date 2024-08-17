# Flusso di costo minimo
Il problema del flusso di costo minimo è un problema molto diffuso che si basa su strutture a grafo in cui gli archi sono pesati e orientati.
I nodi in questo problema si distinguono in base al bilancio tra flusso entrante e flusso uscente in:
- nodi di **transito**, sono nodi in cui la capacità di flusso che entra è pari alla capacità in uscita
- nodi **origine** (sorgente), sono nodi in cui la quantità uscente è maggiore di quella entrante
- nodi **destinazione** (pozzo), sono nodi in cui la quantità uscente è minore di quella entrante
In una situazione normale il bilancio complessivo della rete è nullo, ovvero la quantità in ingresso da uno o più nodi sorgente è uguale a quella in uscita dal/dai nodi pozzo.
Un algoritmo di risoluzione di questo problema ha il compito di individuare uno o più percorsi disponibili per instradare il flusso senza che:
- la *capacità degli archi non venga superata*
- il *costo complessivo del flusso sugli archi sia il minimo*
Una volta individuata una soluzione possiamo determinare che sia la migliore o no analizzando il grafico residuo, se **non** ci sono **cicli di costo negativo** allora la **soluzione è la migliore**, nel caso invece questi siano presenti, bisogna agire **reinstradando il flusso** per giungere alla soluzione ottima.
![[Pasted image 20240815144538.png]]
L'algoritmo fino ad ora descritto si focalizza nel trovare una soluzione ammissibile e successivamente perfezionarla per arrivare alla soluzione ottima.
Il prossimo algoritmo invece si focalizza nell'individuare un insieme di cammini minimi che permettono di instradare il flusso dal nodo sorgente a quello pozzo.
## Costo ridotto
Questo algoritmo tiene in considerazione i costi degli archi e la loro portata per andare a individuare la soluzione ottima senza occuparsi di problemi che riguardano il reinstradare il flusso.
La condizione di ottimalità di questo algoritmo è che tutti gli archi abbiano un costo $\ge 0$ dove il costo per ogni nodo è calcolato come $$c_{ij}=c_{ij}+\pi_i-\pi_j$$
L'algoritmo funziona nel seguente modo:
- Per ogni nodo viene calcolata la sua distanza utilizzando SPT (Shortest Path Tree, dijkstra)
- Viene individuato un cammino su cui instradare il flusso
- Vengono calcolati i nuovi costi ridotti per tutti gli archi
- Viene instradato il flusso e viene aggiornato il grafico residuale aggiungendo archi in senso contrario nel cammino
- Ripeto i passaggi precedenti fino a che non avrò instradato tutto il flusso
