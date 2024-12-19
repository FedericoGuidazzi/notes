📚 Subject: [[SISRV]]
⬅ [[1 - Introduzione ai sistemi di realtà virtuale]]
# Elementi di 3D Audio
## Presentazione Aurale
L'audio all'interno di un mondo 3D ha una grande importanza, quasi allo stesso livello della presentazione visuale, questo perché riesce da fornire moltissime informazioni all'utente e aiuta anche nell'immersione.
Il nostro cervello riesce a percepire e ricavare informazioni dall'audio grazie all'orecchio e alle caratteristiche del suono (che è un'onda che vibra nella stessa direzione in cui si muove), essendo un'onda le caratteristiche fondamentali sono:
- L'**ampiezza**, che determina il *volume* del suono.
- La **fase**, che determina la *posizione* da cui si è generato il suono.
![[Pasted image 20241009161200.png]]
Il suono fornisce importanti informazioni spaziali da 3 fenomeni:
- l'**ITD** (Interaural Time Delay), deriva dalla separazione delle orecchie, di conseguenza, una percepirà il suono con un ritardo (anche se piccolissimo) e ci darà l'informazione che il suono deriva da una posizione più vicina all'orecchio che ha percepito per primo il rumore.
- l'**IID** (Interaural Intensity Difference), deriva dal fatto che i tessuti di cui è composta la testa possano fare da filtro o da risonanza per il suono, andando a modificare il volume con il quale il suono viene percepito dall'orecchio.
- **Filtri della parte esteriore dell'orecchio**, ci possono essere dei fenomeni di assorbimento e rifrazione del suono causati dal padiglione.
## Gestione dell'audio spaziale
Per dare la sensazione di un rumore proveniente da una posizione che non è quella corretta (ovvero tutte le applicazioni che hanno a che vedere con un audio digitale), si possono seguire due metodi:
- **Creazione di un intero campo audio**, questo vuol dire che dobbiamo avere il controllo totale sull'aria attorno al/agli utente/i, *si riesce a fare attraverso n casse posizionate attorno all'utente che riproducono l'audio in maniera in maniera coordinata*, il che vuol dire che verrà applicato un delay a delle casse e un volume maggiore in base alla posizione dell'utente nel mondo virtuale, di conseguenza è anche necessario avere un tracking accurato dell'utente nello spazio.
  Questa soluzione è costosa ma riesce a funzionare bene anche con più utenti contemporaneamente.
  ![[Pasted image 20241009162557.png]]
- **Riproduzione degli stimoli nell'orecchio** (*Head-Related Transfer Function* (HRTF)), questo metodo consiste nella gestione dell'audio dell'utente attraverso l'*utilizzo di cuffie*, permettendo di gestire il campo uditivo con un solo dispositivo, in maniera totalmente equivalente al metodo di prima.
  Questo metodo funziona grazie alla differenza di percezione che abbiamo delle onde nel dominio della frequenza.
  Possiamo ottenere un buon audio grazie a delle misurazioni ottenute mettendo un microfono nel timpano di diversi utenti e campionando l'audio ottenuto, per ottenere dei buoni dati è necessario riprodurre il suono varie volte andando a cambiare volta per volta l'altezza e l'azimut e cambiando anche la persona che porta il microfono, in quanto l'altezza e la composizione fisica possono cambiare l'audio che viene rilevato. Questi dati prendono il nome di HRIR (HRTF se viene applicata la trasformazione di fourier).
  Esistono diversi databases che forniscono questi dati in quanto calcolarli è un processo molto laborioso.
➡ [[]]