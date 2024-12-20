📚 Subject: [[AgentiIntelligenti]]
⬅ [[11 - Modellare Tempo e Azioni]]

# Model Checking

Il Model Checking è un metodo per *verificare le proprietà* di sistemi di agenti, o più in generale di sistemi concorrenti.

Fa questo verificando le proprietà attraverso le *logiche temporali* dei modelli e gli *automi a stati finiti* che descrivono lo sviluppo di un modello.

Il comportamento di un sistema può essere descritto da un **Transition System**.

- [9] Un Transition System consiste in un insieme di stati, un insieme di transizioni fra gli stati e una funzione che associa ad ogni stato un insieme di proposizioni. 

![[Pasted image 20240517114354 1.png]]
Gli stati sono rappresentati dai nodi, le transizioni dalle frecce di collegamento dei nodi e l'insieme di proposizioni si trovano all'interno del nodo.

Attraverso il Transition System individuato possiamo fare model checking, ovvero vogliamo verificare che *per ogni modello φ* (descritto in LTL) *esiste un cammino infinito π appartenente al Transition System*.

Solitamente la dimostrazione viene fatta per **refutazione**, ovvero si verifica che non ci sia nessun caso in cui sia vero il contrario di quanto affermato.
Per esempio se nel transition system in figura voglio verificare che **G(Start ⇒ F Heat)**, ovvero è sempre vero che c'è se start allora ci sarà almeno una volta in cui Heat sarà vero, andrò a cercare se è verificato almeno una volta il contrario (*controesempio*), **¬G(Start ⇒ F Heat)**, che nel nostro caso risulta verificato perché esiste un loop infinito in cui la condizione negata è verificata (1 2 5 2 5 2 5 ………), di conseguenza non posso affermare **G(Start ⇒ F Heat)**.
Al contrario però posso affermare che **(¬Heat) U Close**, ovvero non è verificato Heat fino a che non è verificato Close, poiché non è presente nessun loop infinito all'interno del Transition System per il quale il contrario è verificato.

## LTL e automi su stringhe infinite

Se la proprietà da dimostrare è rappresentata con una formula LTL, il model checking può essere realizzato usando automi di Büchi, ossia automi che accettano stringhe infinite.

Un automa di Büchi ha esattamente la stessa struttura di un tradizionale automa a stati finiti, ma accetta stringhe infinite. L’ automa < Σ,S, δ, $S_0$,F> consiste di un *alfabeto Σ*, un insieme di *stati S*, una *funzione di transizione δ ⊆ S × Σ × S*, un insieme di *stati iniziali $S_0$* e un insieme di *stati di accettazione F*.

Una stringa risulta coerente con il modello se è *compatibile con δ* (ovvero è un cammino infinito presente nel grafico dell'automa), e *almeno uno stato di accettazione F appare infinite volte nella stringa*. 

Un vantaggio di utilizzare gli automi di Büchi per il model checking è che il sistema modellato e le proprietà da verificare possono essere rappresentati nello stesso modo attraverso gli automi di Büchi, semplicemente rappresentando il modello come un automa di Büchi in cui tutti gli stati sono stati di accettazione.
Inoltre è molto semplice tradurre una formula LTL in un automa di Büchi.

### Model Checking utilizzando l'automa di Büchi.

Il model checking utilizzando l'automa di Büchi risulta essere molto semplice, basta eseguire i seguenti passaggi:
- siano dati il transition system π e la formula LTL φ da verificare
- costruire i due automi di Büchi ℬ(π) e ℬ(¬φ)
- costruire l’automa di Büchi che accetta l’intersezione dei linguaggi accettati da ℬ(π) e ℬ(¬φ) (il prodotto dei due automi di Büchi)
- ogni run dell’intersezione sia un run infinito di π sia un modello di ¬φ
- se l’intersezione è vuota, allora φ vale per π, altrimenti un run dell’intersezione fornisce un controesempio.
  
L'ultimo passo risulta essere **lineare** in tempo computazionale, ma la *costruzione dell'automa* può risultare **esponenziale** rispetto alla dimensione della formula.


Oltre alla verifica di proprietà, il model checking, può essere utilizzato anche per altri scopi, come la **pianificazione**, infatti con gli stessi passi è possibile individuare se un *achievement goal* è soddisfabile o no.

Per il momento abbiamo visto come è possibile fare model checking utilizzando LTL, è ovviamente possibile farlo anche con CTL ma seguendo un diverso approccio.


➡ [[13 - Teoria dei giochi]]