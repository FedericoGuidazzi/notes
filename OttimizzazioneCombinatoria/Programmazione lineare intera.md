# Programmazione lineare intera
Un problema di programmazione lineare intera ha lo scopo, dato un insieme di vincoli, di **individuare la migliore soluzione composta solo da un quantitativo intero di oggetti** che appartengono alla soluzione.
È una categoria più **complessa** rispetto alla normale programmazione lineare in quanto in quest'ultima è concesso inserire nella soluzione anche frazioni di oggetti, rendendo di conseguenza il problema più semplice perché ha meno vincoli e di conseguenza un area di soluzioni accettabili più grande.

La programmazione lineare viene identificata come un rilassamento della programmazione lineare intera poiché *la soluzione ottima della programmazione lineare intera è anche una soluzione accettabile della programmazione lineare ma non è sempre vero il contrario*.

## Branch and Bound
Una delle risoluzioni più classiche di un problema di programmazione lineare, sia intera che non, è il branch and bound, ovvero una soluzione che si basa nella costruzione di un albero in cui ogni nodo ha un possibile upper-bound, ovvero la soluzione migliore che quel nodo offre.
L'algoritmo continua ad analizzare ogni nodo e dividerlo in due branch in base a una specifica variabile che si vuole analizzare.
L'analisi da vita a due sotto-nodi che a loro volta saranno associati ad un upper-bound.
L'algoritmo procede nello studiare i nodi con maggiore upper-bound disponibile fino a che non si arriva ad una soluzione che soddisfa.
Per quanto riguarda la programmazione lineare intera, questa soluzione è una soluzione intera con upper-bound maggiore disponibile tra le possibilità individuate, che in questo caso coincide anche con la soluzione **ottima** del problema.
In sostanza quello che questo algoritmo fa è andare a **modificare l'area delle soluzioni ammissibili attraverso dei vincoli che riducono lo spazio**, *tagliando fuori* tutte le *parti che non offrono delle soluzioni in linea con il problema*, successivamente grazie all'utilizzo dell'algoritmo del *simplesso o del simplesso duale* si va ad individuare la **soluzione migliore a partire dall'area modificata**.
## Forma standard
Prima di poter partire con una qualsiasi risoluzione con un qualsiasi algoritmo bisogna portare il problema in una forma standard:
- **Tutti i vincoli devono essere sotto forma di eguaglianza** e non di disequazione, di conseguenza dobbiamo eliminare tutti i vincoli di $\le$ e $\ge$ attraverso l'introduzione di variabili di slack.
  - Se devo eliminare un vincolo di $\le$ aggiungerò una variabile di slack positiva
  - Se devo eliminare un vincolo di $\ge$ aggiungerò una variabile di slack negativa
