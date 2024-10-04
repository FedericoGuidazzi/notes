# SOA
Le architetture software hanno subito un'evoluzione negli anni 2000 *favorendo delle applicazioni sviluppate a servizi piuttosto che una soluzione unica*, questo per favorire il riutilizzo del codice e la manutenzione di quest ultimo, nascono così le architetture SOA (Service Oriented Architecture).
# Web Services SOAP
Con lo sviluppo del web e delle applicazioni funzionanti su esso è stato necessario trovare un modo comune di comunicare indipendentemente dal linguaggio con i quali erano sviluppati i programmi, il formato **XML** infatti venne utilizzato come *linguaggio comune per scambiare messaggi/informazioni tra servizi diversi tra di loro*, in modo che non ci fosse nessun problema di comunicazione tra applicazioni.
Inoltre il web ha iniziato cambiare funzionalità, passando da un posto in quale *principalmente interagivano gli umani a un posto dove la principale fonte di traffico sono i messaggi che viaggiano tra applicazioni*.
Gli standard basati su XML per lo scambio di messaggi erano:
- **SOAP**, protocollo per il richiamo di procedure da remoto
- **WSDL**, linguaggio per la definizione di web services
- **UDDI**, protocollo per la ricerca di web services
## SOAP
I messaggi SOAP sono formati da due parti:
- Header, contiene dati opzionali sulla chiamata, come autenticazione
- Body, contiene l'effettivo messaggio ovvero i dati e/o risultati delle chiamate
Fornisce uno standard per scambiare i dati e mette anche a disposizione ulteriori servizi che possono risultare utili durante lo scambio di messaggistica da parte di applicazioni.
## WSDL
WSDL è un protocollo basato su XML per la self definition dei servizi.
I principali elementi che vengono definiti sono:
- Tipi
- Messaggi
- Operazioni
- Tipologia di porta
- Binding
- Porta
- Servizi
## UDDI
Questo protocollo è stato creato per la definizione dei path in cui possono essere contattati i microservizi e quali servizi offrono, permettendo di mettere in contatto la richiesta e l'offerta (pagine gialle).
## REST
Le architetture che si basano su REST sono più *versatili e scalabili* rispetto a quelle che si basano su SOAP, ma *perde quella che è la robustezza fornita da un protocollo*, in quanto i messaggi REST risultano essere più personalizzabili e in generale le *applicazioni risultano più veloci* perché possono essere customizzate in quanto non devono sottostare alle regole imposte dal protocollo.
I messaggi REST vengono solitamente scritti in linguaggio JSON, ma supportano anche XML e anche i tipi complessi come le immagini.
REST è **stateless**, ovvero *i servizi non devono mantenere le informazioni che riguardano lo stato dei client che fanno richieste*, infatti nelle architetture REST **ogni messaggio è indipendente dagli altri**, permettendo all'architettura di essere molto più snella e veloce.
# JSON
JSON è un linguaggio molto utilizzato per descrivere i messaggi in quanto ha una struttura molto semplice e personalizzabile, supporta i principali tipi primitivi ed è possibile descrivere tutte le tipologie di oggetti attraverso l'utilizzo delle [] e delle {}.
Ogni parametro/oggetto è definito da un nome tra virgolette e seguito da un :.
