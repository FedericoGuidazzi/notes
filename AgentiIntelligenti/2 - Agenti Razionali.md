📚 Subject: [[AgentiIntelligenti]] 
⬅ [[1 - Introduzione agli agenti intelligenti]]
# Agenti Razionali

Gli **agenti intenzionali** sono sistemi che individuano un insieme di **task** che devono essere portate a termine basandosi su un’insieme di **credenze**, questo insieme rappresenta le **intenzioni** del sistema.

Con **intenzione**, in questo ambito, non andiamo a intendere un’intenzione come quella umana, ma rappresenta **un'astrazione**, utile per analizzare in maniera veloce i sistemi e il perché eseguono una serie di task invece che altre, nella realtà dei fatti tutte le azioni compiute da un sistema si basano su **un’analisi delle informazioni e una conseguente scelta dettata dall’algoritmo passato o appreso**.

La tecnica che si basa sul ragionamento sulle azioni prende il nome di **pratical reasoning**.

Il pratical reasoning si divide in due sottoparti:

* **Deliberazione**, decidere **quale** stato si vuole raggiungere.
* **Pianificazione**, decidere **come** raggiungere lo stato desiderato.

Le **intenzioni** introdotte prima sono il **risultato della fase di deliberazione**.

Ogni processo, quindi, è caratterizzato da una **fase iniziale** che rappresenta la **deliberazione**, quindi lo studio delle condizioni esterne e l’individuazione della scelta migliore, da una **seconda fase** che prende il nome di **means-ends reasoning**, che ha lo scopo di trovare un piano che possa portare all’obiettivo finale, per poi passare alla fase **finale** dell’**esecuzione**.

Per riuscire ad arrivare alla conclusione di un processo devono avverarsi due cose:

* **Persistenza delle intenzioni**, una volta individuate le intenzioni devo continuare su quella strada per arrivare alla conclusione del processo
* **Le intenzioni vincolano il futuro practical reasoning**, quindi non posso scegliere intenzioni che non sono coerenti tra loro 

In generale quindi:

1. Gli agenti devono trovare un **insieme di passi per riuscire ad arrivare ad una conclusione** del processo
2. Le intenzioni devono essere utilizzate come **filtro** per non sceglierne di **contrastanti**
3. Gli agenti **monitorano il successo delle intenzioni** e devono poter **tornare sui loro passi in caso di cambio delle condizioni**
4. Gli agenti credono che le loro **intenzioni siano possibili**
5. Gli agenti **non credono** che **non realizzeranno** le proprie intenzioni
6. Nelle circostanze di base, gli agenti **credono** che **realizzeranno** le proprie intenzioni
7. Gli agenti **non** devono avere intenzioni su tutti i possibili **effetti collaterali** delle proprie intenzioni

Un agente deve quindi essere in grado di analizzare l’ambiente che lo circonda e prendere una decisione sul processo da svolgere.

Come ogni cosa, però, questa decisione comporta una spesa di **tempo**, che può determinare la scelta come **non più rilevante**, questo perché l’ambiente è cambiato, sfortunatamente non ci sono soluzioni a questo problema (_calculative rationality_), l’unica cosa che si può fare è far sì che l’agente sia **elastico nelle decisioni**, quindi in caso di cambiamento dell’ambiente la decisione verrà **aggiornata** andando a individuare quella migliore.

Le uniche circostanze dove questo problema non sussiste sono:

* Il tempo impiegato per definire le intenzioni (means-ends) è piccolissimo
* L’ambiente su cui opera l’agente è statico, quindi il tempo non risulta essere un problema
* La scelta dell’intenzione è garantita essere ottimale durante tutta la fase di definizione delle intenzioni, ovvero l’ambiente non cambia durante il periodo di decisione

Quello nella figura sotto è una prima versione di un algoritmo di un agente

**![Photo | center | 512](https://lh7-us.googleusercontent.com/DyD7UBsavCYvnjS_7iK7DLKcF6lXVdPONkX5YLIzftcfOgq2ocnDAoky_7-GLaoeqEGHVObx9J6F3iZWeRdmSrmsj5JhUOEHeWpuhWyM6gk3YRIaev5RByflt5f55-P7TatqRq2p2BWg-toKwk0yWaM)**

Durante il ciclo possiamo vedere come vengano individuate le credenze sulle quali ci si basa per andare ad individuare le intenzioni e successivamente viene fatto il piano per arrivare alla conclusione di un processo.

Questo algoritmo però ha vari problemi per quanto riguarda l’esecuzione delle azioni che devono essere eseguite per portare a termine un processo, infatti, una volta che parte l’esecuzione questa non **termina** fino a che non viene portato a termine l’obiettivo, che però **nel frattempo potrebbe essere cambiato o non essere più l’ottimo**.

Il processo con il quale sono individuati i passi da eseguire prende il nome di **commitment** e ne sono presenti vari tipi
**![Photo | center | 512](https://lh7-us.googleusercontent.com/6wndO-h4Y3vM-e4ne7K_be6tE7qPIBWBwtj8tf-t-FFmSQiXcBx-0dPLbiK7ElTW6t66AaTVBnyP2GTlbmWYVZe2oFDAYV4QSHn0nuUw3TgaWZU-l8AKhcLSTMNTWBPGr1yGITFpfQ11dZjVl32VxDs)**

Il **Blind** è quello che abbiamo ora nell’algoritmo, quindi anche se il mondo cambia, una volta scelto un piano si porta a termine a tutti i costi.

Il **Single-minded** è una versione un po’ più permissiva, con il quale controllo se il piano che sto seguendo è possibile da portare a termine oppure non è più la scelta ottima.

La versione **Open-minded**, invece, risulta essere la migliore perché continuerà a seguire il piano finché questo risulta il migliore, ma potrà cambiare non appena riterrà che un altro piano sia migliore, anche questa versione però può avere un grave problema, ovvero cambia idea troppo spesso e quindi non riesce mai a portare a termine un piano.

La versione migliorata dell’algoritmo di partenza è quindi una che utilizza l’open-minded commitment ma con un controllo sulla necessità di cambiare piano una volta scelto.
**![Photo | center | 600](https://lh7-us.googleusercontent.com/9H3i3R_YL-X40L-XcP3GHdohjVKW8JvtCsVLS8r-e9_8eJ6ujkKuL9kq10aflQmpsByv2h9tbe6FvvISn94EpcHRWa2IwJ5cA9GimvTl4hUPv88BFNVwbOuYAh8YQTrE_ZrIf9qfMBAV1jdKnhFrwTY)**

➡ [[3 - Linguaggi e architetture per agenti]]