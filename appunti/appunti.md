# Creare il primo modello

## training set
Durante la durata del corso verranno utilizzati dataset a forma di **matrice** (banalmente dei file csv) composti come segue:
- le *righe* rappresentano le **istanze** 
- le *colonne* sono le **features** (proprietà) del nostro dataset

Capita che, di tutto il dataset, una colonna è quella che ci interessa trovare, essa è chiamata **label**.

- nel caso in cui la label sia discreta, si parla di **classificazione**
- nel caso in cui la label sia continua, si parla di **regressione**

## training process
è il processo tramite il quale viene letto il dataset e viene creato il modello.

## modello
un modello è un oggetto che prende in input un'istanza e restituisce un'etichetta (label) che è la previsione del modello.

$$
f(x_j) = predizione
$$

Per capire se un modello è buono ne viene calcolata la **precisione** (accuracy) nel caso *discreto* e la **scarto quadratico medio** (o rooted mean square error) nel caso *continuo*.

- precisione: indica la percentuale di istanze che sono state trovate correttamente
- scarto quadratico medio: usato per calcolare la distanza tra due punti (minore la distanza maggiore la precisione)

## test set
Per poter verificare se il modello prodotto effettivamente funzione come ci si aspetta, viene utilizzato un dataset che non è stato utilizzato per la creazione del modello. Dato che non possiamo testare il modello su dati che non abbiamo (futuro), solitamete viene preso il dataset di partenza e diviso in due parti:
- 80% training set
- 20% test set

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