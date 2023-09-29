# Decision Tree

## come funziona
L'idea dietro al decision tree (albero delle decisioni) consiste nel classificare 

###### capitolo 4.3 del libro
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