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

## Step 3
Lo step 3 ha il compito di analizzare il diagramma ottenuto nelle step 2 per cercare di **eliminare eventuali entità che possono essere combinate o entità che possono essere derivate da altre già presenti**.

Tutte le entità che sono presenti nel diagramma devono essere **primitive**, ovvero nessuna entità deve avere degli esempi in overlap con altre entità, nel caso si verifichi questo *overlap*, allora le *entità devono essere unite in una singola*.
![[Pasted image 20241223154211.png]]Nell'esempio sopra, non c'è un vero e proprio overlap, ma tutte le entità hanno un formato comune, il che permette la creazione di una singola entità che comprende tutte le restanti.
Possiamo, inoltre, notare che le 3 relazioni non sono del tutto indipendenti, infatti attraverso 2 qualsiasi relazioni posso ottenere la terza, di conseguenza posso utilizzare delle annotazioni per permettere al sistema di capire come e se inferire i dati dalle informazioni di dominio.

Le annotazioni sono:
- *Derivazione* (\*) e *semi-derivazione*(+)
	- Derivazione, quel parametro sarà sempre derivato a partire da una regola specificata, in questo caso il dato non potrà essere inserito a mano.
	- Semi-derivazione, il parametro viene derivato attraverso la regola se sono presenti i dati necessari per la derivazione, quindi si può anche inserire il dato manualmente.
- *Derivata on query* e *derivata on update* (\*\*), in questo caso il dato viene calcolato solo in caso di necessità e non a priori come nel caso precedente (è un aspetto che riguarda più la costruzione dello scheletro per il database o altri servizi che garantisce ORM)
![[Pasted image 20241223154929.png]]
Nel primo esempio in immagine vediamo un parametro derivato attraverso la formula 
- markup = retailPrice − wholesalePrice
Mentre nel secondo caso, essendo che tutti e 3 i parametri sono semi-indipendenti, posso scegliere arbitrariamente quali parametri inserire per calcolare l'ultimo, andando ad inserire per ogni relazione la formula per il calcolo
- markup = retailPrice − wholesalePrice 
- retailPrice = markup + wholesalePrice 
- wholesalePrice = retailPrice − markup

## Step 4
Nello step 4 si vanno ad inserire i **vincoli di unicità** all'interno delle relazioni che sono state individuate.
Nel caso delle relazioni unarie, possiamo definirle uniche a priori per la loro costruzione e di conseguenza le andiamo ad indicare nel diagramma con l'indicatore di unicità
![[Pasted image 20241227120531.png]]
Le relazioni di unicità possono essere di vari tipi
- *Many to one*
- *One to many*
- *One to one*
- *Many to many*

I vincoli di unicità sono necessari per indicare quelle che in ambito database sarebbero le **chiavi per individuare le altre informazioni**, ogni relazione deve quindi essere dotata di una chiave, che può essere singola o composta, inoltre possono essere presenti più possibili chiavi per la stessa relazione.
![[Pasted image 20241227120950.png]]

Per controllare che i vincoli di unicità individuati siano quelli corretti, possiamo utilizzare 2 metodo:
- **Key Length check**, per questo check *controllo che ogni relazione n-aria abbia almeno una chiave di lunghezza almeno n-1* (tranne per il caso della relazione unaria), se questo non è vero significa che **la relazione può essere scomposta in altri fatti atomici e di conseguenza bisogna fare uno split della relazione**. Avere dei predicati scorretti può portare:
	- Nel caso siano *troppo lunghe le chiavi*, avere delle *relazioni non elementari* che può complicare la modifica del diagramma nel futuro o l'aggiunta di nuovi concetti
	- Nel caso siano *troppo brevi*, *perdita di informazioni rilevanti*
- **Projection-join check**, controlla se la relazione può essere *scomposta andando a prendere in considerazione vari split per poi ricomporre i dati a partire dagli split ottenuti*, se i dati di partenza sono uguali a quelli ottenuti dopo lo split e il join allora la relazione è scomponibile, in caso contrario non lo è.

Sono anche presenti dei **vincoli di unicità esterni**, che vengono utilizzati per andare a inserire vincoli che non riguardano relazioni dirette, che se no non sarebbe possibile inserire all'interno del diagramma.
![[Pasted image 20241227125830.png]]
Per esempio, nella figura, viene inserito il vincolo di unicità per andare a specificare che ogni combinazione di time+room è associato al massimo con un solo Gruppo di tutoraggio.
Lo stesso concetto sarebbe anche specificato dalla forma
![[Pasted image 20241227130754.png]]
che però risulta **non** essere la minima in quanto la relazione può essere splittata come visto precedentemente.