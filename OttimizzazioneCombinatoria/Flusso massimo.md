# Flusso massimo
Il problema del flusso massimo, consiste, dato un grafo pesato, si cerca la quantità massima di flusso che può essere instradata nel grafo a partire da un nodo sorgente fino ad arrivare al nodo pozzo.
Una soluzione è ammissibile se:
- Il bilancio ai nodi risulta rispettato, ovvero la somma del flusso entrante è uguale al flusso uscente per tutti i nodi che non sono ne pozzo ne sorgente
- Su ciascun arco, la quantità di flusso instradato è minore della portata massima
L'algoritmo proposto per risolvere il flusso massimo è di tipo greedy, ovvero si muove sempre verso un ottimo globale non mettendo in discussione quelle che sono le decisioni prese in precedenza.
Vengono individuati i cammini attraverso un implementazione DFS e poi viene instradato ogni volta il flusso maggiore possibile.
A questo processo si aggiunge anche la possibilità di fare reinstradamento del flusso per poter arrivare alla soluzione ottima del problema.
Il problema del flusso massimo ha ora un algoritmo (più di uno) che permette di trovare una buona soluzione.

## Algoritmo di Ford-Fulkerson/Edmond & Karp
Entrambi gli algoritmo forniscono una soluzione al problema del flusso massimo, infatti, differiscono solo per la modalità di individuazione del cammino che collega s e t.
Per quanto riguarda Ford-Fulkerson non viene specificato un metodo specifico per l'individuazione del cammino aumentante, che infatti può essere trovato con un qualsiasi metodo che può portare a un miglioramento o peggioramento della complessità computazionale in base all'algoritmo utilizzato.
Per quanto riguarda, invece, Edmond & Karp l'algoritmo è scelto di partenza ed è il **DFS**, che permette di individuare sempre il cammino con lunghezza più breve.
Entrambi gli algoritmi sono di complessità polinomiale, ma per quanto riguarda Edmond & Karp, si può applicare anche un ulteriore stratagemma
### Capacity scaling
Questo stratagemma consiste nel cercare sempre il cammino con distanza minima ma con portata maggiore, così da saturare prima tutti i cammini più brevi e con maggiore portata, andando a limitare il numero delle iterazioni necessarie per ottenere una soluzione.


