# 4.3 Decision Tree
### come funziona
L'idea dietro al decision tree (albero delle decisioni) consiste nel classificare gli elementi in **due categorie**.
Vengono poste una serie di domande riguardo le proprietà del record che si intende testare, continuando ricorsivamente a porre *follow-up questions* fino a quando non si riceve una conclusione (**label**)
L'albero delle decisione è un albero con 3 tipi di nodi:
- **nodo radice**: non ha genitori e ha zero o più figli
- **nodo interno**: ha solamente un genitore e almeno due figli
- **nodo foglia**: na solamente un genitore e nessun figlio

Il **nodo foglia** rappresenta la label assegnata al record, gli altri nodi contengono le condizioni di test per arrivate alle foglie.

### come costruire un decision tree

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

### come scegliere il miglior split
Lo split migliore (nel caso degli alberi induttivi) è lo split che **massimizza** il **gain** rappresentato come la differenza di errore tra il nodo padre i figli; essendo il padre sempre fisso, si tratta semplimente di trovare il figlio che minimizza l'errore.

### gain
Rappresenta la bontà di uno split, indicato come la differenza tra l'errore del nodo padre e la somma pesata degli errori dei figli.

### algoritmo d'esempio
Consideriamo ora un esempio di un algoritmo per la costruzione di un albero di decisione:
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
Spieghiamo ora il funzionamento dell'algoritmo:
- `BestSplit` e `BestGain` inizialmente sono impostati a `None`
`BestSplit` memorizza l'attuale condizione di split (basata su una feature e una soglia), `BestGain` è il guadagno di informazione massimo fino ad ora
- L'algoritmo scorre tutte le feature e le soglie possibili (ha senso considerare solamente le soglie presenti all'interno del dataset)
- Nel caso in cui il gain ottenuto è maggiore o uguale di quello precedente, vengono aggiornati `BestGain` e `BestSplit` con quelli attuali
- Se `BestGain` è zero oppure viene soddisfatto un altro criterio di arresto l'algoritmo termina ritornando la foglia con la migliore predizione
- Se non sono raggiunti criteri di arresto, l'algoritmo crea uno split basandosi su `BestSplit` dove una condizione è vera (l_1) e l'altra è falsa (l_2)
- Chiamata ricorsiva sui due sottoalberi