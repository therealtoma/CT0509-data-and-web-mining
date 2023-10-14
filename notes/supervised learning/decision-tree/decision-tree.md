# decision tree
[yt video](https://youtu.be/RmajweUFKvM?list=PL4IKJngDfheTNv9yoDTxy_PKaWXPOemAi)

#### cos'è un decision tree?
è un diagramma che usato per determinare una decisione. Ogni **ramo** rappresenta una possibile **decisione**, le **foglie** rappresentano le **predizioni**

#### che tipo di problemi possono essere risolit?
gli alberi di decisione possono essere usati sia per i problemi di **classificazione** che per i problemi di **regressione**:
- **classificazione**: l'albero usa una serie di condizioni *if-then* per classificare il problema.
- **regressione**: è usato quando si vuole predirre una variabile continua. Viene fatto il fit di un modello di regressione per ogni foglia dell'albero; ogni split (divisione) viene fatta in base alla somma dei quadrati degli errori (SSE).

#### vantaggi del decision tree
- è semplice da capire, interpretare e mostarare
- non c'è bisogno di effettuare grandi operazioni per preparare i dati
- è in grado di lavorare sia con dati categorici che dati numerici

#### svantaggi del decision tree
- c'è il rischio di **overfitting**: l'algoritmo cattura anche il rumore
- il modello può non essere preciso a causa della bassa varianza tra i dati
- un albero di decisioni molto complicatopuò avere un bias basso, rendendo difficile al modello lavorare co dati nuovi

#### termini importanti
- **entropia**: rappresenta una misura della randomicità o non predicibilità all'interno del dataset (la root avrà un'entropia maggiore delle foglie) $\sum_{i=1}^k P(value_i) \cdot log_2(P(value_i))$
- **information gain**: valore che indica la diminuzione in entropia dopo uno split
- **foglia**: sono i nodi che contengono la predizione (sia che sia classificazione che regressione)

#### come funziona un decision tree
il test set iniziale avrà un'entropia molto alta, l'obiettvo è quello di dividerlo in modo da massimizzare il gain.
Dopo ogni split viene ricalcolata l'entropia per poter trovare il gain.
Lo split che produce il gain maggiora è quello che viene scelto.
Si continua a dividere il dataset fino a quando non si raggiunge un'entropia pari a 0.