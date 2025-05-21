## Introduzione

Nel contesto di questa attività di prototipazione rapida (_fast prototyping_), è stato affrontato lo **studio e la modellazione algoritmica del problema del cammino minimo in grafi con costi temporali variabili**, noto formalmente come **Time-Dependent Shortest Path Problem (TDTSP)**.

L’obiettivo è stato quello di **sviluppare rapidamente un prototipo funzionante**, in grado di risolvere istanze del problema su grafi diretti in cui **il costo degli archi non è costante**, ma dipende dal momento in cui vengono attraversati. A tale scopo è stato utilizzato ChatGPT per guidare la progettazione, la stesura del codice Python e l’analisi iterativa della correttezza e delle prestazioni della soluzione sviluppata.
## Definizione formale del problema

Il **Time-Dependent Shortest Path Problem (TDTSP)** può essere definito formalmente come segue:

Given a directed graph, a nonnegative transit-time function c_e(t) for each edge e = (v, w) (where t is the time to leave v), a source node s, a destination node d and a departure time t0, the time-dependent shortest path problem asks to ﬁnd an s,t-path that leaves s at time t0 and minimizes the arrival time at d.
## Assenza della proprietà FIFO

Nel contesto affrontato, si considera esplicitamente che **la proprietà FIFO (First-In-First-Out) non vale**. Formalmente, per un arco e t1≤t2 **non è garantita** la seguente disuguaglianza:

t1+c_e(t1) ≤ t2+c_e(t2)

