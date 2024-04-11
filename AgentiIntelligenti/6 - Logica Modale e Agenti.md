📚 Subject: [[AgentiIntelligenti]]
⬅ [[5 - Logica e Agenti]]
# Logica Modale

La logica modale proposizionale cerca di risolvere il problema della logica del prim'ordine (non posso rappresentare il cambiamento delle informazioni né il fatto che più soggetti possano avere delle idee diverse tra loro) andando ad inserire 2 nuovi operatori logici:
* ☐, necessariamente è così (necessariamente pioverà)
* ◊, è possibile che sia così (è possibile che piova)

Un Modello è rappresentato da una tripla <W,R,L> dove:
* W, indica l'insieme dei mondi
* R, è la relazione di accessibilità tra mondi
* L, è l'insieme di proposizioni vere valide per ogni mondo

![[Pasted image 20240404110519.png | center | 600]]

La formula ☐X è vera se è vera in tutti i mondi accessibili dal mondo in cui mi trovo, mentre la formula ◊X è vera se è vera in un qualche mondo accessibile dal mondo in cui mi trovo.

Nella figura sopra, possiamo dire che **☐p** è **vero** nel mondo **w2**, poiché è **vero in tutti i mondi con cui w2 può comunicare** (w2 e w3), ma **non** è **vero** **☐r** perché è **vero** **solamente** in **w3** e non in w2.
**◊r è vero in w2** poiché **vero** in **w3**.

➡ [[7 - Logica Epistemica]]