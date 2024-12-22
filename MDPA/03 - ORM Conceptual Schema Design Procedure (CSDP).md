L'Object Role Modeling (ORM), ha il compito di fornire uno schema di design concettuale delle procedure che si vogliono modellare nell'ambiente applicativo.
È un modello che si basa sugli esempi e quindi sulle relazioni che hanno le istanze.

Per la creazione di un buono schema sono necessari 7 passaggi:
- Trasformare gli esempi forniti in fatti elementari (ovvero fatti che se venissero divisi ulteriormente perderebbero di senso
	- Marco conosce Luca -> fatto atomico, non può essere suddiviso ulteriormente
	- Marco conosce Luca e Chiara -> fatto non atomico, si possono ottenere due relazioni separate (Marco conosce Luca, Marco conosce Chiara)
- Disegnare il tipo dei fatti e verificare che tutti gli esempi forniti siano coerenti con la modellazione
- Controllare il tipo delle entità che hanno delle relazioni, e verificare che non esistano derivazioni dei fatti (x nato il y e x ha y anni)
- Aggiungere vincoli di unicità 
- Aggiungere vincoli sui ruoli
- Aggiungere valori e vincoli di sottotipo
- Aggiungere ulteriori vincoli e check finali

## Step 1
Lo step 1 si concentra nell'individuazioni dei fatti elementari a partire dagli esempi forniti.
Per poter analizzare gli esempi è necessario aver una buona comprensione del dominio applicativo, di conseguenza è molto utile poter rivolgere le domande direttamente ad un esperto del dominio, così da non avere incertezze poi nella fase di modellazione.

Per esempio, senza una conoscenza del dominio applicativo, questo esempio può risultare ambiguo:
**Ann and Bob open a loan request.**
Infatti la domanda che deve essere fatta all'esperto del dominio è: il mutuo è cointestato e di conseguenza se viene spezzato l'esempio si va a perdere del significato, oppure Ann e Bob sono due clienti separati e di conseguenza si può spezzare la relazione senza problemi?

### Oggetti Base
Ogni oggetto deve avere due caratteristiche:
- **Valore**, deve poter essere descritto attraverso un valore, che deve essere rigido e può essere stringa o numerico.
- **Entity**, deve essere referenziabile all'interno del contesto, deve quindi essere identificato da una sua caratteristica univoca.
La frase *Lee is located in E301* viene scritta come
**Person (.surname) ‘Lee’ is located in Room (.code) ‘E301’.**

### Ruoli
I ruoli sono concetti fondamentali all'interno di questo schema, infatti vanno a mettere in comunicazioni entità diverse e a specificarne caratteristiche di singole.

Le caratteristiche che i ruoli devono sottostare sono:
- L'*ordine in cui sono scritte le relazioni conta*
- *Non è necessario che le n relazioni abbiano a che fare con entità distinte* (posso dire che Ann smoke, avendo quindi una sola entità nella relazione)
- Il concetto ottenuto dalla relazione *non deve poter essere modellato come un insieme di relazioni già esistenti nello schema*.

### Procedura
La procedura di esecuzione per portare a termine lo step 1 in maniera corretta è il seguente
- *Ottenere dei dati significanti*, contenete tutti i possibili casi che si vogliono descrivere.
- *Analizzare il dominio insieme a degli esperti*, utilizzando termini comuni a non ambigui per essere sicuri di star esponendo gli stessi concetti, al termine di questo sotto-step si otterrà una **verbalizzazione delle informazioni del sistema as-is**
- *Processare le informazioni*, cercando di individuare gli aspetti che devono essere modellati, andando a creare esempi in caso non fossero presenti, al termine di questo sotto-step si otterrà una **formalizzazione dei fatti elementari del sistema as-is**
- In caso di *nuovi esempi e informazioni ripetere gli step* in modo da riuscire a indentificare eventuali disallineamenti nei concetti modellati, al termine di questo sotto-step si otterrà una formalizzazione dei **fatti elementari del sistema to-be**

## Step 2
Il compito del secondo step è quello di disegnare un diagramma di istanze basato sulle informazioni ottenute al passo 1 e che risulta coerente con tutti gli esempi disponibili fino ad ora.

### Diagramma dello schema concettuale
È una astrazione del diagramma ad istanze.
È composto dai seguenti elementi:
- *Tipo di oggetto*, ovvero il tipo di forma geometrica nel quale inserisco l'oggetto (solitamente a forma di rettangolo, può avere gli angoli smussati o no e può essere solid o tratteggiato)
- *Ruolo*, che specifica il ruolo che ha l'oggetto in una relazione
- *Predicato*, n box contigui in base a che cardinalità ha la relazione
- *Vincolo di partecipazione*, una unica linea che parte da un tipo vuoto fino a un rettangolo ruolo
- *Vincoli*
![[Pasted image 20241222165837.png]]

### Tipi di relazione
Le relazioni possono essere:
- *Tipologia di fatti elementari*, ovvero una relazione tra entità, nell'immagine sopra la relazione tra Person e Company
- *Reference*, una relazione tra entità e valore, nell'immagine sopra la relazione tra Persone e il PersonName
Esiste anche una forma abbreviata per descrivere le relazioni di referenza, in cui viene aggiunto l'identificatore direttamente all'interno del rettangolo che specifica l'entità, ottenendo una diagramma più compatto.
![[Pasted image 20241222170209.png]]

#### Tipologie di referenza e conversioni a tipologia di valori
Nella formulazione abbreviata, possiamo specificare anche delle informazioni che riguardano direttamente l'identificatore che inseriamo nella casella dell'entità, i tipi che possiamo specificare sono:
- *Popular*, indica un identificatore specifico per quell'entità, e viene inserito con un . davanti, nell'esempio il .name dell'entità person vuole dire che la persona ha un nome specifico con il quale viene identificata
- *Measurement*, indica una unità di misura e viene inserita come valore seguito dai :, per esempio EUR: specifica che una determinata entità viene misurata in EUR
- *General*, indica altre tipologie di riferimento, in questo caso si inserisce solamente il riferimento senza nessun simbolo, come nel caso del VAT della Company nell'esempio precedente
### Fatti unari
Come detto precedentemente possono esistere anche fatti che prevedono una sola entità, come per esempio Ann smoke, in questo caso si utilizzano delle tipologie di relazioni unarie come la seguente
![[Pasted image 20241222171058.png]]
### Tipologie di fatti
I fatti possono essere:
- *Eterogenei*, mettono in relazione entità di tipi diversi
- *Omogenei*, mettono in relazione entità di stesso tipo
![[Pasted image 20241222171400.png]]
Le relazioni ad anello sono del tipo omogeneo (nell'immagine la relazione is husband of/is wife of oppure quella che riguarda la company), mentre le altre relazioni sono eterogenee

### Reification, Objectification, Nesting
Alcune relazioni, soprattutto quelle che riguardano più di 2 entità, possono essere riviste attraverso la reification, ovvero l'oggettificazione della relazione per poter andare a mettere in relazione con altre entità.
![[Pasted image 20241222171848.png]]Le due versioni hanno lo stesso significato **solo** in caso la relazione oggettificata sia conosciuta per qualsiasi entità coinvolta, di conseguenza in base al dominio applicativo potrebbe essere più comodo descrivere una relazione in modalità **flatten**, ovvero senza oggettificazione, oppure in modalità **nested**, andando ad oggettificare la relazione per poter andare a collegare altre relazioni ad essa.