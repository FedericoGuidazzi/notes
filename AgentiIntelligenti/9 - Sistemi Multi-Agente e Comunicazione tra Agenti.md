📚 Subject: [[AgentiIntelligenti]]
⬅ [[8 - Modelli di agenti BDI]]

# Sistemi di agenti Distribuiti

I sistemi ad agenti sono solitamente **distribuiti** per vari motivi, di conseguenza è necessaria una **infrastruttura** che **permetta la comunicazione** di questi per portare a termine gli obiettivi che si prefissano.

Ci sono 4 parametri da tenere in conto quando si sviluppa un ambiente distribuito:
- Modularità
- Distribuzione
- Astrazione
- Intelligenza (gestire in maniera intelligente la ricerca e modifica delle informazioni)

 - [9] L'utilizzo di moduli distribuiti combinati a queste 4 tecniche da vita ad un approccio che prende il nome di **Intelligenza Artificiale Distribuita** (**DAI**).

In un ambiente distribuito (**Multi-Agent System**), come detto, gli agenti necessitano una comunicazione e cooperazione per poter riuscire a funzionare in maniera corretta e questo è possibile grazie a dei protocolli per la comunicazione e collaborazione.

## Comunicazione

Gli ambienti multiagente hanno le seguenti caratteristiche:
- Forniscono un'**infrastruttura** per la comunicazione e l'utilizzo di protocolli di interazione.
- Sono progettati per essere **aperti** e **distribuiti**.
- Gli agenti che lavorano in questi ambienti sono **autonomi**, **self-interested** e/o **cooperativi**.

 - [9] La **comunicazione** è **fondamentale** per riuscire a **raggiungere** i loro **obiettivi** o quelli della società/sistema nel quale esistono.

Es: 
L'agente persona ha l'obiettivo di procurarsi della carne, ma non ha la capacità di procacciarsela, si metterà in comunicazione con l'agente supermercato, che ha quella abilità e che come obiettivo ha quello di guadagnare soldi.

Da questo caso possiamo intuire come la comunicazione sia molto **importante** per gli agenti in questo tipo di ambiente.

### Infrastrutture

Le infrastrutture si costituiscono di:
- *Protocolli di comunicazione*, permette agli agenti di capire il contenuto dei messaggi scambiati.
- *Protocolli di Interazione*, permette agli agenti di scambiarsi messaggi (anche strutturati, i.e. una conversazione).

Un protocollo di comunicazione potrebbe permettere azioni come:
- proposta di esecuzione di un’azione 
- accettare una proposta di esecuzione di un’azione
- rifiutare una proposta di esecuzione di un’azione

Un altro componente importante nell'ambito della comunicazione sono le *Ontologie*, che permettono agli agenti di **condividere un linguaggio comune**.

La comunicazione permette agli agenti di **coordinarsi**, in base al rapporto tra questi la proprietà si divide in:
- *Cooperazione*, nel caso gli agenti cerchino di aiutarsi a vicenda. 
- *Negoziazione*, nel caso gli agenti siano antagonisti, competitivi o semplicemente self-interested (in un'asta il compratore e l'offerente sono antagonisti perché cercano di far sì che il prezzo sia quello più conveniente per sé stessi, facendo comunque un azione di coordinazione per portare a termine i loro obiettivi).

### Agent Communication Languages (ACL)

Gli agenti comunicano tra loro scambiandosi messaggi, tra cui anche richieste, gli agenti però sono **self-interested**, quindi possono deliberatamente decidere se **accettare** la richiesta, **rifiutarla** o **ignorarla**.

Gli *ACL*, come KQML e FIPA, sono veri e propri linguaggi utilizzati dagli agenti per scambiarsi informazioni e conoscenza.

Le origini di questi linguaggi derivano dagli anni '90, quando fu avviato un progetto (Knowledge Sharing Effort (*KSE*)), con lo scopo di sviluppare tecniche, metodologie e strumenti software per condivisione della conoscenza e il riutilizzo della conoscenza.

Questo progetto diede origine a 3 linguaggi:
- KQML
- KIF
- Ontolingua

#### KQML

È un linguaggio di alto livello utilizzato per la comunicazione, è indipendente dal:
- Protocollo utilizzato (tcp/ip)
- Linguaggio in cui è espresso il contenuto
- Ontologia utilizzata

Il messaggio consiste di un'azione performativa (scelta tra un pool finito di opzioni) e una lista chiave valore contenente le informazioni da inviare.
Es:
```KQML
(ask-one   <- performativa
	:sender joe 
	:receiver stock-server 
	:reply-with ibm-stock 
	:language LPROLOG <- il linguaggio di rappresentazione del contenuto 
	:content (PRICE IBM ?price) 
	:ontology NYSE-TICKS
 )
 ```

Le **azioni performative** possibili sono:
- *achieve*, il sender vuole che il receiver esegua qualcosa 
- *advertise*, il sender afferma di essere adatto a gestire una certa performativa
- *ask-one*, il sender vuole una delle risposte del receiver alla domanda espressa dal content
- *ask-all*, il sender vuole tutte le risposte del receiver alla domanda espressa dal content
- *reply*, si comunica una risposta attesa
- *sorry*, il sender non può fornire una risposta più specifica
- *tell*, il sender informa il receiver che conosce il content

KQML introduce anche una classe speciale di agenti, che prende il nome di *Broker*, essi hanno informazioni per l'inoltro dei messaggi o l'individuazione dei servizi, e hanno il compito di mettere in comunicazione agenti.
![[Pasted image 20240411150212.png]]

