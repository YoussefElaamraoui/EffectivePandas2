## Chapter 5 : Types Python,Numpy, PyArrow and Pandas

In pratica python per ogni numero lui usa gli oggetti,questi oggetti poi avranno tipo float o integer, e tutti imetodi necessari ,non vanno in overflow dato che sono memorizzati con tanti byte, e quindi non ci sono problemi, se non per l’efficenza dato che con milioni di numeri ho spreco di spazio e di velocità 

Per quanto riguada invece il C, si memorizzano in 4byte in generale gli interi, questi quindi sono 32 bit, i quali possono andare in overflow se supero il valore di (2^32-1).

Per avere la stessa velocità in Python si usa la libreria Numpy, questa libreria porta dei concetti di C in python. Praticamente salva i valori in memorie contingenti, questo fa si che si hanno valori memorizzati vicini ed inoltre non crea un oggetto per ogni valore per crea un oggetto per l’intera ‘lista di valori’. 

Tuttavia dobbiamo dichiarare il numero di byte che vogliamo allocare e quindi anche il tipo della “lista”,ovvero il data type.
Con questa idea di “lista” inoltre possiamo usare il concetto di **Vectorization**, ovvero la possibilità di fare calcoli su vettori, cosa che le moderne CPU sanno fare molto bene e quindi ho un’ottima efficenza

```python
#Vectorization
array = np.arrange (10,dtype='int32')
array +1=
```

Questo è possibile alla SIMD (Single instruction multiple data) ovvero ho un valore in buffer che viene usato per fare più operazioni.

Numpy cosi rende da Python obsoleto, seppure semplice da imparare, a semplice da imparare e veloce nel fare i calcoli, per questo Python è talmente famoso e usato, grazie alle sue libbrerie e delle sue proprietà intrinsiche.

Tuttavia, esistono anche aspetti negativi, ha portato concetti di C vero, questo significa anche che questi valori se hanno un tipo hanno anche overflow come in C, per non parlare anche del fatto che se non ci sono dei valori segnati impliciti, viene riempito lo spazio con Nan ovvero not a number .

E da dire però che noi non useremo valori eterogenei, dato che si usano spesso stringhe interi etc negli spreadsheet, questo porta in gioco Pandas, che usa numpy per i valori numerici (si affida a numpy) però per il resto prende una sua strada.

Il futuro è però PyArrows, è diciamo la versione evoluta di Numpy per Pandas 2, gestisce valori mancanti, gestisce valori non eterogenei e gestisce anche meglio le stringhe, tuttavia è una libreria ancora acerba e avrà bisogno di tempo per essere migliorata e funzionare efficentemente

Quando PyArrows vede che si sta facendo un overflow, non si appresta ad usare gli oggetti(quindi a tornare a Python ‘ideologia’ come fa numpy) ma da direttamente un errore.

Quando prima avevo errori di mancanza di valori, numpy faceva si che la serie diventava subito un float, una serie di float (non significa che il codice è più lento però bisogna starci attento) PyArrows invece gestisce questo problema e lascia la serie int

Quando ci sono delle mancanze in Numpy trovi NAN, invece in PYArrows trovi direttamnete <NA> non cambia nulla per la maggior parte delle operazioni

### String Data

For strings, since they can have different values, meaning free form text, dates values that are stored as strings and more.

> We can not use the simple, dtype = ‘int8[pyarrow]’ nomenclature as we did for integers floats for strings, but instead we have to use pd.ArrowDtype(pyarrow.string()
> 

To simplify use an alias, like this

```python
import pyarrow as pa
import pandas as pd
string_pa = pd.ArrowDtype(pa.string())
#and then 
tf1 = pd.Series(text_form,dtype=string_pa)
```

### Categorical Data

is string data with low cardinality, meaning a column that holds a specific amount of number of different values, like the number of regions in Italy

pandas does a particular way of storing these series, it stores the unique values on an array and then has a second array which contain just stores values as integers that refer to the individual values, there is a crossover point for categorical data instead of using categorical data instead of strings, before the crossover point is better to use categorical data otherwise is more efficient to use strings 

## Dates and Times

Si hanno le stesse peculiarità illustrate fino ad ora, ovvero senza pyarrow sto usando pandas 1.X invece con pyArrow so usando Pandas 2.0