- La f**unzione obiettivo deve essere espressa come una funzione di massimo**, in caso la funzione di partenza sia di minimo basterà moltiplicare il tutto per -1 e otterrò un problema di massimizzazione
## Soluzione di base
Una soluzione di base è una possibile soluzione del problema che non per forza è ottimale, le soluzione di base per dirsi *ammissibili* hanno bisogno di determinate caratteristiche:
- Non ci devono essere equazioni **ridondanti**
- Non ci devono essere equazioni **incoerenti**
- Il **numero di equazioni deve essere minore del numero di variabili**, così da permettere la risoluzione tramite sistema
## Algoritmo del simplesso
L'algoritmo del simplesso è stato pensato con l'idea di partire da una soluzione ammissibile di base, **muoversi tra soluzioni ammissibili di base adiacenti cercando di migliorare il valore della funzione obiettivo**.
Ovvero cercare di spostarsi nella funzione obiettivo per trovare dei *punti di massimo/minimo che corrispondono anche alla soluzione ottima del problema passato* (cambiando base la soluzione può migliorare).
## Dualità della programmazione lineare
La programmazione lineare è un problema difficile, ma che posso semplificare utilizzando il problema duale.
**Il problema duale permette di ottenere una stima per difetto della soluzione ottima del problema primale**.
Grazie alla stima del problema duale e all'upper-bound della soluzione ottima del primale (offerta da una qualsiasi soluzione di base), posso *riuscire a restringere il campo del range di valori che può avere la soluzione ottima*.
Esistono due tipologie di dualità:
- **Dualità debole**, indica che se uno dei due problemi è illimitato allora l'altro sarà privo di soluzioni ammissibili.
- **Dualità forte**, indica che se uno dei due problemi offre una soluzione ottima, questa sarà ottima anche per l'altro problema.
## Simplesso duale
Una volta capito che **il problema duale risulta più semplice del problema primale**, posso cercare di individuare una soluzione ottima andando a individuare una **soluzione ottima del problema duale**, che grazie alla *dualità forte*, mi garantisce di trovare la **soluzione ottima anche per il problema primale**.
Per fare questo basta utilizzare il simplesso direttamente sulla formulazione del problema primale ma tenendo in considerazione delle accortezze che ci permettono di ottenere un risultato tale e quale quello che avremmo ottenuto formulando il problema duale e poi applicando su questo l'algoritmo del simplesso per come lo conosciamo.
Come nel simplesso devo individuare quella che è la *variabile entrante* e quella che è la *variabile uscente*, per farlo con le nuove regole del simplesso duale seguo i seguenti passaggi:
- Individuo la **variabile uscente** andando a guardare quale delle *variabili in base ha un termine noto minore di 0*, nel caso ce ne siano più di una scegliere a caso.
- Individuo la **variabile entrante** calcolando il rapporto tra il *coefficiente in funzione obiettivo e il coefficiente della variabile nell'equazione che ho individuato al punto precedente*, tenendo in considerazione solo i **coefficienti positivi** e solo i coefficienti negativi nella funzione obiettivo (in caso di coefficienti positivi nella funzione obiettivo comunque ci sono degli errori perché significa che la soluzione che sto considerando non è quella ottima)
Nel caso l'equazione individuata come variabile uscente, abbia, per *tutte le variabili*, *coefficienti negativi*, significa che il **problema duale è illimitato** e di conseguenza, per la dualità debole, il **primale è privo di soluzioni**.
## Tagli di Gomory
Il metodo dei tagli di Gomory è un algoritmo che tenta di **restringere l'area delle soluzioni ammissibili andando ad inserire dei vincoli più specifici**, in sostanza l'idea alla base è *molto simile a quello che fa il branch and bound ma i tagli individuati differiscono*.
Per utilizzare questo metodo si parte sempre da una soluzione di base ottima, si prende in considerazione una delle variabili in base e si utilizza questa formula per individuare il nuovo vincolo da introdurre:
$\sum_j fract(-\alpha_{ij})x_j \ge fract(\beta_i)$
dove $\alpha_{ij}$ è il coefficiente delle variabili (ovvero il coefficiente di $x_1$, $x_2$, ecc) e $\beta_i$ è il termine noto dell'equazione.
Trovata la disequazione con la formula qui sopra si riscrive la disequazione in forma standard, ovvero si inserisce una variabile di slack e successivamente *si riscrive l'equazione in funzione della nuova variabile e si inserisce in base*, dove poi si proseguirà applicando il **simplesso duale** per arrivare alla soluzione ottima disponibile.
## Knapsack
Il problema di Knapsack è uno dei problemi più diffusi e difficili che possiamo individuare, è sostanzialmente un problema di programmazione lineare intera in cui posso scegliere solamente se inserire un oggetto all'interno dello zaino o no.
Per risolvere questo problema ci sono approcci diversi, ma i più diffusi sono il branch and bound e la programmazione dinamica.
### Branch and Bound per Knapsack
L'algoritmo del branch and bound può essere leggermente modificato per riuscire a risolvere al meglio i problemi di knapsack.
Se rilassiamo il problema del knapsack e rendiamo possibile inserire delle quantità frazionarie, otterremo che la **soluzione ottima sarà un insieme di variabili prese nella loro interezza e un solo oggetto frazionario**.
Questo rilassamento ci è molto utile nella soluzione con branch and bound perché ci da la possibilità di avere delle *informazioni a riguardo dell'upper-bound*, che come nell'algoritmo del branch and bound normale, ci *guida nello studio dei nodi generati dalle decisioni*.
L'algoritmo parte con il **riordinamento delle variabili in base al rapporto valore-peso**, così che tutti gli elementi migliori vengano considerati per primi e di conseguenza inseriti con precedenza nello zaino.
Una volta fatto l'ordinamento si parte con la risoluzione del problema, andando ad individuare per ogni nodo **upper bound**, ovvero il valore massimo ottenibile tenendo in conto anche dei valori frazionari delle variabili e il **lower bound**, ovvero il massimo ottenibile senza il rilassamento delle variabili frazionarie.
Nel caso il nodo non si chiuda, ovvero non fornisca una soluzione intera, si creano 2 branch in cui nel primo viene imposta la variabile frazionaria a 0, ovvero fuori dallo zaino, e nel secondo invece viene imposta la variabile frazionaria a 1, ovvero dentro lo zaino. 
L'algoritmo continua finché ci sono nodi aperti che propongono un upper bound maggiore rispetto alla soluzione ottima che ho trovato fino a quel momento (che può essere il lower bound di nodi aperti o l'upper bound se il nodo risulta fornire una soluzione ammissibile).
#### Criteri di dominanza
I criteri di dominanza sono dei criteri che possono essere individuati nelle variabili di partenza.
Questi criteri *permettono di determinare che se una variabile viene inserita in soluzione di conseguenza deve essere inserita per forza anche un'altra e viceversa*.
Questi criteri si basano sull'**individuazione di variabili che hanno peso minore e valore maggiore rispetto ad un'altra variabile**, una volta individuata questa relazione, n**on c'è motivo di inserire nella soluzione solo la variabile che risulta peggiore delle due**.
I criteri di dominanza risultano essere molto utili mentre si sviluppa la soluzione tramite branch and bound perché permette di *eliminare in partenza interi branch che non soddisfano le condizioni individuate rendendo più efficiente l'algoritmo branch and bound*.
### Programmazione dinamica
La programmazione dinamica permette di partire dalle variabili e *studiarle in maniera iterativa per riuscire a formulare la soluzione finale del problema*.
Ci sono due approcci:
- Weight based
- Profit based
L'approccio più diffuso è quello Weight based, che parte dall'analisi di una variabile e via via studia le successive andando a creare una tabella utilizzando la seguente formula:
$$f_k(s)=max \begin{cases} f_{k+1}(s) \ con \ (x_k=0) \\f_{k+1}(s-w_k)+p_k \ con \ (x_k=1) \end{cases} $$
Ovvero, **se è possibile inserire l'oggetto nello zaino e se l'inserimento di questo porta a un valore maggiore a quello che avevo nella stessa situazione ma senza l'oggetto, allora lo inserisco, se no no**.
Una volta costruita la tabella che si basa sul peso, in cui in ogni cella avrò il valore massimo possibile, prendendo *la cella in alto a destra della matrice* (ovvero la casella che ottengo dopo aver analizzato tutte le variabili e dove ho lo zaino con la capienza maggiore) *otterrò la soluzione ottima del problema dello zaino*.
