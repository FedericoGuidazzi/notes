Lo sviluppo della data logic, come quelle dello sviluppo, necessitano di vari cambiamenti durante la vita del software, sia per feature non dichiarate sia per problemi che possono sorgere durante lo sviluppo.

I linguaggi di modellazione concettuale sono 3:
- UML
- ER
- ORM

UML è un linguaggio che deriva strettamente da una visione OOP, di conseguenza vengono individuate le classi e gli attributi.
ER invece è un linguaggio nato per descrivere le basi di dati, di conseguenza è basato molto sulle relazioni delle entità.
Entrambi i linguaggi peccano di modularità perché molto spesso ci si ritrova a cambiare delle scelte passate per poter accogliere nuove funzionalità o direttive.
Il linguaggio ORM, invece, è un linguaggio situato ad un livello più alto dei precedenti, non collegato direttamente a nessun concetto e questo permette di essere più flessibili e di esprimere anche concetti che con gli altri due linguaggi non sarebbe possibile esporre.
In questo linguaggio le entità sono solamente caratterizzate dal loro identificatore e quelli che sarebbero stati gli attributi in linguaggio UML diventano le relazioni che legano le entità.
![[Pasted image 20241218184031.png]]
I pro di questo linguaggio sono:
- Stabilità semantica, è un linguaggio modulare, in cui le aggiunte vengono accolte senza problemi.
- Verbalizzazione naturale, tutti i concetti possono essere inseriti all'interno del diagramma senza nessun problema.
- Popolabilità, inserire concetti in questo tipo di diagramma può risultare più semplice rispetto l'inserimento negli altri linguaggi. 
- Non esistono i null, non esiste il concetto di null, le entità che vengono descritte ci sono forzatamente, le cose che possono esserci o no sono le relazioni.