📚 Subject: [[AgentiIntelligenti]]
⬅ [[6 - Logica Modale e Agenti]]
# Logica epistemica

La logica epistemica può essere associata alla [[6 - Logica Modale e Agenti |logica modale]] facendo un piccolo cambiamento, ovvero l'introduzione degli operatori **K** e **B**, che rappresentano la conoscenza (K) e le credenze (B).

I due nuovi operatori seguono le stesse logiche che erano presenti per quanto riguarda l'operatore ☐ della logica modale, ovvero godono:
* **Assioma K**, $K_a$(ϕ ⇒ ψ) ⇒ ($K_a$ ϕ ⇒ $K_a$ ψ)
* **Necessitation**, se ϕ è valida, allora $K_a$ϕ è valida

## Assiomi per knowledge e belief

Sono presenti 4 assiomi per riuscire a utilizzare in maniera corretta gli operatori nella logica modale:
* **Assioma D (serialità)**, la conoscenza di un agente non è contraddittoria $Kϕ ⇒ ¬K¬ϕ$
* **Assioma T (riflessività)**, ciò che conosce l'agente è vero, questo lo accettiamo per le conoscenze ma non per le credenze (non vogliamo che l'agente conosca qualcosa di falso, ma accettiamo che un agente possa credere qualcosa di falso) $Kϕ ⇒ ϕ$
* **Assioma 4**, un agente conosce di conoscere qualcosa $Kϕ ⇒ KKϕ$ (introspezione positiva)
* **Assioma 5**, un agente conosce di non conoscere qualcosa $¬Kϕ ⇒ K(¬Kϕ)$ (introspezione negativa)

➡ [[8 - Modelli di agenti BDI]]