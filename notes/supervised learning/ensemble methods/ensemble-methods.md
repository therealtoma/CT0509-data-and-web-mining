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