##### Semantica

Inizialmente KQML non aveva una propria semantica, successivamente ne viene introdotta una basata su:
- *Precondizioni*, ovvero lo stato in cui gli agenti devono essere per mandare e ricevere la performativa.
- *Post-condizioni*, ovvero lo stato in cui gli agenti si troveranno una volta inviato e ricevuto il messaggio.
- *Condizioni di completamento*, ovvero lo stato finale dopo che una conversazione è terminata.

```KQML
Pre(A) BEL(A, X) ∧ KNOW(A, WANT(B,KNOW(B, S)))
Pre(B) INT(B,KNOW(B, S))
// dove S pu`o essere BEL(B, X) oppure ¬BEL(B, X)
Post(A) KNOW(A,KNOW(B, BEL(A, X))) 
Post(B) KNOW(B, BEL(A, X)) 
Completion KNOW(B, BEL(A, X))
```

Le condizioni potrebbero anche essere **vuote**.
#### KIF

È un linguaggio utilizzato per dichiarare delle **proprietà** e **relazioni** all'interno di un dominio.
Es:
```KIF
//The temperature of m1 is 83 Celsius
	(= (temperature m1) (scalar 83 Celsius)) 
	
//An object is a bachelor if the object is a man and is not married
	(defrelation bachelor (?x) := (and (man ?x) (not (married ?x)))) 
	
//Any individual with the property of being a person also has the property of being a mammal
	(defrelation person (?x) :=> (mammal ?x))
	
```


#### Ontolingua

Un linguaggio per definire ontologie **condivise**, permettendo di dare **significati uniformi** su **applicazioni diverse** agli stessi concetti.

#### Foundation for Intelligent Physical Agents (FIPA)

È stata creata nel '96 per stabilire uno **standard** per il software per agenti interagenti ed eterogenei e sistemi basati su agenti, il frutto di ciò è stato un linguaggio per la comunicazione degli agenti *simile a KQML*, infatti la principale **differenza** tra i due è la **semantica** e la **mancanza dei facilitatori** (Broker) in FIPA.

La sintassi dei due linguaggi però risulta molto simile.
```FIPA
(inform 
	:sender agent1 
	:receiver agent2 
	:language Prolog 
	:content ‘‘weather(today, raining)’’ 
)
```

##### Semantica

Il *Semantic Language* (*SL*), è il linguaggio che sta alla base della semantica di FIPA.

SL è una logica multimodale basata su operatori modali:
- $B_i$ϕ i crede ϕ 
- $U_i$ϕ i è incerto su ϕ ma pensa che ϕ è più probabile di ¬ϕ 
- $C_i$ϕ i desidera (choice, goal) che ϕ valga correntemente

SL permette un ragionamento sulle azioni, questo avviene attraverso una catena di condizioni, le principali sono:
- *Feasible(a, ϕ)*, a può occorrere e se occorre, ϕ sarà vera dopo tale occorrenza
- *Done(a, ϕ)*, a è appena occorsa e ϕ è vera dopo tale occorrenza
- *Agent(i, a)*, i è il solo agent che esegue l’azione a

Viene, inoltre, definito anche il concetto di **persistent goal** ($PG_i$ϕ), sulla base di belief, choice ed eventi.

Anche in questo caso sono presenti le condizioni, che prendono il nome di:
- Feasibility Precondition (**FP**), condizioni che devono valere per il mittente per poter iniziare la conversazione
- Rational Effects (**RE**), effetti dell'esecuzione di un'azione sull'agente

Tutte le comunicazioni devono essere **Conformi**, ovvero per poter essere avviate devono valere le FP, mentre gli RE non sono garantiti (poiché non è garantito che questi avvengano, in quanto l'agente può decidere di non eseguire l'azione richiesta) e di conseguenza risultano *irrilevanti* per la conformità.

Il linguaggio è basato su due operatori:
- **Inform**
- **Request**
Attraverso i quali, con delle combinazioni, sono sviluppati tutti i rimanenti.

### Semantica Sociale per la comunicazione

La semantica sociale nasce per adattarsi al meglio a situazioni in cui gli agenti sono **eterogenei** e **competitivi**.

- [9] È impossibile fidarsi completamente di altri agenti o fare forti assunzioni a proposito dello stato interno degli agenti e sul loro modo di ragionare

Secondo M. P. Singh, esponente di questa idea di comunicazione, un buon ACL deve essere:
- *Formale*, deve essere **chiaro** e **senza ambiguità**
- *Dichiarativo*, deve descrivere il **cosa** e non il come
- *Verificabile*, deve poter permettere di fare **verifiche** sulle motivazioni dei **comportamenti** degli **agenti**
- *Significante*, trattare la comunicazione **secondo il suo significato** e non solo come un'unione di operatori

La semantica sociale si basa sui **Practical Commitments**, ovvero accordi che un agente (il debitore) prende con un altro agente (il creditore) per eseguire una determinata azione.

I Commitments, per Singh, si compongono di 4 parti:
	C(debtor, creditor, antecedent, consequence)

Es:
	C(Libreria, Alice, $12, Libro), ovvero la libreria dovrà dare il libro ad Alice una volta che lei avrà pagato $12.

Il commitment ha un vero e proprio ciclo di vita
![[Pasted image 20240411182207.png]]
Tra i possibili stati troviamo:
- **Detach**, ovvero l'agente creditore ha terminato le sue azioni (Alice ha pagato i $12)
- **Discharge**, ovvero l'agente debitore ha terminato le sue azioni (Libreria ha dato il libro)


➡ [[]]