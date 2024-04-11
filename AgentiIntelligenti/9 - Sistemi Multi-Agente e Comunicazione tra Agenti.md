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

## Agent Communication Languages (ACL)

Gli agenti comunicano tra loro scambiandosi messaggi, tra cui anche richieste, gli agenti però sono **self-interested**, quindi possono deliberatamente decidere se **accettare** la richiesta, **rifiutarla** o **ignorarla**.

Gli *ACL*, come KQML e FIPA, sono veri e propri linguaggi utilizzati dagli agenti per scambiarsi informazioni e conoscenza.

Le origini di questi linguaggi derivano dagli anni '90, quando fu avviato un progetto (Knowledge Sharing Effort (*KSE*)), con lo scopo di sviluppare tecniche, metodologie e strumenti software per condivisione della conoscenza e il riutilizzo della conoscenza.

Questo progetto diede origine a 3 linguaggi:
- KQML
- KIF
- Ontolingua

### KQML

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

### KIF

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


### Ontolingua

Un linguaggio per definire ontologie **condivise**, permettendo di dare **significati uniformi** su **applicazioni diverse** agli stessi concetti.

➡ [[]]