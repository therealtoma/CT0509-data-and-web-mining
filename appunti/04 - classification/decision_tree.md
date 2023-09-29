# Decision Tree
###### capitolo 4.3 del libro

### come funziona
L'idea dietro al decision tree (albero delle decisioni) consiste nel classificare gli elementi in **due categorie**.
Vengono poste una serie di domande riguardo le proprietà del record che si intende testare, continuando ricorsivamente a porre *follow-up questions* fino a quando non si riceve una conclusione (**label**)
L'albero delle decisione è un albero con 3 tipi di nodi:
- **nodo radice**: non ha genitori e ha zero o più figli
- **nodo interno**: ha solamente un genitore e almeno due figli
- **nodo foglia**: na solamente un genitore e nessun figlio

Il **nodo foglia** rappresenta la label assegnata al record, gli altri nodi contengono le condizioni di test per arrivate alle foglie.

### come costruire un decision tree

La costruzione del decision tree *perfetto* è computazionalmente impossibile a causa delle troppe combinazioni possibili.
Sono stati pensati degli algoritmi **greedy** per la creazione di alberi di decisione.

### problemi implementativi di decision tree induction
Un algoritmo che crea un albero di decisione in modo **induttivo** deve affrontare i seguenti problemi:
1. **come divido i record in modo induttivo?** ogni passaggio ricorsivo deve selezionare un **predicato** sul quale sul quale dividere il test-set in sottoinsiemi più piccoli. Questo implica che l'algoritmo deve fornire un modo per valutare la bontà di un predicato e un modo per trovare il predicato.
2. **quando dovrebbe fermarsi lo split?** è nessario trovare un modo per capire il punto di stop. Diverse sono le possibili strategie:
   - terminare quando tutti i record hanno la stessa classe
   - terminare quando tutti i record hanno la stessa feature
a questo si possono implementare altri controlli per far terminare prima l'algoritmo.

### metodi per esprimiere i predicati
Questi algoritmi devono sapere come come creare un predicato e la relativa risposta per i vari tipi degli attributi.
- **attributi binari**: forniscono due tipi di risultati (vero o falso)
- **attributi nominali**: possono essere divisi in due, tre o più sottocategorie (es. stato coniugale = {sposato, single, divorziato})
- **attributi ordinali**: simili agli attributi nominali, ma deve essere rispettato un ordine (raggruppare la dimensione di una maglietta in {small, medium}, {large, extra large} è lecito, {small, large} e {medium, extra large} non è lecito)
- **attributi continui**: per gli attributi continui la condizione può essere espressa come un test di confronto ($A \le v$) e si riceve un risultato binario (vero o falso)













Prendiamo come esempio la seguente immagine che rappresenta un dataset due features e una serie di istanze.
Il plot risulta:
![immagine](../assets/4-quadrants.png)


```python
BestSplit, BestGain = None
for f in features:
    for t in thresholds:
        Gain = godness of the split (f <= t)
        if Gain >= BestGain:
            BestGain = Gain
            BestSplit = (f <= t)
        if BestGain == 0 or other stopping criterion is met:
            mu = best prediction for D
            return Leaf(mu)
        f, t = those of BestSplit = (f <= t)
        d_l = {x in D | x_f <= t} # left partition
        L = BuildTree(d_l) # left child
        d_r = {x in D | x_f > t} # right partition
        R = BuildTree(d_r) # right child
        return Node(L, R)
```
Vogliamo creare un modello per questo dataset.

Una soluzione molto mecacnica consiste nel
1. Se $F_1 \le 0.5$ e $F_2 \le 0.5$ allora $label = rosa$
2. Se $F_1 \le 0.5$ e $F_2 \ge 0.5$ allora $label = giallo$
3. Se $F_1 \ge 0.5$ e $F_2 \le 0.5$ allora $label = giallo$
4. Se $F_1 \ge 0.5$ e $F_2 \ge 0.5$ allora $label = rosa$

Un modo migliore per trovare un modello consiste nell'individuare l'**albero di decisione**, dove i *nodi* sono i **predicati** dell'albero e le *foglie* sono le **label**.

## processo di training
La serie di passaggi per passare dal grafico all'albero di decisione è detto **processo di training**

---

Attraverso un algoritmo *greedy* (maniera incrementale) siam in grado di costruire un albero di decisione. Le tipologie di alberi che vedremo saranno principalmente *binari*
### convenzione
vogliamo trovarci nella situazione dove, all'interno di un predicato la condizione è $feature \le soglia$.

## come faccio a costruire un predicato?
$$
? \le \ ?
$$

Questo oggetto è chiamato **split** e l'obiettivo è dividere il dataset in due parti.

Viene combinata ogni feature con ogni soglia possibile (considerate solamente le soglie presenti all'interno del dataset)

## come scelgo il miglior split?
Viene preso lo split che ha il **gain** minore (vedere script inizio capitolo).