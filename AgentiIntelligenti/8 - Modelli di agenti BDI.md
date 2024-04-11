📚 Subject: [[AgentiIntelligenti]]
⬅ [[7 - Logica Epistemica]]
# Metodi formali per sistemi di agenti

I metodi formali giocano 3 ruoli:
* **Specificare i sistemi**
* **Programmare i sistemi**
* **Verificare i sistemi**

In questa parte ci focalizziamo sulla parte dello **specificare** i sistemi.
Ci sono due correnti in questo:
* Cohen-Levesque
* Rao-Georgeff

Entrambe le teorie, con differenze, permettono di rappresentare **stati mentali degli agenti** (belief, goals, intentions, actions) e di **ragionare su aspetti dinamici per mezzo di logiche temporali e multimodali**.

## Cohen-Levesque intention logic

L'idea è quella di esplorare le relazioni che le intenzioni hanno nel mantenere questo bilanciamento.
Vengono individuati, come da Bratman, 3 oggetti fondamentali per descrivere il comportamento razionale degli agenti:
* **Belief**
* **Desire**
* **Intention**

### Proprietà delle intenzioni

Le intenzioni devono seguire un'insieme di proprietà:
* Le intenzioni pongono dei problemi per gli agenti, che devono determinare modi di soddisfarle.
* Le intenzioni forniscono un "filtro" per adottare altre intenzioni che non devono entrare in conflitto.
* Gli agenti "tracciano" il successo delle loro intenzioni, e sono disposti a tentare di nuovo se il loro tentativo fallisce.
* Gli agenti credono che le loro intenzioni siano possibili.
* Gli agenti non credono che non riusciranno a soddisfare le loro intenzioni.
* In certe circostanze, gli agenti credono che riusciranno a soddisfare le loro intenzioni.
* Gli agenti non si aspettano tutti i side-effects delle loro intenzioni.

### La logica

La logica si compone di 4 operatori fondamentali:
* **BEL**, esprime una credenza dell'agente ($BEL_i$ ϕ)
* **GOAL**, esprime l'obiettivo di un agente ($GOAL_i$ ϕ)
* **HAPPENS**, esprime che un'azione accadrà successivamente (HAPPENS α)
* **DONE**, esprime che un'azione è stata appena conclusa (DONE α)

Esistono anche ulteriori logiche derivate che vanno ad aggiungere anche gli operatori:
* **G**, la condizione vale sempre (G ϕ)
* **F**, la condizione vale a volte (F ϕ)
* **LATER**, l'azione verrà fatta in futuro (LATER ϕ)
* **BEFORE**, l'azione è stata compiuta precedentemente (BEFORE ϕ)

Sono presenti anche altri tipi di GOAL che prendono il nome di:
* **A-GOAL**, che vengono ritenuti falsi dall'agente ma che in futuro vorrebbe che diventino veri.
* **P-GOAL**, è un goal che l'agente vuole che sia verificato e continua a mantenerlo in considerazione fino a che
	* l'agente non crede che il goal sia soddisfatto.
	* l'agente non crede che il goal non sia soddisfacibile.

## Rao-Georgeff's BDI logic

Questo tipo di logica varia da quella di Cohen-Levesque in quanto le intenzioni non sono più derivate dagli altri operatori, ma trovano un loro posto insieme a BEL e GOAL.
Inoltre i mondi non sono più successioni di eventi ma sono **strutture temporali branching time**, ovvero per ogni azione eseguita o no si possono espandere varie linee temporali (utile per scopi come la pianificazione).


➡ [[9 - Sistemi Multi-Agente e Comunicazione tra Agenti]]