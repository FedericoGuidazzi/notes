# Maven
Maven è un tool utile nella costruzione di grandi progetti, ha il compito principale di *scaricare e linkare tutte le dependency* che vengono indiacate nel file pom.xml.
È molto utile anche nella *gestione delle build* (per esempio clean install) dove può rigenerare file compilati e creare delle configurazione per permettere l'avvio del progetto.
Permette l'utilizzo di *plugins* per estendere le sue funzionalità, inserendo semplicemente i tag all'interno del pom.
# JEE
Java Enterprise Edition è un framework per lo sviluppo di applicazioni server-side complesse.
Questo framework è particolarmente utile in applicazioni che devono essere *scalabili*, deve essere assicurata la *data integrity* e l'applicazione deve essere *rivolta a più clients*.
JEE ha come target principale le applicazioni che hanno lo scopo di *fornire APIs in modo efficiente e scalabile*.
JEE è un buon framework di partenza per grandi applicazioni perché fornisce molti componenti utili da libreria, così che non ci sia il bisogno di riprogrammarli da 0 tutte le volte, questi sono:
- Enterprise Java Bean (EJB), sono dei *Bean di sessione* che mantengono le informazioni, possono mantenere la *sessione dell'utente oppure mantenere solo delle informazioni one-shot*, possono anche eseguire delle semplici business logic ma solitamente mantengono i dati di sessione prima di passare alla servlet.
- Java Naming and Directory Interface (JNDI)
- Remote Method Invocation (RMI)
- Servlets
- Java Server Pages (JSP)
- Java Messaging Service (JMS), sono dei componenti che hanno lo scopo di fornire delle code per poter inviare messaggi a servizi diversi, vengono implementati con delle code e possono essere sincroni o asincroni, one-to-one o one-to-many, come i middlewares di messaggistica permettono il *Fire and Forgot* da parte del mittente e invece da parte del ricevente permettono di *consultare il messaggio quando si vuole* con la *garanzia di riceverlo*.
- Java Transaction Service (JTS)
- Java Database Connection (JDBC)
- Java Authentication and Authorization Service
- JavaMail
JEE individua 3 livelli di architettura:
- **FE layer**
- **Business Logic layer**
- **Database/ORM layer** 
## Persistenza
In JEE è possibile anche creare dati persistenti che vanno a simulare delle tabelle database, per creare un oggetto persistente si utilizza il tag Entity, mentre per la creazione dei campi delle tabelle basta semplicemente crearli come un normale oggetto Java.
# Single Page Application
L'evoluzione nel campo delle interfacce web ha portato a rendere *obsoleta la maniera in cui erano costruite le pagine web negli anni passati*, andando a sostituire quasi del tutto le tecnologie HTML + Javascript + CSS.
Le SPA sono applicazioni web che si aggiornano e modificano senza il bisogno di un ricaricamento della pagina o un caricamento di una pagina diversa, infatti attraverso la presenza di codice javascript vengono fatte le chiamate in background e aggiornate automaticamente le pagine senza far intuire niente di tutto questo all'utente che sta usufruendo del servizio.
Questa evoluzione ha portato principalmente ad una *migliore interazione dell'utente* e ad una *velocità maggiore generale del sito web*.
