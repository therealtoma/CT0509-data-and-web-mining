# ensemble methods
sono delle tecniche che consistono nel combinare modelli singoli per incrementare le performance del modello.
- **bagging**: permette di ridurre la **varianza**
- **boosting**: permette di ridurre il **bias**
- **stacking**: permette di migliorare le **predizioni**

è possibile crere un modello attraverso combinando diversi modelli più **deboli**, o combinando modelli già più **forti**.

#### averaging
è una tecnica dove ogni metodo contribuisce ugualmente alla predizione finale, questo risulta utile nel momento in cui i metodi hanno performance simili.
Nel caso della **regressione** la predizione consiste nella **media** delle predizioni che compongono il modello.

#### weighted averaging
il contributo che ogni modello ha sulla predizione finale è pesato sulle **performance**. Il peso consiste in una serie di valori positivi che sommati fanno $1$.