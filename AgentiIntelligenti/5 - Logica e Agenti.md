📚 Subject: [[AgentiIntelligenti]]
## Logica per gli agenti

La logica è stata ideata molti secoli fa per avere un modo formale di:
* **Rappresentare la conoscenza**, questo perché:
	- ha una **semantica precisa**
	- rappresenta la conoscenza in maniera **dichiarativa**
* **Ragionamento automatico**, attraverso delle regole di inferenza

La logica per sua natura è molto utile per riuscire a **spiegare la conoscenza** e utilizzarla per poter **fare ragionamento**, ma non è molto utile per quanto riguarda la **descrizioni delle azioni di un agente**.

### Logica classica (Proposizionale)

La logica classica si compone di un'insieme di condizioni legate tra loro da connettivi (And, Or, Not).
Queste condizioni hanno due possibili stati, *True* o *False*, quando una espressione logica deve essere verificata, si prendono gli stati delle varie condizioni e si verificano, andando ad ottenere la risposta finale (anche questa sarà un Booleano).
I possibili connettivi logici sono AND (∧), OR (∨) e NOT (¬), che possono anche essere combinati tra loro per ottenere connettivi più complessi.

Es:
In0,0 ∧ Facing_north ∧ ¬Dirt0,0 ⇒ Do_forward

Ovvero, se mi trovo in posizione 0,0, sono rivolto a nord e non è presente terra in 0,0 allora vado avanti.

Una formula si dice **soddisfacibile** se esiste almeno un modello per cui le condizioni risultano verificate.
Una formula si dice **valida** se è verificata da tutti i modelli.

### Problemi della logica classica

Per quanto riguarda applicazioni che coinvolgono gli agenti, è necessario poter **mantenere le credenze che questi hanno** per riuscire a capire al meglio per quale motivo sono state **intraprese determinate azioni**, questo però non ci è concesso dalla logica classica, in quanto, questa, **non riesce a modellare** il fatto che soggetti diversi possano avere **credenze diverse**, andando a dare come verificata qualsiasi conoscenza che viene inserita anche se non corretta, portando così poi a una inconsistenza.

Per poter riuscire a risolvere il problema si deve cambiare la logica utilizzata andando a sostituirla con quella **[[6 - Logica Modale e Agenti|modale]]**.