In altre parole, la funzione di **tempo di arrivo** t+c_e(t)t + c_e(t) **non è necessariamente crescente**.  
Questo implica che **partire più tardi da un nodo non garantisce un arrivo più tardi** a destinazione, e anzi, potrebbe essere vantaggioso **attendere** o **partire più tardi** per sfruttare un costo temporaneo più basso sull’arco successivo, in questa istanza del problema però non è concessa l'attesa ad un nodo affinché il costo decresca, in quanto è stato dimostrato che ogni istanza di un problema non FIFO può essere ricondotta ad un'istanza in cui la proprietà vale, rendendo il problema non NP Hard.
## Obiettivo della prototipazione
La prototipazione ha avuto lo scopo di:
- Modellare un grafo time-dependent con funzioni di costo personalizzabili
- Gestire correttamente la dinamica del tempo discreto
- Risolvere il problema anche in presenza di cicli e assenza della proprietà FIFO
- Verificare l’output in termini di correttezza del percorso e arrivo ottimale
## Passi per arrivare alla soluzione
Sono stati necessari più iterazione per ottenere il risultato atteso, le principali fasi sono state le seguenti:
### Definizione informale del problema e richiesta di un algoritmo risolutivo
Nella fase iniziale ci siamo limitati a dare una definizione informale del problema e la richiesta di fornire un algoritmo in grado di risolverlo.
Inizialmente il chatbot ha proposto la risoluzione attraverso una versione modificata dell'algoritmo di Dijkstra o di A*, ponendomi ulteriori domande per chiarire il problema, senza però fornire il codice, dando solo delle indicazioni generali su come poter implementare la soluzione. 
### Risposta ai quesiti e richiesta di implementazione
Una volta ricevuta la risposta alle domande il chatbot ha proposto una soluzione del problema basandosi su l'algoritmo di Dijkstra.
La soluzione proposta non risulta idonea per vari problemi, tra cui il fatto che sottostà alla proprietà FIFO e il fatto che non tiene in considerazione la possibile presenza di cicli a costo negativo all'interno del grafo.
### Richiesta di non rispettare la proprietà FIFO
Alla nostra richiesta di non rispettare la proprietà FIFO come da definizione del problema, il chatbot ha fornito una versione aggiornata dell'algoritmo, mantenendosi su una soluzione basata su Dijkstra, in che non va a risolvere il problema relativo ai cicli di costo negativo.
### Richiesta di sviluppare una soluzione non basata su Dijkstra
Una volta chiarito il fatto che un algoritmo basato su Dijkstra non può coprire eventuali problemi di cicli a costo negativo, il chatbot ci ha fornito un nuovo algoritmo basato su Bellman-Ford.
L'esempio fornito in maniera automatica però si è rivelato non corretto in quanto non riusciva a individuare una soluzione in quanto il grafo era strutturato in maniera non corretta, dopo due iterazioni il problema è stato risolto fornendo un esempio funzionante e corretto.
### Pulizia del codice e spiegazione
Nell'ultima fase abbiamo richiesto una pulizia del codice in quanto quello che era stato generato precedentemente non risultava chiaro, abbiamo inoltre chiesto anche una spiegazione passo passo dell'algoritmo proposto che è risultata molto accurata e d'aiuto.
## Algoritmo proposto per la soluzione (Bellman-Ford)
``` python
import math

# Funzioni di costo temporale
def f01(t): return 2
def f12(t): return 1 + (t % 3 == 0) * 0.1 + (t % 3 != 0) * 2
def f23(t): return 1 + (t % 4 == 0) * 0.1 + (t % 4 != 0) * 2
def f31(t): return 1 + (t % 5 == 0) * 0.1 + (t % 5 != 0) * 2
def f34(t): return 2
def f45(t): return 2
def f05(t): return 20

graph = {
    0: [(1, f01), (5, f05)],
    1: [(2, f12)],
    2: [(3, f23)],
    3: [(1, f31), (4, f34)],
    4: [(5, f45)],
    5: []
}


def get_min_arrival(goal, distance):
    """Trova il tempo e il costo minimo per raggiungere il nodo goal"""
    arrivals = [(time, cost) for (node, time), cost in distance.items()
                if node == goal and cost < float('inf')]
    if not arrivals:
        return None
    return min(arrivals, key=lambda x: x[1])  # ritorna (tempo, costo)


def bellman_ford_time_dependent(graph, start, goal, max_time=50):
    distance = {(node, time): float('inf') for node in graph for time in range(max_time + 1)}
    distance[(start, 0)] = 0
    previous = {}

    for _ in range(len(graph) * max_time):
        updated = False
        for current_node in graph:
            for current_time in range(max_time):
                current_cost = distance[(current_node, current_time)]
                if current_cost == float('inf'):
                    continue

                for neighbor, cost_func in graph[current_node]:
                    cost = int(math.ceil(cost_func(current_time)))
                    arrival_time = current_time + cost

                    if arrival_time > max_time:
                        continue

                    if arrival_time < current_time:
                        raise ValueError("Violazione del tempo causale: arrivo prima di partire")

                    new_cost = current_cost + cost
                    if distance[(neighbor, arrival_time)] > new_cost:
                        distance[(neighbor, arrival_time)] = new_cost
                        previous[(neighbor, arrival_time)] = (current_node, current_time)
                        updated = True

        if not updated:
            break
    else:
        raise ValueError("Ciclo negativo rilevato")

    result = get_min_arrival(goal, distance)
    if result is None:
        print("⚠️ Nessun cammino trovato")
        return float('inf')

    best_time, best_cost = result
    print(f"✅ Arrivo al nodo {goal} al tempo {best_time}, costo: {best_cost}")

    # Ricostruzione del cammino
    path = []
    current = (goal, best_time)
    while current in previous:
        path.append(current)
        current = previous[current]
    path.append((start, 0))
    path.reverse()

    print("📍 Cammino percorso:")
    for node, time in path:
        print(f"  - Nodo {node} al tempo {time}")

    return best_cost
```
### Prove successive
Abbiamo richiesto ulteriori versioni modificate dell'algoritmo, inizialmente le soluzioni proposte erano nuovamente basate sul Dijkstra, anche se già precedentemente richiesto di non utilizzarlo.
Dopo ulteriori scambi ci è stata proposta una versione basata su A*, la riportiamo di seguito.
## Algoritmo proposto per la soluzione (Bellman-Ford)
```python
import math
from heapq import heappush, heappop

def time_expanded_a_star(graph, start, goal, max_time=50):
    def heuristic(node):
        return 0  # Euristica ammissibile

    open_set = []
    g_score = {}
    came_from = {}

    heappush(open_set, (0, 0, start, 0))
    g_score[(start, 0)] = 0

    while open_set:
        _, curr_g, u, t = heappop(open_set)
        for v, cost_func in graph.get(u, []):
            cost = int(math.ceil(cost_func(t)))
            arrival_time = t + cost
            if arrival_time > max_time:
                continue
            tentative_g = curr_g + cost
            state = (v, arrival_time)
            if state not in g_score or tentative_g < g_score[state]:
                g_score[state] = tentative_g
                priority = tentative_g + heuristic(v)
                heappush(open_set, (priority, tentative_g, v, arrival_time))
                came_from[state] = (u, t)

    candidates = [(t, g_score[(goal, t)]) for (n, t) in g_score if n == goal]
    if not candidates:
        return float('inf'), []

    best_time, best_cost = min(candidates, key=lambda x: x[1])
    path = []
    current = (goal, best_time)
    while current in came_from:
        path.append(current)
        current = came_from[current]
    path.append((start, 0))
    path.reverse()
    return best_cost, path
```
## Confronto Algoritmi forniti
Le soluzioni fornite sono entrambe corrette per il problema in questione, si può però dire che A* è meglio di Bellman-Ford nei problemi **metrici** (cioè con una nozione di distanza e euristiche ammissibili) per i seguenti motivi:
- **Efficienza:** A* esplora molti meno nodi grazie all’euristica che guida la ricerca verso la destinazione, mentre Bellman-Ford esplora sistematicamente tutti i percorsi.
- **Ottimalità garantita:** A* trova sempre il percorso minimo se l’euristica è ammissibile e consistente.
- **Più adatto a spazi metrici:** In ambienti spaziali (mappe, griglie), A* sfrutta l'informazione geometrica (come la distanza euclidea) per guidare la ricerca in modo intelligente, cosa che Bellman-Ford non fa.
Di conseguenza la seconda soluzione fornita risulta essere più performante sul problema specifico.
## Considerazioni
Abbiamo trovato l'utilizzo di un chatbot durante la fase di fast prototyping molto utile, in quanto va a velocizzare di molto il processo di prima implementazione dell'algoritmo.
Abbiamo però riscontrato varie criticità nell'utilizzarlo a causa delle soluzioni fornite, che senza la nostra supervisione, si sarebbero rivelate errate.
Si è notato che il modello AI molto spesso cerca di aggirare il problema piuttosto che affrontarlo direttamente, ha più volte proposto delle soluzioni basate su Dijkstra pur non essendo l'algoritmo corretto, fino a che non glielo abbiamo specificato direttamente, inoltre, in chat precedenti, ci è più volte capitato che anche con una definizione formale del problema in input, il modello abbia divagato fornendo soluzioni che non soddisfacevano vincoli.
Di conseguenza l'utilizzo di modelli AI può essere molto utile se utilizzati come strumento a supporto e verificandone accuratamente le risposte.  