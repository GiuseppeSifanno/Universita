## Sconfinamento con array
Succede quando l'array viene indicizzato con un indice al di fuori del suo range ammesso. È possibile che succeda uno dei seguenti casi:
- Nel migliore si ha un errore di **segmentation fault** (errore che si verifica durante l'esecuzione di un programma quando tale ultimo tenta di accedere ad una posizione di memoria alla quale non è permesso accedervi, oppure quando tenta di accedervi in una maniera non concessa)
- Più spesso si va a scrivere/leggere una variabile che appartiene al programma allocata subito dopo al vettore, non si può conoscere a priori quale sia ed è un comportamento errato e molto pericoloso del programma, difficile pure da diagnosticare

In C non è presente alcun controllo di sconfinamento, si rischia di andare a scrivere oltre i limiti
### Array multi dimensionali
Tutti i linguaggi consentono di dichiarare array con più indici (**array di array**), un caso tipico è quello di vettori a due dimensioni, ovvero le matrici o tabelle
### Matrici
Una **matrice** o array bidimensionale è un insieme di valori che sono indicizzati facendo ricorso a due o più indici, la notazione usata per loro è **M\[i , j]** (per una matrice a due dimensioni i è detto indice riga e j indice colonna)
#### Criterio di linearizzazione
La linearizzazione di un array n-dimensionale consiste nel trasformare un array multidimensionale in un array monodimensionale. Questo è utile per memorizzare i dati in strutture di memoria lineari come la RAM.
### Rappresentazione di un array bidimensionale
**MAT\[N]\[M]**
Ogni elemento di un array occupa una locazione di memoria ed è rappresentato in una zona di memoria contigua, cioè composta da locazioni di indirizzi consecutivi.
Gli elementi di un array vengono memorizzati per righe a partire da una certa locazione di memoria iniziale e seguendo, nell'ambito della stessa riga, l'ordine dato dall'indice colonna 
- Nelle prime M locazioni di memoria sono destinati gli elementi della prima riga, le seconde M locazioni di memoria alla seconda riga e così via fino alla N-esima colonna
Il numero di locazioni necessarie per la memorizzazione di un array a due dimensioni con indici \[1...N] e \[1...M] è pari a $N\cdot M$

