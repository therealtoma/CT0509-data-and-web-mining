# Supervised Learning
Il **supervised learning** è un tipo di apprendimento nel quale il modello viene allenato su un dataset etichettato, in altre parole, ad ogni esempio nel set è associata una **label** o risultato.
L'obiettivo di questo tipo di apprendimento è fare in modo che il modello sappia come mappare le caratteristiche in input con delle etichette in output.
Una volta che il modello viene addestrato, è possibile utilizzarlo per fare delle predizioni su dati che non sono stati etichettati.

## K-Nearest Neighbors Classifiers
Il classificatore **KNN** è un metodo di classificazione semplice, utilizzato sia per la classificazione che per la regressione.
#### classificazione
- dato un punto in input, knn trova nel dataset i $k$ punti più vicini all'input in termini di distanza (distanza Euclidea(Pitagora), Manhattan, ...)
- controlla le etichette dei $k$ punti trovati
- assegna la label che ricorre più frequentemente tra i $k$ punti trovati
#### regressione
- dato un punto in input, knn trova nel dataset i $k$ punti più vicini
- calcola la media delle etichette dei $k$ punti trovati
- assegna la media come etichetta di output
#### vantaggi
- *semplicità*: il knn è intuitivo e facile da implementare
- *non parametrico*: non fa assunzioni riguardo alla distribuzione dei dati
- *adatto al multi-case*: può essere utilizzato per problemi di classificazione con più di due classi
#### svantaggi
- *costo computazionale*: dato che deve calcolare la distanza tra il punto in input e ogni punto del set, può risultare computazionalmente costoso, specie per grandi set di dati
- *sensibile a caratteristiche irrilevanti*: se il dataset contiene caratteristiche irrilevanti, queste possono influenzare negativamente il risultato finale
- *sensibile agli outliers*: gli outliers possono avere un impatto negativo sulle prestazioni

#### ottimizzazione delle prestazioni
- **scelta del k**: è fondamentale scegliere un valore di $k$ ottimale, infatti, se è troppo piccolo il modello risulta sensibile al rumore, se è troppo grande potrebbe essere computazionalmente costoso
- **ponderazione**: i punti più vicini all'input hanno maggiore importanza rispetto a quelli più distanti
