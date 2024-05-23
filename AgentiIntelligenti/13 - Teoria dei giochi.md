📚 Subject: [[AgentiIntelligenti]]
⬅ [[12 - Model Checking]]

# Teoria dei giochi

Un gioco è definito da:
- Giocatori, agenti che prendono decisioni, solitamente sono *egoisti* (cercano di massimizzare il loro profitto non curandosi delle intenzioni degli altri).
- Strategie, solo le azioni che ogni giocatore può scegliere per arrivare al suo scopo ultimo.

Il risultato di un gioco prende il nome di **Strategy Profile**, e racchiude le informazioni riguardanti le strategie adottate da ogni giocatore. 

Ogni strategia può essere descritta da delle *utility functions*, che hanno lo scopo di associare ad ogni risultato possibile un numero, che va ad indicare quanto la strategia sia buona.

Attraverso l'utilizzo delle utility functions è anche possibile costruire una *matrice di payoff*, in cui sono indicati tutti i valori numerici per tutti i giocatori.

![[Pasted image 20240516105607.png]]

L'utilità principale della teoria dei giochi è quella di individuare una **strategia razionale**, ovvero la migliore strategia possibile date tutte le condizioni.

ES:
Nel caso del dilemma del prigioniero ci sono due giocatori (Alice e Bob), questi possono decidere se testimoniare o no, esistono le seguenti combinazioni di strategie:
- Se uno testimonia e l'altro no, chi non lo ha fatto si prende 10 anni e l'altro 0.
- Se entrambi testimoniano prendono 5 anni.
- Se nessuno testimonia prendono entrambi 1 anno.
Quale è la soluzione migliore per gli agenti?

La matrice dei payoff di questo caso è la seguente:
![[Pasted image 20240516110205.png]]
Possiamo individuare che la **strategia dominante** (ovvero la strategia che sotto tutti i punti di vista è migliore delle altre, che prendono il nome di *strategie dominate*) per entrambi dato che possono succedere le seguenti cose:
- se Bob testimonia -> 5 anni se Alice testimonia e 10 se non lo fa, quindi in questo caso è meglio testimoniare.
- se Bob si rifiuta, Alice prende 0 anni se testimonia e 1 anno se rifiuta. Quindi anche in questo caso testimoniare è meglio.
Di conseguenza non ci sono strategie migliori di questa, il che vale per entrambi.

Il risultato che si ottiene in questo caso si dice non **Pareto Optimal** (ovvero la soluzione migliore sotto tutti i punti di vista), in quanto è presente un'altra soluzione in cui entrambi i giocatori ne escono con un output migliore (ovvero che entrambi rifiutino), ma la strategia che dovrebbe essere presa non è *razionale né ottimale* per nessuno dei due giocatori.

La strategia individuata come migliore viene detta *punto di equilibrio* o *equilibrio di Nash*, ovvero è la soluzione razionale che porta entrambi i giocatori alla migliore soluzione qualsiasi sia la mossa dell'altro giocatore.

Possono esistere anche casi in cui non esiste una **strategia dominante** e in cui sono presenti più punti di *equilibrio di Nash*, in questo caso, per poter fare la scelta migliore, bisogna valutare se esiste un punto di equilibrio migliore dell'altro per entrambi gli agenti, nel caso esiste, le probabilità che entrambi gli agenti lo scelgano sono elevate, nel caso in cui invece non esista, bisogna cercare sia di *comunicare*, stabilendo una convenzione prima di iniziare il gioco, sia di *negoziare* per raggiungere un accordo durante il gioco che soddisfi entrambi.

Possono esistere anche casi in cui non sono presenti equilibri di Nash, questa tipologia di giochi prende il nome di **giochi a somma zero**, ovvero un gioco in cui le vincite sono uguali e opposte per gli agenti (se vince uno perde l'altro e viceversa), in questi giochi, non esiste una strategia vincente, di conseguenza devono essere attuate delle *strategie miste*.

Le **Strategie miste**, consistono nel dare una probabilità di esecuzione ad ognuna delle strategie possibili e poi sceglierne una, ovviamente la somma delle probabilità delle strategie deve *sommare a 1*.

- [9] Ogni gioco in cui ogni giocatore ha un insieme finito di strategie possibili ha un equilibrio con strategie miste.

## La teoria dei giochi nella realtà

Fino ad ora abbiamo preso per definizione che gli agenti *self-interested* (egoisti) e *non collaborativi*, e abbiamo quindi ipotizzato soluzioni da questa base di partenza.
Se però eliminiamo questi precondizioni, allora le soluzioni che si possono andare a considerare **diventano altre**, poiché attraverso la **collaborazione**, molto spesso si arriva a *soluzioni* che vanno a *favorire entrambi gli agenti* (nel problema del prigioniero, con agenti collaborativi si riuscirebbe a optare per la soluzione ottimale).

Inoltre nel caso che il gioco venga *ripetuto varie volte*, possiamo notare anche in questo caso che le soluzioni finali risultano **diverse** rispetto a se il gioco fosse one-shot, questo anche se manteniamo le definizioni degli agenti self-interested e non collaborativi.

Oltre a questo, nelle applicazioni della teoria dei giochi nella realtà, si aggiungono anche *altri fattori* all'equazione, come una conoscenza degli attori che li porta a collaborare, la soggettività degli agenti (preferire una soluzione ad un'altra) e la non razionalità.

In linea generale, comunque, come anche evidenziato dal torneo di Axelrod, si è notato come *collaborare è solitamente la soluzione migliore da prendere*.

➡ [[]]