# Supervised Learning
Il supervised learning è un tipo di apprendimento nel quale il modello viene allenato su un dataset etichettato, in altre parole, ad ogni esempio nel set è associata una **label** o risultato.
L'obiettivo di questo tipo di apprendimento è fare in modo che il modello sappia come mappare le caratteristiche in input con delle etichette in output.
Una volta che il modello viene addestrato, è possibile utilizzarlo per fare delle predizioni su dati che non sono stati etichettati.

# K-Nearest Neighbors Classifiers
è un modello che si basa sul concetto di **vicinanza**. Dato un punto, il modello cerca i k punti più vicini e restituisce la label più frequente tra i k punti.

## come scegliere il k più adattto
- se $k$ è piccolo, risulterà sensibile agli errori (rumore)
- se $k$ è grande, sarà sicuramente più efficace, ma può risultare computazionalmente molto costoso

Spesso, per aumentare l'accuratezza del modello, risulta utile **normalizzare** i dati, ovvero portare i dati in un range di valori che va da 0 a 1.
La normalizzazione può essere fatta in due modi:
- **min-max normalization**: risulta più sensibile agli outliers ma è in grado di normalizzare i dati in maniera più accurata
- **normalizzazione standard**: non standardizza ogni feature, dipende dalla varianza. Una feature con una varianza molto alta avrà un peso maggiore rispetto ad una con varianza bassa.

La distanza euclidea (teorema di pitagora) assume che tutti le feature hanno la stessa importanza, cosa che non è quasi mai vera.

