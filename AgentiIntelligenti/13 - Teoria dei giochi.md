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


➡ [[]]