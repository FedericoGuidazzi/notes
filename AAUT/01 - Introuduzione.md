Il Machine Learning ha 3 pilastri:
- **Tasks**, ovvero il problema che il modello che andremo a creare deve risolvere
- **Models**, la tipologia del modello che andremo a creare
- **Features**, la tipologia di dati che abbiamo a disposizione
Il Machine Learning consiste nel creare un modello che in maniera automatica riesca a risolvere il problema di partenza, questo viene fatto a partire da una fase di addestramento su un insieme di dati da cui estrapola le caratteristiche che poi gli permettono di generalizzare e applicare la stessa logica a esempi mai visti prima.

## Tasks
I tasks si dividono in:
- Predittivi, hanno lo scopo di predire un dato a partire dalle features, i principali problemi di questo tipo sono: **classificazione**, **regressione** e **clustering**.
- Descrittivi, hanno lo scopo di individuare caratteristiche nascoste all'interno dei dati, un esempio può essere il clustering ma senza l'etichetta di classe, oppure gli algoritmi di reccomendation basati sulle matrici.
I tasks inoltre si dividono in supervised e unsupervised.

## Models
I modelli di Machine Learning possono essere classificati in base al metodo che utilizzano per arrivare al risultato.
Possiamo individuare modelli:
- Geometrici, utilizzano la geometria per riuscire ad ottenere il risultato, come l'introduzione di iperpiani, trasformazioni lineari o metriche di distanza
- Probabilistici, sono modelli che funzionano attraverso le probabilità, il loro funzionamento si basa nel cercare di limitare l'incertezza.
- Logici, cercano di individuare regole logiche su cui basarsi per arrivare al risultato.

## Features
I dati che utilizziamo possono essere modificati in modo che i modelli che poi andremo a costruire possano lavorare in maniera più semplice ed efficiente.
Per esempio, in cui caso in cui bisogna utilizzare un classificatore lineare, ma abbiamo dei dati non linearmente separabili, che però una volta applicata una trasformazione lo diventano, possiamo pensare di applicare la trasformazione individuata prima di passare i dati al modello così che questo migliori le sue performance, ottenendo una soluzione molto migliore di quella che potremmo ottenere senza la trasformazione.
In generale è molto importante utilizzare dei buoni dati in input per avere dei buoni risultati in output.
