I frammenti di codice generati dai sottoprogrammi si chiamano **Funzioni e Procedure**, ogni linguaggio ha il proprio modo di definire le funzioni e meccanismi diversi per **invocarli**.
il principio alla base delle funzioni e procedure si chiama **ASTRAZIONE**.

==L'astrazione è il processo di definizione e utilizzo di sottoprogrammi senza preoccuparsi si come è implementato.==

Le **funzioni** sono delle **astrazioni sui dati**, poiché ci permettono di estendere gli operatori disponibili.
Le **procedure** sono delle **astrazioni sulle istruzioni** poiché ci permettono di estendere le istruzioni primitive.

Si usa la programmazione modulare oggi giorno perché è sempre più difficile creare programmi che diano soluzioni a problemi reali complessi utilizzando un **unico file sorgente**. Specialmente diviene complesso **riutilizzare** lo stesso codice in altri problemi data la sua lunghezza.
Per questo possiamo definire diversi vantaggi della programmazione modulare:
- Migliora la **leggibilità**
- Avviene il fenomeno dell'**astrazione**
- E' **riutilizzabile**
- Ed è **modulare** (frammenti diversi di codice svolgono **ruoli diversi e testabili**. Solo **una parte di codice** svolge un determinato lavoro)
*Ex:*
E' più semplice leggere un main che sia imposto in questo modo:
```
int main(){
	int peso=90, int altezza=198;
	float bmi=calcoloBMI(peso,altezza); //FUNZIONE
	printf(bmi);
}
```
Rispetto ad un main scritto in questo modo:
```
int main(){
	int peso=90, int altezza=198;
	float bmi=(float) peso/ ((altezza/100)*(altezza/100)); //Non Funzione
	printf(bmi);
}
```

### LEGGI DELLA PROGRAMMAZIONE MODULARE
Chi ci garantisce l'uso di una buona programmazione modulare nel C sono proprio le funzioni e le procedure.
Le leggi fondamentali della programmazione modulare sono:
- La possibilità di dividere il programma in **moduli**
- I moduli devono essere **quasi indipendenti l'uno dall'altro**
- Ogni modulo dev'essere testato singolarmente
- Ogni modulo deve avere un interfaccia chiara
L'utilizzo stesso delle **librerie** fa riferimento all'uso della programmazione modulare, poiché richiamiamo parti di codice (funzioni) che sono state scritte indipendentemente dal nostro programma da altre persone.

## MA CHE COS'E' UNA FUNZIONE?

==Una **funzione** è un **blocco di codice riutilizzabile**, progettato per eseguire una specifica operazione o serie di esse. Le caratteristiche della funzione sono:==
==- Il **nome**==
==- Insieme di **parametri**==
==- **Valore di ritorno**==
==- Implementazione==
==Nome, parametri e valore di ritorno definiscono il **PROTOTIPO DELLA FUNZIONE**==

<font color="red">!ATTENZIONE!</font> Il **prototipo della funzione NON corrisponde alla sua chiamata**.
Poiché, ricordiamo, che la chiamata è **un istanza del prototipo**, cioè leghiamo i parametri a nomi di variabili di quel tipo specifico.

**Prototipo della funzione**: 
`float calcoloBMI(int , int)`

**Chiamata della funzione**:
`bmi=calcoloBMI(altezza, peso)`

**Sintassi** nel linguaggio C:
```
<valore_di_ritorno> <nomeFunzione> (<parametri>){
	<implementazione>
}
```
*Ex:*
```
short int promosso (int voto){
	short int promosso=0;
	if(voto>17) promosso=1;
	return promosso;
}
```

<font color="red">!ATTENZIONE!</font> I **parametri** della funzione si chiamano **ATTUALI** nella sua **chiamata** e **FORMALI** nel suo **prototipo**. Essi devono essere compatibili, altrimenti si generano degli errori.
La fase che riguarda i prototipi delle funzioni dev'essere stipulata (ovvero dichiararle) **prima del main**.
Il passaggio di parametri inoltre, in C, avviene di **default** per **valore**, TRANNE GLI **ARRAY**.
**Definiamo che**: Il passaggio di parametri per valore **effettua una copia** del valore del parametro ATTUALE nel parametro FORMALE ed eventuali modifiche ai parametri **verranno perse al termine dell'esecuzione della funzione,** poiché la funzione lavora su una **nuova** locazione di memoria, lasciando **senza modifiche** quella vecchia.
Per evitare ciò si usa il passaggio per **riferimento**, il quale dev'essere impostato dal programmatore. Nel passaggio per riferimento sia il parametro formale che quello attuale puntano alla **stessa locazione** di memoria; in modo tale che le modifiche vengono **ereditate dal programma chiamante**.

**Ricordiamo** anche che: Non esiste un'unica intestazione delle funzioni, ovvero esistono diversi tipi di implementazione per una funzione.

La scelta dei parametri di **Input** e dei valori di **ritorno** della funzione devono essere definiti e chiari ben prima della creazione della funzione stessa, questo è un concetto fondamentale e dogmatico della **progettazione** modulare.
## DIFFERENZA TRA FUNZIONE E PROCEDURE
==Una procedura è una funzione che corrisponde ad un insieme di istruzioni che non corrisponde ad una cella di memoria in cui collocare il risultato; per rappresentare in C una funzione che non restituisce nulla si usa la parola chiave **void**. Non esiste un area di memoria nel main dedicata alla restituzione del risultato della procedura.==
Infatti nella procedura non avremmo **return** rispetto alla funzione.

==Una funzione è un sottoprogramma a cui **corrisponde** una locazione in una cella di memoria, dove viene conservato il valore di ritorno al termine della sue esecuzione== (o nello stack o in un registro del processore).