Un programma e i suoi dati al fine di essere eseguiti (o run) devono essere, almeno parzialmente, presenti in memoria centrale
Il gestore della memoria (che è il sistema operativo):
- Si occupa di allocare memoria fisica ai processi
- Garantisce la protezione dei dati dei processi, il processo deve sapere quanta memoria gli è allocata e non permettere di sconfinare nello spazio di indirizzamento di altri processi
- Garantisce meccanismi di condivisione, in modo che i processi possano condividere dati tramite aree comuni di memoria

L'utilizzo globale delle risorse e le prestazioni di un calcolatore vengono influenzate dalle prestazioni del modulo di gestione della memoria sia in funzione della sua efficienza nell'allocare memoria, sia per l'influenza che può avere sullo scheduler
## Introduzione
La CPU preleva le istruzioni dalla memoria centrale sulla base del contenuto del Process Counter
Il programma prima di essere eseguito attraversa diversi stadi (alcuni opzionali):
- Programma sorgente con indirizzi **simbolici** (esempio: variabile x)
- Compilazione, dal programma sorgente avviene la generazione di un modulo compilato con indirizzi **rilocabili**, (esempio: +14 bytes dall'inizio)
- Caricatore (loader): L'**editor dei collegamenti** (linker) combina diversi moduli compilati, risolvendo riferimenti tra di essi, e il **loader** assegna gli **indirizzi assoluti** quando il programma viene caricato in memoria, determinando le posizioni fisiche effettive. (esempio: 74000+14= 74014)

La generazione di indirizzi di memoria (assoluti) avviene per ogni categoria a tempo di:
- **Compilazione**: Si genera codice assoluto che deve risiedere in memoria, presenta gli indirizzi quindi logici relativi allo spazio di indirizzamento logico del programma, un area immaginabile nella RAM.
- **Caricamento**: Se non è noto dove un programma deve risiedere in memoria viene rigenerato codice rilocabile, durante questa fase poi diventano indirizzi assoluti.
- **Esecuzione**: Se durante l'esecuzione il processo può essere spostato da un segmento di memoria ad un altro l'associazione degli indirizzi viene ritardata fino alla fase di esecuzione, permettendo una maggiore flessibilità nell'uso della memoria

L'indirizzo logico è un indirizzo generato dalla CPU
L'indirizzo fisico è l'indirizzo visto dall'unità di memoria, cioè caricato nel registro dell'indirizzo di memoria(Memory Address Register, MAR)

L’associazione nella fase d’esecuzione dagli indirizzi virtuali agli indirizzi fisici è svolta da un
dispositivo detto unità di gestione della memoria 
![[Pasted image 20241218194834.png]]
## Allocazione di memoria
I moduli di gestione della memoria si differenziano in base al tipo di allocazione della stessa, che può essere:
- **Contigua**
- **Non contigua**

Nell'allocazione contigua la memoria viene allocata in modo tale che ciascun oggetto occupa un insieme di locazioni i cui indirizzi sono strettamente consecutivi.
Esistono vari tipi di allocazione contigua
- **Mono allocazione**
- **Partizionamento statico**
- **Partizionamento dinamico**
- **Segmentazione**
### Mono allocazione (Monitor Mono processo)
La memoria viene suddivisa in **due aree contigue**:
- La prima viene allocata permanentemente ad una porzione residente del sistema operativo (**monitor**)
- La seconda assegnata ai processi in esecuzione, processi utente o porzioni non residenti del sistema operativo, per il tempo necessario al completamento.
![[Pasted image 20241219174957.png]]
Il sistema operativo:
- Tiene traccia della prima e dell'ultima locazione disponibile per i **processi transienti**
- Viene posto ad uno dei due estremi della memoria
- Ingloba i vettori dell'interrupt

Questo schema di allocazione viene generalmente utilizzato dai sistemi operativi mono-processo per microcomputer.
Alla richiesta di esecuzione di un programma il sistema operativo:
- Si assicura che le dimensioni del processo siano compatibili con la memoria disponibile;
- Conferisce il controllo al processo utente fino al suo completamento o ad eventuali condizioni di errore
- Al termine del processo la memoria viene liberata e può essere assegnata ad un altro processo in attesa

Raramente un monitor mono processo supporta meccanismi di protezione tra processi utente in quanto in ogni istante vi può essere al **massimo un solo processo residente in memoria**. Gli eventuali meccanismi si riferiscono alla protezione del codice del sistema operativo da eventuali sconfinamenti del processo transiente in esecuzione.
#### Meccanismi di protezione
La protezione del sistema operativo dai processi utente è spesso effettuata mediante **supporti hardware** come:
- **Registri barriera**: usati per tracciare un confine tra le aree di processi di sistema e dei processi transienti. Nel registro viene memorizzata la prima locazione disponibile al processo e il sistema operativo effettua i controlli di sconfinamento. 
- **Diritti di accesso mediante bit di protezione**: Ad ogni parola di memoria viene associato un bit di protezione (1 nelle zone che contengono il sistema operativo, 0 nelle restanti)
- Sistema operativo in memoria a sola lettura

La **condivisione del codice e dei dati** non ha molto senso in questi ambienti mono processo e viene raramente supportata, tuttavia programmi utente possono condividere dati tramite accordi interni, ponendoli in locazioni di memoria che non vengono sovrascritte durante l'esecuzione di processi partecipanti
#### Prestazioni
La mono allocazione presenta diversi difetti prestazionali:
- **Non presenta la multi-programmazione**, abbassando l'efficienza della memoria e della CPU (occupati da un unico processo alla volta)
- **La memoria può risultare sovradimensionata per la maggioranza dei processi**
- Processi di dimensione più grande della memoria non possono essere eseguiti o richiedono particolari suddivisioni del codice (overlay)
- I programmi tengono ad essere ottimizzati rispetto alla dimensione della memoria, comportando spesso sacrifici di funzionalità e velocità

Come pregi però presenta:
- **Basso costo di progettazione** del modulo di gestione della memoria
- Contenuti supporti hardware specifici per la memoria

La mono allocazione è principalmente utilizzata per micro-computer dedicati permanentemente a specifiche applicazioni.
### Partizionamento statico
[da finire]

