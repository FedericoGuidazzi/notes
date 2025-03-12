Il concept learning è un metodo di apprendimento che si basa nell'individuazione di feature che caratterizzano l'appartenenza dell'oggetto ad una classe.
In base alle caratteristiche l'algoritmo impara un inductive bias, ovvero un insieme di concetti che utilizza per arrivare al fine, a partire da degli esempi forniti da un oracolo (esempi etichettati).
Una volta ottenuta la conoscenza sotto forma di bias, posso utilizzarla per applicare la conoscenza a esempi non ancora visti.
Attraverso l'allenamento della rete posso andare a modificare il bias andando a renderlo più o meno ampio, così da ottenere il miglior risultato possibile durante la fase di utilizzo del modello ottenuto.
Questa tipologia di apprendimento studia le caratteristiche cercando di individuare una regola generale per riuscire ad arrivare alla soluzione attesa, questo approccio permette anche di studiare in maniera specifica quale è stato il processo che ha portato il modello ad arrivare ad un risultato piuttosto che un altro, andando così ad evitare il problema della black box.

L'appendimento, come detto parte dalle caratteristiche cercando di andare a estrarre una regola che permette di arrivare alla conclusione, questa regola può essere più o meno generale, il che poi va ad individuare un'area dei punti maggiore o minore, il fatto di andare a studiare singolarmente le feature comporta anche la possibilità di classificare le regole ottenute in più o meno specifiche, concetto fondamentale per gli algoritmi che tratteremo in seguito, in quanto permette lo studio specifico dello spazio delle soluzioni.

Bisogna sempre ricordare però che il funzionamento di questa tipologia di algoritmi si basa su due ipotesi:
- Lo spazio che posso descrivere con l'utilizzo delle sole feature può generare almeno una soluzione.
- I dati di training non contengono errori ovvero non c'è rumore ed è consistente con i dati che poi daremo in pasto al modello.