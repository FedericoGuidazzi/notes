📚 Subject: [[SISRV]]
⬅ [[]]

# Introduzione ai sistemi di realtà virtuale
Un sistema di realtà virtuale è una simulazione che dà il senso della **posizione** e dell'**azione** ad un utente, producendo dei **feedback** basati su uno o più sensi, dando la sensazione di essere **immersi** in una realtà.

### Concetti Base
Per far si di creare un ambiente che l'utente può percepire come credibile, ci deve essere la possibilità di eseguire delle task in maniera efficiente e confortevole.
I fattori necessari per una buona esperienza dal punto di vista fisico e psicologico sono:
- **Immersione**
- **Presenza**
#### Immersione
L'immersione deriva dalla configurazione fisica dell'utente, esistono diverse modalità con cui la VR lavora:
- fully immersive, es. visore
- semi-immersive, es. grande schermo (CAVE)
- nonimmersive, es. VR nel computer
La classificazione varia in base a quanto l'utente riesce ad *interagire con l'esterno* mentre all'interno della simulazione.
#### Presenza
La presenza ha a che fare con l'**aspetto psicologico**, infatti va a quantificare quanto l'utente si sente all'interno della simulazione.
La presenza può portare ad un *coinvolgimento* e a delle *reazioni emotive* da parte dell'utente.
La presenza va modellata in base ai contesti che si vogliono creare, infatti in alcuni casi, come le simulazioni per applicazioni mediche, è più importante mantenere un buon livello nei feedback, piuttosto che fornire una qualità di simulazione ottima.

### Altri elementi fondamentali
Oltre l'immersione e la presenza, ci sono altri elementi fondamentali per permettere all'utente di avere la migliore esperienza possibile, come:
- Qualità del mondo virtuale
- Feedback sensoriale
- Interattività
In generale, per ottenere una buona simulazione, si devono bilanciare 3 aree:
- **Interattività**, possibilità di spostarsi e interagire con il mondo 3D
- **Immersione**, sentirsi interno al mondo virtuale
- **Real time**, tempi di risposta brevi
![[Pasted image 20241004195640.png]]
## Tipologie di realtà virtuali
Esistono 2 tipologie di sistemi VR:
- Windows on Word (WOW), utilizzano un normale PC per mostrare un mondo virtuale.
- Immersive VR, immergono l'utente interamente all'interno del mondo virtuale, andando a togliere tutti gli input e collegamenti con il mondo reale.
- Telepresenza, sposta virtualmente l'utente in una presenza diversa da quella in cui si trova, solitamente permettendo di comandare da remoto, attraverso dei sensori, delle macchine per eseguire azioni che risulterebbero pericolose, la differenza rispetto alla VR è che l'utente viene immerso in un ambiente reale e non uno artificiale.
- Realtà aumentata, integrazione di elementi virtuali ad elementi reali
- Distributed VR, sistema di VR che permette a più user di interagire con lo stesso ambiente grazie ad un ambiente distribuito.
## Sistemi di realtà virtuale
La creazione di un sistema di realtà virtuale necessita l'integrazione di più componenti.
Questi componenti sono sia Hardware che Software.
![[Pasted image 20241004200927.png]]
  Nell'immagine possiamo individuare quelli che sono i componenti fondamentali di un sistema VR:
  - Tracking system. sistema che permette di tracciare i movimenti dell'utente e rispecchiarli nel mondo virtuale
  - Input devices, sistemi di input con il quale l'utente interagisce e i quali comportano delle azioni all'interno del mondo virtuale (tuta aptica, guanti, sensori)
  - Simulation computation, software che permette di computare gli input ricevuti e far si che si riflettano nel mondo virtuale
  - Graphics computation, computazione grafica che riporta a livello visivo la computazione effettuata
  - Visual Display, dispositivo di output che permette all'utente di visualizzare il mondo virtuale (schermo, visore)
  - Audio Computation, computazione dell'audio che dipende dalla computazione della simulazione
  - Haptic computation, computazione del feedback da fornire all'utente derivante dalla computazione della simulazione
  - Audio display, strumento con il quale viene fornita la computazione audio all'utente (sistema audio immersivo, cuffie)
  - Haptic display, strumento con il quale viene fornito un feedback aptico all'utente (tuta aptica, sistema di vibrazione)
