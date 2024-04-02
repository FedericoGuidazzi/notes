Subject: [[AgentiIntelligenti]]
I trend che hanno caratterizzato la computazione sono stati:

* **Ubiquità**, ovvero il fatto che con lo sviluppo tecnologico, i dispositivi informatici sono disponibili quasi ovunque, è quindi utile poterli utilizzare per risolvere task specifiche in autonomia.
* **Interconnessione**, è importante che i dispositivi possano comunicare tra loro in modo che possano interagire e influenzarsi per riuscire a risolvere il task nel miglior modo possibile
* **Intelligenza**, la complessità dei compiti che possiamo affidare alle macchine è sempre maggiore a causa del fatto che l'intelligenza dei dispositivi continua ad aumentare e di conseguenza i casi in cui risultano utili
* **Delega**, consiste nell'affidare un determinato task ad una macchina che si occuperà di portarlo a termine
* **Human-orientation**, creare programmi che permettano agli utenti di interfacciarsi alle macchine nel modo più semplice possibile
Questi 5 punti ci portano alla conclusione che necessitiamo di sistemi informatici che possano agire in **maniera indipendente**
e che **agiscano nei nostri interessi**, portando a termine task affidati.

L'interconnessione di questi sistemi informatici porta al fatto che questi debbano **cooperare e raggiungere accordi** oppure **competere** tra loro.

L'interconnessione di questi sistemi informatici porta allo sviluppo dei sistemi **multi agente**.

Ma che cosa è un agente? **Un agente** è un sistema di computazione, un sistema informatico, capace di **agire in modo indipendente** per conto di un utente o proprietario (capendo cosa deve essere fatto per soddisfare gli obiettivi di progettazione, piuttosto che essere costantemente informato).

Che cosa è un sistema multi agente? **Un sistema multi agente** consiste in una serie di agenti, che **interagiscono** l’uno con l’altro. Nel caso più generale, gli agenti agiscono per conto di utenti con differenti obiettivi e motivazioni.

Per interagire con successo, richiedono la capacità di **cooperare**, **coordinarsi** e **negoziare** tra loro, **in modo analogo a quanto fanno le persone**.

Un agente in sostanza è un sistema di computazione, capace di agire **autonomamente** in un qualche **ambiente** per portare a termine gli **obiettivi** per il quale è stato progettato.

