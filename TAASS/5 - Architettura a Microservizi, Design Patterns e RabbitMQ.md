# Microservizi
I microservizi hanno dato la possibilità di offrire soluzioni che sono più al passo con i tempi, infatti essi permettono una *scalabilità maggiore*, la possibilità di avere *più rilasci* invece che uno singolo alla fine dei lavori, offrono una *affidabilità maggiore* e sono più allineati con la possibilità di *sviluppare ed introdurre feature nuove mentre si sviluppa*.
Un microservizio è un progetto che offre dei servizi e comunica con l'esterno per ottenere informazioni o restituirle, un microservizio è un componente, solitamente autonomo, di una macchina più grande e complessa.
I pro dei microservizi sono:
- La *quantità di azioni* che ricoprono, e di conseguenza, la *quantità di codice* al loro interno è *ridotta*
- *Non è necessario che tutto l'applicativo sia sviluppato con la stessa tecnologia*, andando a dare la possibilità di inserirne di diverse in diversi microservizi
- Solitamente i microservizi sono più *aggiornati e più affidabili* di una applicazione monolitica
- È possibile *scalare* molto più semplicemente
- Essendo codice specifico per dei determinati compiti è più facile *modificarlo e riutilizzarlo*
I contro invece sono:
- *Produttività*, i nuovi developer potrebbero trovare difficoltà ad ambientarsi in applicazioni decentralizzate
- *Interazioni complesse*, se sviluppati male i microservizi possono risultare *chatty*, ovvero scambiano troppi messaggi tra loro, andando a rallentare l'esecuzione
- *Deployment e Monitoring*, quando si va a rendere disponibili i microservizi vanno linkati tra loro e c'è la necessità che venga controllato che tutti siano disponibili, rendendo necessario un tool di deploy e verifica dell'attività
Come detto i microservizi devono essere il più indipendenti possibili, infatti molto spesso, ogni ms ha un suo database specifico, al quale non è possibile in nessun modo accedere direttamente senza passare dal ms.
## Architetture dei Microservizi
Le architetture che si basano sui microservizi sono molteplici, e non esiste la migliore o la peggiore, le architetture vanno scelte dopo un'analisi di quello che è il comportamente richiesto dall'applicativo e delle caratteristiche ricercate per l'interazione con esso.
Per esempio esiste l'architettura **Hub and Spoke**, ovvero è presente un servizio chiamato *API Gateway* che si mette tra il FE e il layer di BE che ha il compito di ridirigere, andando anche in alcuni casi ad aggiungere informazioni o modificare quelle presenti, le richieste al servizio che è specializzato nel task richiesto.
Un altro esempio è l'**architettura ad eventi**, dove tutti i servizi sono in *ascolto su una coda comune* in cui vengono fatte delle richieste.
## Design principles
I microservizi devono essere:
- *Focussati su un singolo compito*
- *Autonomi*
- Basati nella rappresentazione di una *singola funzione di Business o un solo dominio*
- *Resilienti*
- *Osservabili*
- *Autonomi nel notificare problemi*
Devono anche essere presenti *ambienti separati* in base alla fase e al contesto per cui sono utilizzati gli ambienti, devono essere presenti almeno 3 ambienti:
- Sviluppo
- Testing
- Produzione
Le comunucazioni con i microservizi possono avvenire in diverse modalità, quella più classica è il richiamo dell'API direttamente da un applicativo, ma possono esistere anche chiamate indirette causate da un evento come per esempio un webhook, inoltre la comunicazione può essere sincrona o asincrona in base alle esigenze.
# RabbitMQ
RabbitMQ è un servizio che permette la *messaggistica in maniera asincrona*.
È un tool open-source molto utilizzato soprattutto nella comunicazione tra microservizi quando non è necessaria una azione immediata o non è necessario che l'informazione sia processata immediatamente.
RabbitMQ mette a disposizione diverse modalità per lo scambio di messaggi:
- *Direct Exchanges*, i messaggi vengono inviati a uno specifico receiver
- *Fanout Exchanges*, i messaggi vengono inviati a più receiver specificati
- *Topic Exchanges*, i messaggi vengono inviati a tutti i receiver che hanno fatto subscribe di un determinato topic (*publish and subscribe*)
- *Header Exchanges*, utilizza i dati presenti nell'header del messaggio per filtrare i receiver a cui va inviato il messaggio
Questo tipo di servizi danno la possibilità ai due componenti di non preoccuparsi della ricezione dei messaggi e di tutte le logiche di invio e ricezione in quanto il i message broker garantiscono la consegna del messaggio, e altri servizi che garantiscono la funzionalità.
