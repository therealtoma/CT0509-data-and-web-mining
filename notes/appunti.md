# Creare il primo modello

# machine learning
#### in cosa consiste il machine learning?
è un'applicazione dell'informatica che ha l'abilità di **imparare** e **migliorare** in base all'esperienza ottenuta.

#### tipi di machine learning
- **supervised leaning**: si è già in possesso dei dati e delle risposte 
- **unsupervised learning**: abbiamo i dati ma non conosciamo le risposte
- **reinforcement learning**: non hai i dati prima di iniziare e, in base alle risposte che il modello fornisce, riceve un punteggio positivo o negativo in base all'accuratezza della risposta.

#### problemi nel machine learning
- **classificazionie**: problemi con soluzioni categoriche ("si" o "no", "vero" o "falso", ...)
- **regressione**: il risultato da predirre è continuo ("prezzi", "profitto", ...)
- **clustering**: problemi dove i dati devono essere organizzati in gruppi per ricercare specifici pattern

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

# ricapitoliamo (02/10/2023)
domande fast per ricapitolare, non provengono dal testo d'esame
## KNN Classifier
- cosa succede se k tende a infinito?
  - viene preso l'intero dataset
- cosa fa il classificatore al tempo di training?
  - memorizza il training set (possibilmente indicizzandolo)
- che impatto ha la scala delle faatures?
  - il calcolo della disrtanza è dominato dalla features con range [min-max] maggionre

## binary decision tree
- che impatto ha la scala (min-max) delle features
  - nessun
- perche binary?
  - un nodo puo avere solo 2 figli
- quante features possono essere conivolte nel predicato di un nodo
  - dipende da ...
- qual è la profondita massima
  - corrisponde al numero di istanze
-