**![](https://lh7-us.googleusercontent.com/GReEvrc0o3lEf5EtrmegAuGAw3QbBu42ZYjIWK2u3Wf3JR79tu_HWPf3BGCQXY9P0pP31EaoyxRuI_LsNsuSmCT2F_CCET2lZ2YmqC7h_3jsAOfryhnk3dgl5B7JOzvp4s2_IxO-orDoyfWURBjsbUc)**

Un esempio di agente può essere il cruise control, che analizza l'ambiente circostante per poter decidere se frenare o accelerare, oppure più semplicemente un termostato che in base alla temperatura che rileva (ambiente) decide se accendere o spegnere il riscaldamento.

Per intelligente, non si intende che il programma riesce a capire la situazione e agire di conseguenza, il programma non capisce, segue solo il set di istruzioni che sono state specificate, infatti con la parola intelligente si intende un sistema che riesce a portare a termine un obiettivo che avrebbe richiesto l'intelligenza di un essere umano.

Di conseguenza l'intelligenza sta nel fatto che lo sviluppatore riesce a individuare le casistiche specifiche del dominio di applicazione in modo da riuscire a dare un set di possibili decisioni che l'agente prenderà in maniera autonoma in base all'ambiente in cui opera.

Un agente intelligente è quindi un sistema che prende decisioni in maniera **autonoma** e **flessibile** in un determinato **ambiente**.

Per flessibile si intende:

* **reattivo**, per reattività si intende la capacità di **adattare le decisioni all'ambiente su cui opera**, che per natura è dinamico e quindi cambia nel tempo. 
Questa reattività sono in sostanza delle decisioni if then che non hanno bisogno di "**ragionamento**" (se l'auto davanti frena -> freno). 
**![](https://lh7-us.googleusercontent.com/NSmrLh8kbmuDA574BpiWI0gUNyu8TVErlJufNmiLE64DMtKj_MZelIVTH6lOmrBmR8UiSGVfCxq39tYRPvH0DGe2dARIQGviRmCqF0oG0VcI5A12-HbhjnU757nHa4af20d5_vDU32ZMThStNUhGnzU)**
* **proattivo**, con questo termine si intende che gli agenti non debbano essere solamente guidati dagli eventi, ma devono agire in prima persona per tentare di raggiungere gli obiettivi, quindi **prendere l'iniziativa**. 
Di conseguenza è necessario che l'agente faccia simulazioni di eventuali azioni che può effettuare per andare a calcolare l'impatto dell'azione. 

**![](https://lh7-us.googleusercontent.com/UHQ_y8J6BNlq5lndLezKNwUOtRLw3edTnKUdc5CtyeNjW6aFvijkPscbwspsG4qNor7X548lWXm8HPIph40qCHYL6DutazoI5JytoYk_25Nw7WTTn6KQb4QObqqGQlvSqaszvLappzbhhQkdhsXUJ2c)**
* **sociale**, con questo si intende la capacità di un agente di comunicare con gli altri, attraverso un **linguaggio di comunicazione**, per poter **cooperare**.

La **reattività** e **proattività** sono molte volte in **conflitto**, in quanto per fare delle scelte **proattive** c'è bisogno di **simulazioni**, mentre per la **reattività** si vuole una **scelta veloce**, che quindi va ad escludere la possibilità di fare delle simulazioni. 

Il **bilanciamento** di queste due caratteristiche è quindi **fondamentale** per la creazione di un buon agente, e proprio per questo, è ancora al momento un argomento di studio.

Riassumendo, quindi, un agente intelligente si distingue da un semplice programma per le caratteristiche sopra citate, che portano al fatto che l'ambiente su cui va ad operare l'agente si **muta ogni volta che questo esegue delle azioni**.

## Triangolo della computazione

Ogni codice per dirsi di qualità deve essere:
* Corretto
* Robusto
* Estensibile
* Riutilizzabile

Uno degli ingredienti fondamentali per riuscire a sviluppare codice di qualità è la **modularizzazione**.

Esiste un modo per riuscire a comparare diverse soluzioni di modularizzazione, ovvero il triangolo di Meyer. 
**![](https://lh7-us.googleusercontent.com/PFZYyAG6bswn6lgCxK_62HaDDgEfTjF_fFCPvIc9TlZeNbAF3cez84YeEcTDwgGpW9QXbEYS3F1aG4mXQBH7q3MBwgTNyuungH0XEEWq7ofpPDuinUoBE_e1nJ11SGIE2lqYNdRRD9pkrWnAcsPqHSw)**
Secondo questo metodo di valutazione, **la Programmazione orientata agli Agenti**, è la migliore, in quanto è l'unica che modella gli agenti e l'ambiente e che mette entrambi allo stesso piano.


## Architetture ad Agente

Le architetture più conosciute che si basano sugli agenti sono:

* **Ragionamento simbolico**, questa tipologia di architettura contiene un **modello simbolico** dell'ambiente, e in base a questo prende delle **decisioni simboliche**.
  Questo approccio però ha due grandi problemi:

	* Problema della traduzione, ovvero la difficoltà di **tradurre il mondo reale in una rappresentazione** in un **tempo che risulti abbastanza piccolo** per far sì che la rappresentazione sia ancora utile.
	* Problema della rappresentazione/ragionamento, ovvero il problema di **come creare la rappresentazione** in modo che gli agenti la possano utilizzare, tenendo sempre in conto il **tempo** che deve essere **abbastanza piccolo** per non far diventare irrilevante la rappresentazione.

Entrambi i problemi non sono facilmente risolvibili, le uniche soluzioni che possono andare ad alleviare il problema sono:

* Indebolire la logica con il quale è descritto l'ambiente
* Utilizzare una rappresentazione simbolica, quindi diversa dalla logica classica
* Impostare il programma in modo tale che il maggior numero di decisioni vengano trattate durante la fase di programmazione e non durante la fase di esecuzione, così da andare a velocizzare i processi dell'agente.
* **Reactive Agents Movements**
* **Architetture ibride**
