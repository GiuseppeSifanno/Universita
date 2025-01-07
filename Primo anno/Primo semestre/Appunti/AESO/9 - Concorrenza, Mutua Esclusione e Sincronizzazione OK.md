## Terminologia
Terminologia della lezione
- **Sezione critica**: insieme di istruzioni attraverso le quali si richiede l'accesso e si gestisce la risorsa condivisa
- **Deadlock** (semplice): situazione in cui **almeno** due o più processi sono impossibilitati dal procedere poiché sono in attesa l'uno dell'altro
- **Livelock** (stallo attivo): situazione in cui **almeno** due o più processi cambiano continuamente il proprio stato a causa del cambiamento di stato degli altri (senza fare alcun lavoro utile)
- **Race condition**: situazione dove i thread o processi leggono e scrivono un dato condiviso e il risultato dipende dalla loro velocità, il più veloce vince rispetto a quello più lento
- **Starvation**: situazione nella quale un processo non riceve mai l'utilizzo di una risorsa e viene costantemente scavalcato da altri processi
## Concorrenza
La concorrenza è la competizione tra processi (o threads) per ottenere (e condividere) le risorse come CPU, memoria, I/O, files etc.
Il problema della concorrenza nasce dall'implementazione e l'utilizzo di: 
- Multiprogrammazione (gestire più processi su un singolo processore)
- Multiprocessing (gestire più processi su più processori)
- Multi-Threading (a livello di pipeline)
### Problemi derivati dalla concorrenza
#### Sistemi a singolo processore
- La condivisione diventa pericolosa, poiché l'ordine delle operazioni di lettura e scrittura su aree di memoria condivise potrebbe portare a perdite di dati
- Esiste una difficoltà ad assegnare le risorse ai processi in maniera ottimale
- Diventa difficoltosa la rilevazione di errori nel codice e dei conflitti di interlacciamento (race-conditions)
Esempio:
![[Pasted image 20241228140816.png]]
#### Sistemi SMP
- Stessi problemi di un calcolatore a singolo processore
- Interlacciamento di esecuzione di processi paralleli:
	Quando processi paralleli operano contemporaneamente, possono verificarsi situazioni di **perdita di aggiornamenti**, in cui i dati letti o scritti vengono sovrascritti o perduti a causa della mancanza di coordinamento tra i processori. 
Esempio:
![[Pasted image 20241228141155.png]]
Il risultato finale dipende dalla velocità degli $n$ (in questo caso 2) processi, quello più veloce avrà la prevalsa
## Mutua esclusione
La soluzione ai problemi della concorrenza quindi è la mutua esclusione, un requisito (che noi programmatori richiediamo) per il quale, se un processo è nella propria sezione critica, nessun'altro processo può entrare nella propria sezione critica se questa fa riferimento a risorse condivise con il primo processo
### Requisiti per la mutua esclusione
Ci sono dei requisiti fondamentali per poter implementare e garantire la mutua esclusione:
1. Un solo processo alla volta deve accedere alla sezione (o risorsa) critica
2. Un processo fuori dalla sezione critica non deve interferire con il processo nella sezione critica (come la richiesta continua della sezione critica)
3. Ogni processo deve poter accedere dopo un tempo finito di attesa in coda alla risorsa critica (senza creare situazioni di stallo o starvation)
4. Se nessun processo è nella sezione critica, un processo deve poter entrare nella sezione critica senza tempi di attesa
5. Non ci devono essere ipotesi di velocità di esecuzione dei processi
6. Il tempo di permanenza nella sezione critica è finito e definito
	Un processo quando entra nella sezione critica, che abbia finito o no le sue operazioni importanti, deve rilasciare la risorsa allo scadere del tempo
### Meccanismi di Mutua esclusione
A questo soluzione è possibile applicare più algoritmi:
- **Approccio software**: soluzione totalmente a carico del programmatore che scrive un pezzo di codice per la coordinazione dei processi (Algoritmo di Dekker)
	Questo approccio ha come svantaggi:
	- Aumento dei tempi di esecuzione
	- Errori frequenti dati da un codice pensato o scritto male
- **Approccio hardware**: utilizzo di istruzioni macchina, tipicamente test-set o swap 
- **Supporto del sistema operativo**: il sistema operativo mette a disposizione dei costrutti specifici (monitor o semafori) che sono in grado di gestire la mutua esclusione

===Quali delle 3 uso? Sicuramente non quella software, superata da oramai tanto tempo (a meno di casi molto particolari) ===
#### Approccio software: Algoritmo di Dekker
L'algoritmo di Dekker è un metodo progettato per garantire la mutua esclusione tra due processi che devono accedere a una risorsa condivisa, è basato sull'uso di due variabili principali: 
- Una per indicare l'intenzione di ogni processo di accedere alla risorsa 
- Un'altra per stabilire quale processo ha la priorità in caso di conflitto.

Il funzionamento si basa su una combinazione di comunicazione e attesa;
Quando un processo decide di accedere alla risorsa, dichiara questa intenzione impostando una variabile condivisa, se l'altro processo non sta cercando di accedere, può entrare direttamente nella sezione critica. 
Tuttavia, se entrambi i processi vogliono accedere contemporaneamente, l'algoritmo utilizza una variabile aggiuntiva, chiamata turno, per stabilire chi può procedere per primo, il processo che non ha il turno aspetta fino a quando l'altro ha completato l'accesso alla risorsa.

Questo approccio garantisce che solo un processo alla volta possa entrare nella sezione critica, evitando conflitti e garantendo che entrambi i processi abbiano la possibilità di accedere alla risorsa e inoltre non richiede dipendenze esterne come meccanismi hardware o supporto del sistema operativo.

Tuttavia, presenta alcuni limiti, uno dei principali è l'attesa attiva, che implica che un processo in attesa consuma cicli di CPU controllando continuamente lo stato dell'altro e inoltre, se un processo si blocca all'interno della sezione critica, l'altro rimane in attesa indefinitamente. Questi aspetti rendono l'algoritmo meno efficiente rispetto a soluzioni più moderne, anche se il suo design rimane un esempio storico di come risolvere il problema della concorrenza in maniera indipendente.

**Esempio:**
![[Pasted image 20241228174919.png]]
#### Mutua esclusione: Supporto Hardware
Esiste un supporto da parte del costruttore del calcolatore per la mutua esclusione, un modo per poter ottenere la mutua esclusione nelle macchine monoprocessore è prevenire l'interruzione di un processo attivando e disattivando gli interrupt in modo seguente:
```
<disattiva le interruzioni>
<sezione critica>
<attiva le interruzioni>
```

Il problema della mutua esclusione viene risolto a discapito di un inefficienza, il processore non può liberamente alternare i processi, oltre a non funzionare su macchine SMP (se nel core 1 viene avviata una sezione critica la stessa potrebbe essere avviata su altri core, la soluzione sarebbe disabilitare gli interrupt a tutti, praticamente impossibile).
Nelle macchine SMP allora si è deciso di creare delle istruzioni macchina speciali per l'accesso a locazioni di memoria in modo atomico (o non interrompibile) come:
- **Test&Set**
- **Scambio (swap)**
L'accesso sequenziale ad una locazione di memoria è garantita dall'hardware, infatti se vengono eseguite due Test&Set contemporaneamente, esse vengono serializzate