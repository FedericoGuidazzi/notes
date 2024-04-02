Subject: [[AgentiIntelligenti]]
## AgentSpeak(L)

È un linguaggio che cerca di tradurre in un formato quanto più simile alla programmazione classica gli step che un agente segue per portare a termine i gol. 
È pensato per la programmazione di agenti con una architettura **BDI** (belief, desire, intention).

Le componenti del linguaggio sono:

**![](https://lh7-us.googleusercontent.com/lkdHTKYh8X4vXlFLLWVbbyFkGoae0UXfxi1eQtGpCYKY3DudR-Kq0JrnhSZYgx7rkmiqhsHr6-ux3W7CKOlCi3yJf2DsrUI1Eg-AQmEMFCLnn69IeF2LMwk3MbV1gk3qCZnLZgqKejh6NlSJqwHKbr8)**

**![](https://lh7-us.googleusercontent.com/ardS8vMHH9isTZPTcDV0IEgHv0EQG6Pp4-eJklqGtyAaEkpFdQfeIw8uXcGEQd-J5hzTqJsN09KnpS-z8cjQYmro6c-qmmLgBdHucwna_ace7rNJBapRRjqoBvJZdjuzkSeviCnl89NrdwllcmTe3DQ)**


### BELIEF

I **belief**, sono indicati da un nome (scritto con l'iniziale in minuscolo) seguito dalle parentesi tonde, che ospitano i componenti della credenza, per esempio:

**adjacent(X,Y).**
**location(robot, X).**
**location(car, X).**

Dove X,Y sono variabili (i cui nomi hanno sempre la prima lettera scritta in caps), mentre robot è una "costante" che indica l'agente in se in questo caso.
### Goal

Un goal è uno stato che l'agente vuole raggiungere. \
Esistono 2 tipi di gol:

* **Achievement goal** (!g(t)), è indicato da un ! che precede il nome e i parametri del goal, rappresenta il fatto che l'**agente vuole raggiungere** uno **stato** dove **g(t)** è ritenuto **vero**.
* **Test goal** (?g(t)), è indicato da un ? che precede il nome e i parametri del goal, rappresenta il fatto che l'**agente vuole verificare** che il **belief** g(t) sia **vero o falso**.

**!cleared (b)**: l’agente vuole pulire la corsia b.
**location (car ,b)**: l'agente vuole verificare se nella corsia b ci sono auto
### Triggering Event

Quando l'agente acquisisce un nuovo goal oppure nota una modifica nell'ambiente può far scattare aggiunte o rimozioni di beliefs o goals.

**L'aggiunta** di un belief/goal è indicata dal belief/goal preceduto dal simbolo **+**, mentre la **rimozione** è indicata da un simbolo **-**.

**+location(waste, X)**: aggiunto il belief che nella posizione X si trova waste
**+!cleared(X)**: aggiunto il goal di pulire X 

**![](https://lh7-us.googleusercontent.com/7On59vB7ifiphVa3D0yl2twvzU5vfTyQNcbvyXPeFb9Fy4-_WT2GKqnJ4DxAaVzG77-gzTTI_Kyl1Eh9BWr4vfqQaWhuS6KoU0lOTrgvaGKHGM6TOHLLbyH9Dr4T6QFXsTP8TcfmeWIgAPNAInFKLYw)**

### Azione

Sono gli tutti i passi che l'agente esegue per portare a termine un goal, è indicato da una sintassi simile a quella dei belief, ma si distingue in quanto il nome associato all'azione è associato ad un simbolo di azione.

**move (X,Y)**: indica che l'agente si sposta da X per andare in Y

### Piano

Un piano indica la serie di passi che potrebbe fare un agente per compiere un goal.

Un piano ha la seguente sintassi: 
piano := head <− body

head := triggering event : context 

**![](https://lh7-us.googleusercontent.com/-XhGolUVa4IHzlMIyiEmbRxvUVLY6bBuP4VS_XyAj0log-5LVdU4hQ5s7FIo8CV6MSSk2PENUX7tryFeoikuPPaTkmaMAHzlLLsMq73StH1_b41CeBGVTVXfLNz_S77GPIErp2H1skDPUZE_IHGlZ58)**

## Semantica Operazionale

Al momento dell'esecuzione l'agente può essere visto come costituito da un insieme di:

* Beliefs
* Piani
* Intention
* Eventi
* Azioni
* Funzioni di selezione

Il funzionamento di un agente in funzione è il seguente:

1. Il tutto è statico nell'agente fino a che non viene individuato un **triggering event** (che può essere interno o esterno, interno se è modificato uno stato dell'agente, esterno se è modificato l'ambiente), l'evento viene **inserito** nella lista degli **Eventi**.
2. Viene applicata una **Funzione di selezione** (Belief Revision Function), che ha il compito di scegliere l'evento da prendere in considerazione.
3. Attraverso l'evento selezionato vengono individuati i **Piani rilevanti** grazie all'utilizzo di un **Unificatore rilevante**, ovvero vengono associate alle variabili che si trovano nei piani le costanti prese dall'evento, se il piano risulta ammissibile viene tenuto in considerazione per la scelta successiva del piano da seguire.
4. I **Piani individuati** vengono **filtrati** attraverso le **conoscenze** che sono presenti nelle **Beliefs** e vengono mantenuti solo i piani che risultano coerenti, anche in questo caso si potrebbero individuare più **Piani applicabili** e più **Unificatori applicabili**. 
5. Viene **scelto** un solo **piano** (intended means) tra quelli individuati e viene **inserito** all'interno delle **Intention**, se **l'evento** era **interno** il piano individuato verrà posto sulla **cima** dello **stack** del **triggering event**, in caso di evento **esterno**, invece, viene **creato** un **nuovo** **stack**.
6. Viene scelta un'intenzione da mettere in atto tra quelle disponibili.
7. Viene messo in atto quello che è stato scelto, ci possono essere 3 casi:
    1. **Eseguire un achievement goal**, equivale a generare un evento interno per aggiungere il goal alla corrente Intention
    2. **Eseguire un test goal**, equivale a trovare una sostituzione per il goal che sia coerente con le informazioni che si hanno nei belief, in caso venga trovata una sostituzione, il test goal è rimosso dal top dello stack dell'intention
    3. **Eseguire un'azione**, equivale ad aggiungerla al set di Azioni e rimuoverla dal corpo del top delle Intention
8. **Il ciclo ricomincia** fino a che non ci sono più **Eventi** o non è possibile eseguire altre **Intentions**.

**![](https://lh7-us.googleusercontent.com/1FiupcBUpQUo2rqnGJ6QNS8D0S4dfnqiIVNPy-sehgR_mnErPc6KmleFXnUIZzgxUkGj8DyTjr4m3guPGyuf--YAjUocUKDf8lJIkts7xIbxK9Sks83j6alYvNi0zeyYL2bMCxLjVb3mRE_6MFbS3xI)**

Ciclo applicato all'esempio del robot.

**![](https://lh7-us.googleusercontent.com/oD7rbL6QgiU57D-R__rC5iKs8rqfOF16l3Q7DUOKSzxfGjJuhXMhsAfmIYNoYI3YAiEHETqO8kyWqVy9vwRBJJmBslR6Pa4Y-tRm6bJ6xM7Felqns9nldFYSFoXEk6ue0uxsnHYDLfOT1jLECs_u1Ck)**

## Jason

Jason è una prima implementazione di AgentSpeak(L), implementato in Java ed open-source.
La creazione di un programma con questo linguaggio è molto semplice, basta fare:

* Inserire il nome dell'agente nel file di configurazione
* Creare un file .asl contenenti i piani che l'agente andrà ad eseguire

Le principali differenze che Jason ha rispetto ad AgentSpeak(L) sono:

* È possibile eseguire una **negazione forte**, in particolare possono essere eseguite due tipi di negazione:
    * **Negazione debole**, è presente anche in AgentSpeak(L) ed è introdotta dall'operatore not (es: not location(car, X)).
    * **Negazione forte**, è utilizzata per negare un fatto/predicato ed è introdotta dall'operatore ~ (es: ~location(waste, b))
* **Annotazioni**, si possono specificare annotazioni nella _base belief_ per aggiungere informazioni, per esempio per mantenere la fonte di quell'informazione (es: blue(box1)\[source(ag1)] ), ci sono due annotazioni particolari che vanno a specificare la fonte dell'informazione:
    * \[source(percept)], indica che la conoscenza è stata percepita dall'ambiente
    * \[source(self)], indica che la conoscenza è stata aggiunta direttamente dall'agente durante l'esecuzione di un piano
* **Labels**, è possibile associare una label a ciascun piano, la label può essere un qualsiasi predicato (tra cui anche le annotazioni)
* **Gestione del fallimento di un piano**, se un piano fallisce viene inserito nello stack degli eventi -!g, ovvero la cancellazione del piano che stava eseguendo, nel caso sia previsto un piano associato all'evento -!g, allora questo viene eseguito, in caso contrario viene eliminata l'intera intention e segnalato un warning
* **Azioni interne**, possono essere eseguite azioni che non hanno a che fare con l'ambiente esterno, le due più comuni sono:
    * .send(), usata nelle comunicazioni tra agenti.
    * .print(), utilizzata per scrivere messaggi nella console.

Attraverso l'utilizzo di Jason è inoltre possibile la **personalizzazione** degli **agenti** e delle **operazioni** che questi compiono, basterà dichiarare delle nuove classi Java in cui vengono descritti gli agenti o le operazioni e successivamente potranno essere utilizzate.
