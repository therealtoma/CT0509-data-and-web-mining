# ensemble methods
è una tecnica di machine learning che consiste nel combinare i risultati ottenuti da diversi modelli, con l'obiettivo di migliorare l'accuratezza della previsione.
**bagging** e **boosting** rappresentano due diverse tecniche di ensembled learning.

#### bagging
viene solitamente indicato come **bootstrap aggregating**, è una tecnica di ensembled learning. Questa tecnica **riduce** la **varianza**, non è sensibile all'overfitting ed è usato sia per problemi di regressione che di classificazione, molto usato all'interno degli alberi di decisione.

**come applicare bagging**
- dato un dataset con $n$ osservazioni e $m$ features. Bisogna selezionare un sottoinsieme a caso dal training set senza ripetizione
- ora ho un dataset preso dal set iniziale tramite il quale sono in grado di creare un modello
- la feature che genera il miglior split viene usata per creare l'albero di decisione
- una volta che l'albero è cresciuto ho ottnenuto il miglior *full grown tree*
- ripeto questi passaggi diverse volte, aggregando i risultati dei diversi alberi di decisione in modo da ottenere la migliore predizione

**vantaggi del bagging**
- minimizza l'overfitting dei dati
- migliora la precisione del modello
- lavorare con dataset di grandi dimensioni risulta efficiente

#### boosting
l'idea di base è quella di combinare una serie di modelli più **deboli** per poterne creare uno più **robusto**

**come applicare il boosting**
- ad ogni sample viene assegnato lo stesso peso
- questo set viene passato al primo modello che si occupa di fare le predizioni
- l'algoritmo di boosting valuta quindi le predizioni e aumenta il peso in caso di maggior errore e lo diminuisce in caso di minor peso
- viene passato il risultato ad un altro modello che ripeterà il passaggio
- ripetuti iterativamente i passaggi 2 e 3 fino a quando l'errore non scende al di sotto di una soglia indicata

**vantaggi del boosting**
- è in grado di lavorare in modo efficiente con dataset di grandi dimensioni
- continua a mantenere l'accuratezza nonostante ci siano dati mancanti

#### differenze
Mentra l'algoritmo di **bagging** seleziona casualmente i sotto-dataset, l'algoritmo di **boosting** si concentra sui dati che nel ciclo precedente hanno ottenuto un peso maggiore.
L'algoritmo di **bagging** non è sensibile all'overfitting, l'algoritmo di **boosting** minimizza il bias.
**bagging** minimizza la varianza, mentre **boosting** minimizza il bias
nel **bagging** ogni modello ha lo stesso peso, nel **boosting** è assegnato un peso in base alle performance