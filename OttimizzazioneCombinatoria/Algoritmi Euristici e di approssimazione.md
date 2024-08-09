# Algoritmi euristici e di approssimazione
Gli algoritmi studiati fino ad ora permettono di trovare soluzioni ottime ai problemi che prendiamo in considerazione ma, solitamente, il tempo necessario per arrivare ad ottenerla è molto elevato soprattutto per problemi abbastanza complessi.
Per risolvere il problema della lentezza si può pensare di utilizzare un trade-off che permette di velocizzare il processo di soluzione fornendo una risposta sub-ottima, ma molto spesso abbastanza buona.
## Knapsack approssimato
Il problema knapsack, come detto quando esposto per la prima volta, è uno tra i problemi più complicati che esistano per quanto riguarda la versione che non ammette variabili frazionarie.
Abbiamo visto che può essere risolto in maniera ottima utilizzando una versione del branch and bound, ma è molto costoso a livello computazionale.
Nel caso, quindi, che una soluzione sub-ottima possa comunque essere accettabile e vogliamo prediligere una soluzione veloce piuttosto che ottima possiamo pensare di utilizzare una versione del problema del knapsack euristico.
### Knapsack FPTAS
L'algoritmo del knapsack approssimato è un'evoluzione del knapsack greedy che, in base al livello di accuratezza della soluzione richiesta, può essere più o meno efficiente in modo arbitrario, infatti, modificando l'errore relativo massimo accettabile, l'algoritmo si modifica fornendo soluzioni più o meno vicini all'ottimo (ovviamente più mi avvicino a un errore relativo basso più il tempo computazionale aumenta).
Questo algoritmo ha una complessità esponenziale $$O(n^3\frac{1}{\epsilon})$$
Quindi è un algoritmo di $\epsilon$-approssimazione per knapsack.
## TSP Simmetrico (Commesso viaggiatore)
Il problema del TSP simmetrico è un problema NP completo che consiste nell'individuare un ciclo hamiltoniano nel grafo di partenza.
Un ciclo hamiltoniano è un ciclo in cui tutti i nodi sono visitati una e una sola volta, fatta eccezione del nodo di partenza che funge sia da partenza che da arrivo.
L'algoritmo TSP viene risolto da due algoritmi:
- Double spanning tree, questo algoritmo consiste nella duplicazione di tutti i rami per poi andare a individuare il ciclo hamiltoniano, questo algoritmo è di 1-approssimazione
- Christofides, questo algoritmo individua, analizzando solo i nodi con connessione dispari nel minimum spanning tree, i migliori branch da tenere in considerazione per la costruzione del ciclo hamiltoniano, questo algoritmo è di $\frac{1}{2}$-approssimazione
