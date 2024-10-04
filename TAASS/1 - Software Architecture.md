# Architetture Software
Le architetture nel corso degli anni hanno subito *molte modifiche* passando da essere principalmente **server side** a diventare **ibride** e in alcuni casi anche quasi totalmente **client side**, questo è stato possibile grazie al processo tecnologico che ha permesso di avere sempre più potenza di calcolo nei dispositivi che utilizziamo tutti i giorni.
## Central Database
L'architettura a central database è una delle architetture più diffuse e più semplici, consiste in un solo database alla quale tutte le richieste si riferiscono per l'accesso in lettura o scrittura dei dati.
Questa architettura ha vari pro e contro, di conseguenza va studiata prima di essere applicata.
**Pro**:
- *Integrità dei dati*, dato il fatto che è presente un solo db, i dati si trovano tutti in un solo posto e quindi non ci sono problemi di inconsistenza o di duplicazione.
- Avere una sola macchina può portare ad avere *accessi più controllati* e richiedere *autorizzazioni più specifiche*.
- In generale risulta più semplice fare *migrazioni* e *amministrare i dati*.
**Contro**:
- Gli *accessi* sono *limitati* dalla velocità di banda.
- Il *computer centrale* è un *single point of failure*, se va down, il servizio non è più disponibile.
- Se il *database viene compromesso può portare alla perdita di tutti i dati* al suo interno.
- Se qualcuno entra nel computer centrale ha tutti i dati.
- *Scalare* con questa architettura risulta essere *molto complesso*.
Questa architettura prende il nome di **Fat Client**, in quanto praticamente *tutta la logica e di conseguenza la complessità viene gestita dal client*, lasciando al server solo i compiti di rispondere alle chiamate effettuate e di accedere al database.
### Stored Procedures
Per velocizzare questa architettura si possono usare le **stored procedures**, ovvero cercare di *portare la logica a livello di database*, andando a *ridurre le interazioni client-server* e quindi andando a rendere più *efficiente* l'interazione, per esempio facendo ritornare direttamente i dati in una forma utile per essere poi passati al client senza ulteriore passaggi.
Questo metodo può essere utile ma ha lo **svantaggio di non essere portabile** in caso di cambio RDBMS.

## Soluzioni con più database
A differenza dell'architettura Central Database, in questa sono presenti più db che mantengono i dati, andando quindi a eliminare tutti i contro che aveva la precedente architettura riguardo a questa scelta implementativa.
Uno dei principali problemi che troviamo in questa tipologia di architettura è il fatto che i dati devono essere *replicati su più database diversi*, e questo può causare dei *disallineamenti* e dei *problemi di consistenza* dei dati.
A questa situazione non c'è una vera e propria risoluzione, ma si possono utilizzare delle linee guida per cercare di andare a ridurre al minimo i problemi che possono nascere.
Alcuni dei punti fondamentali da mantenere in questa situazione sono:
- Configurabilità dei dati da replicare
- Sincronizzazione automatica dei DB
- Propagazione cambiamenti "al più presto"
- Protezione delle transazioni e integrità referenziale dei dati replicati
- Supporto di RDBMS localizzati sui PC client (mobile computers)
# Middleware
Un **middleware** è un *software utilizzato per riuscire a far comunicare al meglio più parti di una architettura*, per esempio può facilitare lo scambio di informazioni tra client e server andando a gestire le code di richieste o gestire il corretto re-instradamento delle chiamate.
In base alla funzione che svolgono possono essere individuati più middleware:
- TP Monitor
- Message Oriented
- Publish/Subscribe
- Object Request Brokers
- Object Transaction Monitor
## TP Monitor
Un TP Monitor è un middleware con lo scopo principale quello di rendere più semplice e resistente la comunicazione tra parti.
Hanno le seguenti caratteristiche:
- Segue le *proprietà ACID*
- Sincronizzazione in *two phase commit* (per permettere di fare rollback in maniera semplice di informazioni sbagliate o per impedire disallineamenti di dati nei database)
- *Bilanciamento del carico del server*
- *Gestione* del pool di *risorse*
I **Vantaggi** che questo middleware fornisce sono:
- *Scalabilità e tuning* per grandi sistemi
- Maggiore *resistenza nelle applicazioni critiche*
## Object Request Brokers
Questo middleware permette di scambiare dati tra linguaggi ad oggetti diversi attraverso la marshalizzazione e demarshalizzazione dell'oggetto di partenza.
### CORBA
Corba è un ORB che funziona in maniera leggermente diversa rispetto ad un ORB base, infatti invece che fare la marshalizzaione, *viene utilizzato il pattern broker* e il *dynamic binding* per far si che l'oggetto ricevuto sia direttamente un oggetto del linguaggio di programmazione corretto.
Inoltre è anche presente un *middleware* che si occupa di *tutta la comunicazione e il load balancing delle interazioni tra servizi*, che hanno solo bisogno di comunicare quale servizio stanno richiedendo.
## Message Oriented Middleware
Questa tipologia di middleware si occupano dello scambio di messaggi tra diversi servizi attraverso l'utilizzo di code specifiche, i messaggi, una volta inviati, vengono inseriti all'interno di una coda che conserva i messaggi fino a che il server/client legge i messaggi in sospeso.
Per il servizio che manda un messaggio è possibile utilizzare la tecnica **fire and forget**, in quanto il messaggio è garantito che verrà consegnato.
Questi middleware possono essere sia *One-To-One che One-To-Many*, nel secondo caso ci sono delle *policy di subscribe/unsubscribe* alle code contenenti messaggi relativi a un determinato topic.
