## Percezione della profondità e Stereoscopia
La percezione della profondità è data da 4 componenti:
- Binocular disparity, consiste nel fatto che gli occhi vedano delle immagini leggermente traslate tra loro (se chiudo un occhio vedrò gli oggetti più a destra o sinistra), grazie a questa differenza il cervello riesce a intuire quanto un oggetto è distante, questo meccanismo funziona fino a che la differenza di posizione dell'oggetto diventa impercettibile, ovvero circa 10-15 metri.
- Convergence, consiste nella rotazione dell'occhio per visualizzare un punto specifico
- Accomodation, permette di mettere a fuoco un oggetto andando a ingrandire o rimpicciolire la pupilla
- Altri fattori (geometrici, di esperienza o di memoria)
![[Pasted image 20241011193632.png]]
L'unione tra convergence e accomodation da un ulteriore input al cervello per stimare la profondità.
Altri fattori che possono tornare utili per capire la profondità sono:
- Prospettiva
- Occlusione degli oggetti
- Ombre
- Motion parallax
- Grandezza relativa
![[Pasted image 20241011195217.png]]
Ci sono anche altri aspetti da tenere in conto per quanto riguarda il riconoscimento della prospettiva derivante da una sola immagine (ovvero la possibilità di capire la prospettiva anche con un solo occhio aperto):
- l'esperienza può darci idea della grandezza di un oggetto e di conseguenza può farci capire la lontananza da noi
- Distanza dalla linea dell'orizzonte, gli oggetti più vicini alla linea dell'orizzonte saranno più lontani rispetto agli oggetti lontani da questa
- Altezza relativa
Tutti questi punti possono essere utilizzati in combinazione per dare all'utente la percezione della profondità anche utilizzando strumenti che non sono 3D (schermo, visore)
Gli schermi che sono stati ideati con l'idea di dare un senso di profondità all'utente sono:
- Schermi Autostereoscopici
- Non autostereoscopici
- Head Mounted
- Display multipli
## Cattura stereoscopica
Il più semplice modello di fotocamera prende il nome di pinhole e consiste in un buco nel quale passano i raggi di luce, andando ad imprimere nella parete opposta l'immagine capovolta.
![[Pasted image 20241015151128.png]]
Questa tipologia di camera, che nella realtà fa fatica ad esistere in quanto nel buco deve passare un solo raggio, e questo è impossibile, è governata dalle seguenti formule
![[Pasted image 20241015151316.png]]
Ovvero le coordinate della figura catturata sono riportate in maniera inversa (data dalla moltiplicazione con la matrice di inversione) e ingrandita o rimpicciolita in base al fuoco e alla distanza.

Un funzionamento simile viene utilizzato per l'individuazione di metriche di una scena a partire da una immagine scattata da due diversi punti, attraverso la **geometria epipolare**.
### Geometria Epipolare
Questa geometria dice che individuando dei punti esatti nelle immagini scattate dai due punti di vista, posso riuscire a dare una stima precisa delle dimensioni della scena 3D.
![[Pasted image 20241015151903.png]]
In particolare, ci interessano le rette $X_L - e_L$ e $X_R-e_R$ che prendono il nome di linee epipolari e che ospitano tutte le proiezioni dei punti visibili dall'altra camera, di conseguenza, se riesco ad individuare con precisione in una camera, so che lo stesso punto sarà nella linea epipolare dell'altra camera e questo mi permette di fare triangolazione e di ottenere la dimensione dell'oggetto in immagine.
### Modello a camere parallele
Il ragionamento per ottenere delle informazioni riguardanti la posizione dalle immagine 2D al mondo 3D è possibile farlo anche attraverso un sistema di camere parallele.
![[Pasted image 20241015153132.png]]

![[Pasted image 20241015153451.png]]
Attraverso le formule posso quindi riuscire a determinare delle informazioni riguardanti le posizioni di oggetti all'interno dell'immagine 2D (e facendo le formule inverse del mondo 3D).
La disparità, ovvero quanto l'oggetto che sto analizzando è distante dal punto centrale, è data da 
![[Pasted image 20241015153611.png]]
La disparità orizzontale decresce con l'aumentare della distanza del punto preso in considerazione.
Sarebbe possibile anche calcolare la disparità verticale ma le cose da tenere in considerazione e di conseguenza i calcoli si complicano di molto.