La computazione viene eseguita su un motore di computazione che prendendo tutti gli input restituisce lo stato della simulazione, ovvero audio, video e feedback in caso di accessori di output dedicati.
La computazione può essere eseguita su uno o più computer a causa della complessità computazionale richiesta per ottenere dei risultati in un arco di tempo abbastanza breve per riuscire a gestire a meglio la latenza.
### Head Mounted Display (HMD)
È l'accessorio più diffuso e la prima cosa che viene in mente quando si parla di VR, coinsiste in un elmetto che permette la visione del mondo virtuale attraverso uno schermo.
Questo dispositivo può permettere la realtà virtuale o, in alcuni casi, la realtà aumentata.
Inoltre, solitamente, ha delle cuffie integrate direttamente nel visore e dei sensori che vengono utilizzati per il traking.
#### Pro
I pro di questa soluzione sono:
- Buon senso di immersione
- L'utente può muoversi in grandi spazi (ha libertà di movimento, anche se non totale)
- Costa poco
- È facile da installare e utilizzare
#### Contro
I contro sono:
- È invasivo
- Distorsione dell'immagine soprattutto nella parte di visione periferica
- La latenza e il completo distaccamento dal mondo possono portare a dei problemi di nausea
### HUD Display
È un display trasparente che permette la visualizzazione di informazioni, soprattutto testuali, senza perdere il contatto con l'ambiente circondante.
Questi dispositivi sono utilizzati soprattutto in ambito automotive per poter dare informazioni alla guida.
### Large Screen Stationary Display
CAVE ne è un esempio, sono dei grandi schermi su cui viene proiettato il mondo virtuale.
Permettono un senso di immersione grazie alla proiezione su tutto il campo visivo e grazie al tracking continuo dell'utente nello spazio che permette di aggiornare le proiezioni sugli schermi.
Un altro punto a favore di questa tecnologia è il fatto che l'utente non debba indossare nessun tipo di accessori per immergersi nell'esperienza virtuale.
### Binocular Omni-Orientation Monitor (BOOM)
Consiste in un visore montato su un braccio meccanico.
Grazie al fatto che il tutto è collegato ad un braccio, il tracking avviene in real time e si possono utilizzare feedback tattili, come l'indurimento delle giunzioni del braccio.
Ha il contro, però, di essere fisso in un punto, di essere molto più costoso di un semplice visore e solitamente, il livello di immersione risulta essere minore rispetto alle altre tecnologie.
### Strumenti aptici
Gli strumenti aptici permettono di dare dei feedback tattili all'utente che sta utilizzando il sistema.
Il feedback può essere dato da impulsi elettrici/contatto sulla pelle, o in alcuni casi, direttamente a livello muscolare/scheletrico.
Gli strumenti aptici possono essere:
- fissi, come il braccio robotico nella tecnologia BOOM
- stazionari, come i guanti/tute che permettono di dare delle sensazioni tattili agli utenti
## Dispositivi di input e di tracking
Il tracking dell'utente e la possibilità che questo ha di interagire con l'ambiente virtuali sono necessari per la c*reazione di una esperienza sufficiente all'interno della simulazione*.
Non esiste, per il momento, un dispositivo che riesca a dare dei risultati ottimi sotto tutti i punti di vista, è quindi necessario scegliere accuratamente i dispositivi in base all'utilizzo che si vuole fare della VR.
Per esempio se si deve sviluppare un'applicazione molto sensibile e accurata, sarà necessario utilizzare sistemi cablati piuttosto che senza cavi, andando così a peggiorare il comfort dell'utente ma andando a migliorare la qualità dell'input.
I sistemi di tracking più diffusi sono:
- Elettromagnetici
- Meccanici
- Ottici
- Giroscopici e inerziali
- Tracking muscolare e neuronale
## Software per la Realtà Virtuale
I software necessari per applicazioni in realtà virtuale sono:
- **Motore fisico,** necessario per simulare le leggi della natura
- **Librerie di Rendering**, convertono il mondo generato dal computer in un mondo familiare all'utente, andando a migliorare la user experience
- **Librerie VR**, permettono di creare output in linea con quelle che sono le azioni dell'utente e la sua posizione, andando ad interfacciarsi con il sistema di tracking ed eventuali ulteriori dispositivi di input



➡ [[]]