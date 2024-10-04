# CMS
Un Configuration Management System è un software che permette la gestione del codice in maniera veloce e pulita, viene utilizzato quando:
- Più persone lavorano su del codice in via di sviluppo
- Deve essere disponibile più di una versione del codice (prod, sviluppo, ecc)
- Il codice deve girare in più dispositivi e sistemi operativi
Un CMS mette inoltre a disposizione strumenti per il controllo del codice che viene pushato e per la supervisione del progetto, per permettere di mantenere una buona qualità del codice e una buona struttura del progetto.
Per esempio, può essere necessaria una code review prima di un merge, attraverso la quale è possibile lasciare commenti o richiedere modifiche prima di accettare il codice ed eseguire il merge.
È solitamente una buona idea identificare un insieme di persone che si occupano di gestire tutte le configurazioni del progetto, a partire dall'analisi fino allo studio del codice sviluppato prima di andarlo a mergiare, così da assicurarsi che il codice che è stato sviluppato sia coerente con quelli che erano i piani iniziali.
# GIT
Git è un Control Versioning System, è utilizzato per riuscire a gestire in modo semplice il lavoro di gruppo e il versionamento dei file.
Una delle cose fondamentali che permette git attraverso il versionamento è la possibilità di tornare indietro nel branch per tornare a una condizione di codice diversa da quella attuale e permette anche la creazione di branch diversi staccabili da qualsiasi nodo dell'albero.
# GITFLOW
Aggiunge delle funzionalità a GIT come la creazione di branch paralleli che vanno ad identificare diverse tipologie di sviluppo/stati del progetto.
Per esempio gitflow mette a disposizione branch come quello feature, ovvero dove avvengono gli sviluppi, oppure branch come l'hotfix dove avvengono delle correzioni di bug solitamente in ambienti rischiosi, come può essere prod.