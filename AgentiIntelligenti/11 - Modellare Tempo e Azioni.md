📚 Subject: [[AgentiIntelligenti]]
⬅ [[10 - Robustezza e Agent-based Modeling]]

# Modellare Tempo e Azioni

Come visto in precedenza ogni agente situato in un sistema deve *ragionare su tempo ed azioni* per poter conseguire i propri obiettivi.

Da questo si sviluppa la logica temporale.

## Logica Temporale

Sono presenti parecchie varianti di questa logica, nel nostro caso prenderemo in considerazione situazioni in cui il tempo:
- È **discreto**
- Ha un **momento iniziale**
- È **infinito**
Vedremo due variazioni:
- *Linear-time logic*, in cui il tempo si presenta lineare
- *Branching-time logic*, in cui il tempo si presenta come un albero

### Linear Temporal Logic (LTL)

In questa logica un modello è una struttura lineare del tipo <S, x, L>, in cui:
- S, è l'insieme degli stati
- x, è una sequenza infinita di stati
- L, è l'insieme delle proposizioni vere per ogni stato

Le proposizioni di questa logica (*PLTL*) sono le seguenti:
- p
- α ∨ β
- ¬ α
- Xα, significa che α sarà vero nel prossimo istante di tempo
- α U β, è vero al tempo t se e solo se β è vero in un futuro istante t' e α è vero in tutti gli istanti fra t e t’
È possibile anche derivare altri operatori modali:
- Fα ≡ true U α (che significa: prima o poi α)
- Gα ≡ ¬ F ¬α (che significa: sempre α)

### Computation Tree Logic (CTL*)

In questa forma di logica ogni istante può avere molteplici istanti successivi, andando a creare alberi infiniti.

In CTL* è possibile formulare:
- *path formulas*, simili alle formule LTL
- *state formulas*, riguardano gli infiniti cammini uscenti da uno stato

#### State Formulas

Gli state formulas sono:
- p 
- α ∨ β 
- ¬ α 
- Aπ (per tutti i cammini uscenti da uno stato vale π) 
- Eπ (esiste un cammino uscente da uno stato per cui vale π)
Gli operatori A e E sono duali

#### Path Formulas

I path formulas sono:
- α 
- π ∨ ρ 
- ¬ π 
- Xπ 
- π U ρ

CTL* come LTL esprime i modelli secondo una tripla <S, T, L> dove:
- S, è l'insieme degli stati
- T, è un albero infinito in cui gli stati sono rappresentati dai nodi
- L, è l'insieme delle proposizioni vere per ogni stato


Il linguaggio CTL* risulta essere *troppo complicato* e troppo *poco efficiente* per essere utilizzato nel model checking, di conseguenza viene utilizzato un linguaggio più semplice, **CTL**.

In CTL le path formulas diventano le stesse di LTL.

In base al problema che si sta affrontando, e in base alle caratteristiche che questo ha si sceglie CTL o LTL.

## Ragionare sulle azioni

Come detto precedentemente un agente deve essere in grado di ragionare sul tempo e sulle azioni.
Il ragionamento sulle azioni si basa sulla logica classica e si compone di 3 aspetti principali delle situazioni:
- Situazioni, è lo stato del mondo ad un istante t
- Fluenti, proposizioni il cui valore varia da uno stato all'altro (sta_portando(robot, oro, $S_0$))
- Azioni, causano un cambiamento nello stato del mondo

### Azioni

Ogni azione è caratterizzata da due assiomi:
- Assioma di possibilità, dice quando è possibile eseguire l'azione
- Assioma di effetto, specifica cosa succede quando l'azione è compiuta

### Frame Problem

Ogni azione va ad intaccare un numero finito di Fluenti, di conseguenza è necessario individuare un modo per permettere di rappresentare in modo efficiente il cambiamento senza dover specificare che tutti gli influenti non intaccati dall'azione rimangono uguali.
Da questo nascono i *Successor State Axioms*.

#### Successor State Axioms

Questa tipologia di Assiomi serve per specificare, in maniera efficiente, quale è il cambiamento che l'azione ha comportato al fluente, essi si riferiscono ad un solo fluente alla volta.


➡ [[12 - Model Checking]]