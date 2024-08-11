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
## TSP Metrico (Commesso viaggiatore)
Il problema del TSP metrico è un problema NP completo che consiste nell'individuare un ciclo hamiltoniano nel grafo di partenza.
Un ciclo hamiltoniano è un ciclo in cui tutti i nodi sono visitati una e una sola volta, fatta eccezione del nodo di partenza che funge sia da partenza che da arrivo.
L'algoritmo TSP viene risolto da due algoritmi:
- Double spanning tree, questo algoritmo consiste nella duplicazione di tutti i rami per poi andare a individuare il ciclo hamiltoniano, questo algoritmo è di 1-approssimazione
- Christofides, questo algoritmo individua, analizzando solo i nodi con connessione dispari nel minimum spanning tree, i migliori branch da tenere in considerazione per la costruzione del ciclo hamiltoniano, questo algoritmo è di $\frac{1}{2}$-approssimazione

# Dimostrazioni
## Knapsack greedy è un algoritmo di 1-approssimazione
Knapsack implementato con un algoritmo greedy funziona nel seguente modo:
- Si riordinano le variabili in rapporto al valore/peso decrescente
- Si prendono quante più variabili possibili all'interno della soluzione fino a che lo zaino non è pieno/non ci stanno più elementi
- In caso venga individuato un elemento che fornisce una soluzione migliore rispetto a quella individuata fino a quel momento, viene buttata via la soluzione di prima e inserito il nuovo elemento
Per dimostrare che l'algoritmo è di 1-approssimazione, si parte dall'assunzione $$\frac{OPT}{A}\le \frac{\mu_\beta}{A}$$ Ovvero la soluzione ottima fratto la soluzione individuata (euristica) è minore dell'upper bound individuato fratto l'euristica.
Di conseguenza si può dire che $$\frac{\mu_\beta}{A}=\frac{p_1+p_2+\dots+\alpha p_s}{A}$$
In quanto l'upper bound viene costruito come la somma di i valori delle variabili che è possibile inserire nello zaino più una frazione della variabile critica che non entra nella totalità all'interno dello zaino.
Possiamo inoltre dire che $$\frac{p_1+p_2+\dots+\alpha p_s}{A}\le\frac{p_1+p_2+\dots+ p_s}{A}$$
In quanto il parametro $\alpha$ era sicuramente una frazione minore di 1.
Successivamente possiamo scorporare l'equazione in questo modo $$\frac{p_1+p_2+\dots+ p_s}{A}\le 1+\frac{p_s}{A}$$
In quanto la sommatoria dei p escluso l'oggetto critico è la soluzione proposta dall'euristica e di conseguenza è uguale al valore di A, infine $$1+\frac{p_s}{A}\le 2$$
In quanto sicuramente il valore di $\frac{p_s}{A}$ sarà inferiore a 1, in quanto per costruzione del problema, se $p_s$ fosse maggiore di $A$ ovvero della soluzione fornita dall'euristica, $p_s$ diverrebbe la nuova soluzione del problema eliminando tutta la parte precedente.
Attraverso questa dimostrazione possiamo quindi dire che $$\frac{OPT}{A}\le1+\epsilon \le 2$$ e di conseguenza $\epsilon$ al massimo può valere 1, di conseguenza l'algoritmo è 1-approssimazione.
(Nel caso voglia tenere in considerazione la formula alternativa $\frac{A}{OPT}\le1-\epsilon$, l'algoritmo sarebbe di $\frac{1}{2}$-approssimazione, in quanto $\epsilon$ potrebbe valere al massimo $\frac{1}{2}$).
## Knapsack greedy migliorato, approssimazione $\frac{1}{k}$
Questa versione del knapsack funziona in modo leggermente diverso da quello di base, andando a fornire una soluzione che può essere resa più corretta o meno andando a lavorare su un parametro k (più la soluzione sarà precisa, più il tempo per trovarla sarà elevato).
- L'algoritmo parte sempre con l'individuazione della scala di scelta delle variabili basate sul rapporto valore/peso.
- Successivamente, invece che procedere direttamente con l'algoritmo greedy per individuare le variabili da inserire nello zaino, si seleziona l'insieme composto da k variabili migliore presente (questo è possibile analizzando tutte le permutazioni di k elementi prendendo l'insieme con valore/peso migliore) e poi si continua a riempire lo zaino con un approccio greedy.
Questa modifica va a rallentare l'algoritmo, ma fornisce una soluzione che può essere modificata a piacimento per aumentarne l'accuratezza.
La dimostrazione dell'accuratezza è la seguente:
La soluzione ottima e quella euristica avranno almeno k elementi uguali, in quanto vengo fissati all'inizio e non vengono più modificati, quello che cambia tra le due soluzioni è il completamento della parte rimasta libera attraverso l'algoritmo greedy.
![[Pasted image 20240810141421.png]]
$$\frac{OPT}{A}=\frac{p(s^*)}{p(s)}=\frac{p(E)+p(H^*)}{p(s)}$$
Una volta stabilito questo, posso scomporre ulteriormente $p(H^*)$ nella sommatoria dei valori che rientrano nello spazio rimanente ($H^1$) + l'elemento critico che non entra nello spazio, di conseguenza:$$\frac{p(E)+p(H^*)}{p(s)}\le\frac{p(E)+p(H^1)+p_r}{p(s)}$$
Dalla scomposizione però, quello che ottengo è la somma della soluzione che mi fornisce l'euristica (ovvero $p(E)+p(H^1)$) sommato a un elemento che non posso inserire all'interno dello zaino in quanto non ci sta nella sua interezza, di conseguenza posso riscrivere come: $$\frac{p(E)+p(H^1)+p_r}{p(s)}=\frac{p(s)+p_r}{p(s)}=1+\frac{p_r}{p(s)}$$
Da questo posso ulteriormente dire che sicuramente $p(s)\ge kp_r$ in quanto se no avrei inserito $p_r$ al momento della scelta dei k elementi iniziali, di conseguenza posso dire che $$1+\frac{p_r}{p(s)}\le1+\frac{1}{k}$$
## Knapsack con soluzione FPTAS
![[Pasted image 20240810185037.png]]
## Double Spanning Tree, 1-approssimazione
Data una soluzione del problema del commesso viaggiatore utilizzando il metodo del DST ottengo una soluzione ($c(c)$) che sicuramente avrà un costo inferiore rispetto al doppio del costo del minimum spanning tree generato al primo passaggio dell'algoritmo DST, questo perché nella soluzione abbiamo inserito delle scorciatoie che, quindi, riducono il costo. $$C(c)\le2C(t)$$
Possiamo inoltre notare che un qualsiasi ciclo euleriano, è uno spanning tree al quale manca un arco di collegamento per creare il ciclo, di conseguenza avrò che $C(t)\le OPT$ di conseguenza posso concludere che $$C(c)\le2C(t)\le2OPT$$
Essendo che C(c) non è altro che il nostro A ovvero la soluzione fornita dall'algoritmo euristico, posso concludere che $$\frac{A}{OPT}\le2$$
## Christofides, $\frac{1}{2}$-approssimazione
Questo algoritmo risulta essere migliore rispetto ad un approccio DST in quanto inserisce una logica di matching per l'individuazione dei migliori archi da tenere in considerazione durante la costruzione del ciclo euleriano.
Questo algoritmo è di $\frac{1}{2}$-approssimazione in quanto $$A\le C(t)+C(m)$$
Ovvero la soluzione che individuo con l'euristica è minore del costo del minimum spanning tree sommato al costo del matching che introduco (ovvero il costo degli archi che inserisco per collegare i nodi di grado dispari).
$C(t)\le OPT$ come abbiamo visto prima in quanto al minimum spanning tree manca l'arco di collegamento che fa chiudere il ciclo euleriano.
Per quanto riguarda invece il costo del matching passiamo prima dall'individuazione di cicli di costo minore che posso individuare nel ciclo euleriano individuato
![[Pasted image 20240810160336.png]]
Infatti aggiungendo delle scorciatorie, per la caratteristica del problema, ovvero la metricità posso dire che $$C(c^1)\le C(c)=OPT$$
da questo posso dire che la somma dei matching, non ottimali, come quelli individuati nel ciclo $c^1$ è sicuramente inferiore al doppio di $C(m)$, ovvero il matching ottimo individuato nel ciclo di partenza, per cui $$2C(m)\le C(m_1)+C(m_2)$$
Dove la somma dei costi dei matching è minore uguale a $C(c^1)$, di conseguenza $$2C(m)\le C(m_1)+C(m_2)\le C(c^1)\le C(c)=OPT$$
Quindi $$2c(m)\le OPT$$ovvero $$c(m)\le \frac{1}{2}OPT$$
Tornando alla formula individuata in precedenza $$A\le C(t)+C(m)$$
possiamo quindi concludere che $$A\le OPT+\frac{1}{2}OPT$$ovvero $$A\le\frac{3}{2}OPT$$