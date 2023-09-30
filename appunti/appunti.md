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

