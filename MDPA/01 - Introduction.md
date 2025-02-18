Ogni concetto, se non definita una base comune può avere interpretazioni diverse, in quanto il linguaggio non ha significato univoco.
Per poter avere la certezza che il significato delle parole che stiamo scambiando sia uguale per entrambe le parti coinvolte è necessario che vengano individuati in maniera chiara i **concetti**, le **intenzioni** e le **classi**.
Un *concetto* deriva da un'astrazione e da una generalizzazione derivata dell'esperienza del singolo individuo, che di consegunza, non è univoco (una persona daltonica crede che il mondo abbia dei colori diversi da una persona che non lo è, di conseguenza se descrive dei particolari questi possono differire).

La *concettualizzazione* delle descrizioni sono un insieme di invariazioni rilevanti descritte dagli agenti in base al fine che devono comunicare, per esempio un tavolo può essere descritto in vari modi diversi per inseguire fini diversi, può essere descritto come un oggetto di stile e quindi descrivere le sue caratteristiche costruttive, oppure può essere semplicemente descritto come un pezzo di legno di certe dimensioni.

È quindi necessario un **sistema di informazione** che sia condiviso tra gli agenti così da poter comunicare senza il problema dell'interpretazione che può variare da agente ad agente.

- [ ] Un **sistema di informazione** è un sistema che *colleziona*, *mantiene*, *processa* e *distribuisce* informazioni riguardanti un dominio per facilitare la *pianificazione*, il *controllo*, *coordinazione* e *presa di decisioni* all'interno di una organizzazione.

Il sistema di informazioni mantiene stati del dominio
- **Intenzionali**, concetti che descrivono la struttura del dominio
- **Estensionali**, insieme di istanze che descrivono i concetti
I sistemi di informazioni possono essere queried per recuperare informazioni a riguardo del dominio applicativo rappresentato e questo risponde attraverso un linguaggio condiviso.

Le queries che possono essere rivolte ad un sistema di informazioni sono di due tipi:
- Estensionali, ovvero riguardanti le singole entità (chi sta seguendo un determinato corso? La risposta sarà una lista di studenti) 
- Intenzionali, ovvero riguardanti l'oggetto in se (Che cosa è uno studente? La rispostà sarà un'insieme di caratteristiche che descrivono lo studente)

Solitamente per riuscire a evitare i problemi di interpretazione, si utilizzano linguaggi specifici come l'ER, dove i componenti fondamentali sono:
- **Entità**, le istanze che agiscono e che esistono nel dominio,
- **Relazioni**, come le entità sono legate tra loro, solitamente sono azioni.
L'insieme tra entità e relazioni formano delle tuple (corriere-consegna-pacco).

Lo **stato di un dominio** consiste nelle proprietà rilevanti di questo che sottosanno a dei vincoli, di conseguenza le proprietà che devono essere interne allo stato del dominio sono solo le *primitive*, ovvero informazioni che non posso riuscire a ricavare in nessun altro modo (data di nascita -> primitiva, età -> derivata).
I vincoli all'interno del domionio possono essere:
- **Statici**, sono le informazioni fondamentali che non subiscono variazioni, si trovano nello schema concettuale strutturale.
- **Dinamici**, sono vincoli che possono evolversi durante la vita del dominio e cambiare, si trovano nello schema dei comportamenti.
- **Temporali**, sono vincoli che permettono l'evoluzione dei dati.
Un modello concettuale è formato da uno schema concettuale (ovvero le entità che fanno parte del modello) e l'insieme delle informazioni di base (ovvero le istanze delle singole entità).

Un buon schema concettuale riesce a specificare bene tutti i concetti del dominio e rimane stretto a quelli, senza includere specifiche non richieste.
![[Pasted image 20241211194503.png]]Questo perche se no, quando ci si interfaccia con altre entità che a loro volta avranno il loro schema concettuale, si potrebbero verificare delle incomprensioni date da specifiche che non dovevano essere interne al dominio.
![[Pasted image 20241211194633.png]]