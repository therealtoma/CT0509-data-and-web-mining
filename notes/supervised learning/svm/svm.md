# SVM
è l'acronimo di Support Vector Machine

#### perchè svm
è un metodo di machine learning che si occupa di dividere i dati in due categorie.
Vengono presi i dati, e viene tracciata una linea che li divide nelle due categorie; quando voglio predirre un elemento, guardo dove cade e decido in base alla sua posizione rispetto alla linea

La linea di separazione deve essere tale da **massimizzare** la distanza tra i punti più vicini delle due categorie, in modo da riuscire a separare meglio i dati.
In termini tecnici, vogliamo che la distanza tra il **support vector** e l'**iperpiano** sia la maggiore possibile.
- **support vector**: i punti più estremi del dataset
- **iperpiano**: ha la maggiore distanza possibile dai support vectors; il motivo per cui viene chiamato iperpiano è perchè quando si lavora con più di due dimensioni, non è più una linea ma un piano

Trovare l'iperpiano nel caso in cui i dati, plottandoli, mostrano una chiara separazione è facile; se invece si è nella situazione in cui una categoria si trova in mezzo all'altra?
In questo caso bisogna spostarsi da una dimensione a quella successiva. Viene fatto uso del **kernel**: funzione che si occupa di convertire i dati da una dimensione ad un'altra, in modo da poterli separare.

#### vantaggi di svm
- dati su più dimensioni: mentre, lavorando con molte dimensioni, alcuni algorimi possono non essere adatti, svm si adatta facilmente
- lambda: è un parametro che indica se avremo un bias di dati o un overfitting