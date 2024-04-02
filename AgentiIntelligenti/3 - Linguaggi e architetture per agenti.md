Subject: [[AgentiIntelligenti]]
## PRS

Il Procedural Reasoning System è stata una delle prime e principali architetture per agenti che ha fatto uso del paradigma **BDI** (belief-desire-intention), ovvero far sì che l’agente possa decidere in autonomia quali sono i possibili piani che può seguire per arrivare al compimento della task, andando anche a tenere in considerazione eventuali cambiamenti nel mondo esterno che possono portare al fatto che un piano diventi impraticabile e quindi debba essere cambiato.

Gli input in PRS sono **eventi** ricevuti grazie ad una _coda di eventi_ e possono essere:

* **Esterni**, percepiti dall’ambiente.
* **Interni**, derivati dall’aggiunta o eliminazione di belief.

Gli output, invece, sono azioni compiute dall’agente una volta passate dall’interprete.

**![](https://lh7-us.googleusercontent.com/BE0MW_QiyRZuVW9cEf0MZ4gS8lOoaE2ladMFSWsl_P_KeQTjhW28_y7zeIR-3kuh6U_3hp828zfmXakYceExqaY5S1OWJyokx6jPdPuFscRqXyQnPoXcO3umwPHIy_UNehGh7mB0PIxM2yTob7MST_4)**

In PRS **non c’è una pianificazione**, viene fatto riferimento ad una **libreria di piani forniti direttamente dal programmatore**, l’agente sceglierà quale è il piano migliore nelle determinate condizioni in cui si trova per riuscire a raggiungere l’obiettivo prefissato.

Ogni piano è composto da:

* Nome
* Condizione di invocazione, ovvero l’evento che triggera l’attivazione del piano.
* Precondizioni, ovvero le condizioni che devono valere per poter eseguire il piano.
* Body, una sequenza di operazioni da eseguire per arrivare al termine del task, queste operazioni possono essere atomiche oppure sotto-task.

Per raggiungere un dato goal, l’agente formula **l’intenzione **di raggiungere questo obiettivo,

cioè **sceglie un piano applicabile** _triggered_ dal goal. Questo piano diventa una **intenzione**, ed è **aggiunto alla intention structure**.

Per portare a termine un goal ci possono essere più piani possibili, sta all’agente la scelta del piano che ritiene migliore nelle condizioni in cui si trova.

**![](https://lh7-us.googleusercontent.com/v4CgMuo2H6wGwEiSwj7_-48taXmBrrrCaAJwNp2qnEnbxQI11FQ3DTxgtzjaqW5l9LBheHVvEHnNrnyxJR5pw1t5uSPesboqdY7cm_bU2Bu98quQe-d0O1MC4iX7rxVXxHNqpBcBgU05Af5283pUZs4)**

Ogni volta che viene individuato un piano da seguire viene avviato un **control loop**, ovvero un loop di azioni che l’agente compie fino a che non viene portato a termine il goal.

**![](https://lh7-us.googleusercontent.com/uCGkz3g09KgAmG6HAl8e-TCuLavmMZTu-TKb9KpNhwHT_myUHWXha2eVRzpryravS5QAnGjo31KWkdeWJ06epZmTxGwbW_oh61vIKSDI2lHi87eerRZzjU9oW66Q6SD_3MEr7nmiGUP3_HWGPuI_PDI)**

Ad ogni passo viene **aggiornato **anche lo **stack delle intenzioni**, ovvero l’insieme dei passi ancora da compiere, in cui le azioni da compiere per prime sono posizionate alla cima dello stack, ad ogni aggiornamento della event queue il **posizionamento delle intenzioni può variare** (in caso di abbandono del piano attuale, verranno rimosse dalle prime posizioni tutti i passi legati a quel piano, oppure in caso di presenza di un sotto-gol da portare a termine prima del gol principale, verranno inserite nelle prime posizioni dello stack le azioni legate al sotto-gol). 


### AgentSpeak(L)

AgentSpeak(L) è un linguaggio proposto per la programmazione di agenti BDI utilizzando una sintassi operazionale, cerca quindi di andare a colmare il gap tra specifica teorica e implementazione di un agenti BDI, questo linguaggio ha dato origine a JASON (ovvero la prima implementazione di AgentSpeak(L)).


## Agent-oriented programming (AOP)

Questo nuovo paradigma di programmazione promuove una visione sociale della computazione, in cui più agenti comunicano tra loro.

In questo linguaggio, ad ogni azione corrisponde un determinato tempo, ed ogni agente ha delle **belief**, **capabilities**, **commitments** e **commitment rules**, che possono cambiare nel tempo (tranne capabilities che rimangono fisse).

* **Belief**, sono le credenze che ha un agente all'istante T.
* **Capabilities**, sono le capacità che possiede un agente (non cambiano nel tempo).
* **Commitments**, l’insieme delle azioni che un agente farà.
* **Commitment Rules**, è il “programma” che va a determinare come un agente agirà.

A seguito un esempio di Commitment Rule:

**![](https://lh7-us.googleusercontent.com/btM2tobPPFbhrsuKtqOxu-RZHDMcqMeIukBhKTTIdFizY25XFHEESMG7LPu4yDaEs2PbccGRv8R74XLFqekU2KE4-2BqkOkC6bc9B92DI6F9yLGs8TvZAvogyXnOMJyvOItuHlA0PJp1OIk04Z5qwrA)**

Anche in questo caso per riuscire ad arrivare ad un gol finale possono dover essere eseguiti vari step e le condizioni dell’ambiente potrebbero cambiare, di conseguenza è **necessario inserire nel loop** per la scelta delle azioni delle **condizioni** che tengono in conto del **cambiamento interno** (quindi cambiamente causati da azioni dell’agente) e **esterno** (quindi cambiamenti dell’ambiente), di conseguenza ad ogni tempo verranno fatti:

* **Lettura dei messaggi** e **aggiornamento** di **belief** e **commitment**.
* **Esecuzione** del **commit** per il tempo attuale **eventualmente** portando ad una **modifica** dei **belief**.
## Agenti reattivi

Ci sono **tanti problemi irrisolti** nell'_AI simbolica_, proprio per questo si sono sviluppate **architetture reattive** che **variano molto tra loro**, a che si basano tutte sul pensiero che l'approccio che utilizza l'AI simbolica sia **sbagliato**.

### L'Approccio di Brooks

Brooks per spiegare la sua idea di agente reattivo ha individuato 3 punti:

* Un comportamento intelligente può essere generato **senza rappresentazione esplicita**.
* Un comportamento intelligente può essere generato **senza ragionamento esplicito**.
* L'intelligenza è una **proprietà emergente** di un sistema complesso.

L'architettura reattiva che propone Brooks fa uso della _subsumption architecture_, ovvero una gerarchia di task che eseguono _behaviours_, dove ogni behaviour è una struttura a regole molto semplici. 

**![](https://lh7-us.googleusercontent.com/S05Fb--_ttudDNWLsWEl5e9i_sSthQkEFQFrFZ7yU9jTiz3ooHMmTOVOAtXtLJuNlepbKBGoNmUvR2qhXudQv4ZTaRqN_l0agSyU7GGuIVQGkDWZ1wBwkQpaf4AdpH3yB69jWAVYkYKv8E5_E7-nTfc)**

In pratica, l'agente avrà dei sensori che utilizzerà per avere degli input, questi input verranno passati ai vari livelli e questi potranno attivarsi o no, in base a come è stato programmato l'agente. \
Nel caso che due o più livelli si attivino per lo stesso input, si tiene solamente l'output del livello più basso e si scartano gli altri.

Questo tipo di architettura è stato utilizzato all'interno dello **Steels’ Mars Explorer** e i suoi livelli erano: 

**![](https://lh7-us.googleusercontent.com/U3B72gFicPkgPXyZuWSazWPTLPEbVSFW25e_VAqOJaeTjTXk9f-72LX9v63BX-1v7SmHvfQweasbKxVJqUZFQ7Gh9miRz6WZb656CEKOqa5aT0Hh-pEh2NYXZk9nlB25LD1ft7jjp5MHPi2ex1QC0PI)**

Nel caso che l'agente debba compiere task che non erano previsti inizialmente deve essere rivisto l'ordine dei livelli, andando a integrare le nuove funzioni come fossero livelli indipendenti dagli altri. 

**![](https://lh7-us.googleusercontent.com/3yTv2G3J0dQqHMUuVv3bHlHbhKPefCKLb6ocmFnyViqmUA48I5E4xmaR5jC8xCps3PYCIk_vvpTSOEFtxWSt5TZ7ARuqL2VubBTrduz_WC3JCmP04Wi3ByX84g6LUbj98XgciRCuN_YjP_Ha2FnwQEg)**

L'approccio utilizzato dagli agenti reattivi ha come pro:

* Semplicità
* Economia
* Trattabilità computazionale
* Robustezza verso i fallimenti
* Eleganza

Mentre i lati negativi sono:

* **Non** avendo **informazioni** **pregresse** dell'ambiente devono individuare queste ogni volta
* Se **l'informazione** individuata è **locale**, come fa l'agente ad ottenere **informazioni** **non** **locali?** (gli agenti reattivi hanno una **visione a breve termine**)
* Difficile realizzare agenti reattivi che **apprendano**
* È difficile **ingegnerizzare** agenti reattivi specifici in quanto le informazioni che questo ha derivano dall'ambiente e questo può cambiare ogni volta
* È difficile realizzare agenti con un g**rande numero di behavior** in quanto è **complesso** trovare un **ordine** dei **livelli** che vada sempre bene.

## Architetture Ibride

Le architetture ibride nascono per cercare di prendere i punti migliori delle architetture reattive e deliberative, in quanto un approccio puro non è ottimo per nessuna delle due architetture citate.

Un approccio molto diffuso di queste architetture è quello di costruire un agente con almeno 2 sottoinsiemi:

* Uno **deliberativo**, contenente un **modello simbolico dell'ambiente** e capace di **costruire piani** e **prendere decisioni**.
* Uno **reattivo**, capace di **reagire ad input velocemente** **senza ragionamento**.

Solitamente in questo tipo di agenti viene data la precedenza all'output della parte reattiva, e in caso questa non ci sia o non sia soddisfacente si passa all'output della parte deliberativa.

Anche questo tipo di architetture sono composte da livelli e questi possono essere:

* **Horizontal layering**, tutti gli strati sono connessi ad input ed output contemporaneamente.
* **Vertical layering**, gli input ed output sono gestiti al massimo da un layer alla volta.

**![](https://lh7-us.googleusercontent.com/VjVAk4RkZFfaUu-5x0X02Jyle9L5rkQnVfWGi5odw4Hg4pHYbuhIGDs7TEBfmUmR5tbyGa8Eovm2Fg5KVBVWeNA16za5jidRN10ueKZqVWeBNBPV2cHn5nrdAat_dfgce7Ev9LdBwn70ogXAuEPfBDM)**

Due esempi di questa architettura sono:

* TOURINGMACHINES
* inteRRaP

### TOURINGMACHINES

L'architettura consiste di sottoinsiemi di **percezione** ed **azione**, che si interfacciano direttamente con l'ambiente dell'agente e **3 control layers** inseriti in un **control framework**, che ha il compito di mediare tra i livelli. \
**![](https://lh7-us.googleusercontent.com/hBZwO-803edODvZgVugSgHZTMPRxGgkBH_9zi1-ESUzwXhm8pHX6sWUdcRl9vzW8qjAz7T6AFco85PYl3egWbFrP9TtJ0xf5F6T7w-0Yy7XN8z_yreiK7rAlPtxwUNm8y8rug3YOhPXFji7c-C635fk)**

Il r**eactive layer**, è il livello implementato con una **architettura reattiva**, si basa quindi su **regole individuate al momento della programmazione dell'agente**, non fa ragionamenti ed è quindi il livello più veloce.

Il **planning layer**, è il livello che ha il compito di **creare piani** e **scegliere azioni** da eseguire per riuscire ad arrivare al gol

Il **modelling layer**, è il livello che contiene la r**appresentazione simbolica degli stati cognitivi delle altre entità** nell'ambiente dell'agente.

I layer comunicano tra loro e sono inseriti all'interno del **control subsystem** che ha il compito di **scegliere l'azione da eseguire**.

### inteRRaP
**![](https://lh7-us.googleusercontent.com/Sk378DQLpe5egU0_lWAS7z3L3HWJSBssAb5KGbLGXhEcITrXPhpcZ34V3k5NbJxlTEB2-aXt_sXJ6EaJVE4zYIrXdSB_OLmmzLbwu-C3zobuykeQuasPEKKrcCECIdLpVy4PYi7eRLuYvcS9lTsbQS8)**

Su questa architettura si basa “**Stanley**”, ovvero una macchina autonoma sviluppata da Stanford che è riuscita a concludere per la prima volta un percorso nel deserto. 
I livelli che sono stati individuati nella sua architettura sono:

**![](https://lh7-us.googleusercontent.com/Q6pw1b8n96jHziFw9dRqYpNYHur__rewoJy3Md-A0RXqoHwY_LPqBUOqnfBzUICG5O3u6fjxRlqYTQflb9T6mJITgv8Dzb2U24AZM4g9zPo6g5Bnvgn4iuACo3zQNwwujF4T8sGG-fYpnoxVqFuL9mo)**

Il **problema più grande** individuato dal team di Stanford è stato la **percezione** dell'ambiente esterno più del compiere l'azione in se, infatti, l'azione stop in caso di ostacolo è stata semplice da implementare, ma è stata molto complessa la parte dell'individuazione dell'ostacolo, proprio per questo la macchina aveva **tantissimi sensori** per riuscire ad avere più informazioni possibili dell'ambiente circostante.
