I puntatori sono un nuovo tipo di **variabili** capaci di memorizzare SOLAMENTE gli **indirizzi di memoria**. 
![[Pasted image 20241218112359.png]]

### DICHIARAZIONE VARIABILI PUNTATORI
La dichiarazione di una variabile puntatore segue una struttura differente da una variabile normale:
```
<tipo_primitivo>* <nomevar>
```
L'operatore di **dereferenziazione** (\*) può anche essere posto vicino al nome della variabile.
Le caratteristiche di questa variabile puntatore cambiano nel corso del programma, infatti abbiamo:
- nome
- tipo
- valore 
- indirizzo
Il nome ed il tipo saranno i medesimi sin dalla loro dichiarazione a differenza del valore che sarà **casuale** (solo inizialmente). L'indirizzo invece sarà definito dal compilatore nella fase di compilazione.

Successivamente nel programma è essenziale **inizializzare** la variabile puntatore, perché essendo memorizzato un valore qualsiasi, randomico inizialmente all'interno della variabile, potrebbe portare a **corrompere** la memoria e le operazioni con i puntatori avranno problemi in fase d'esecuzione.
Usiamo il valore **NULL** per inizializzare le variabili puntatori.

E' importante definire un tipo ad una variabile puntatore poiché, come tutte le variabili primitive, anche il puntatore dev'essere definito in un proprio indirizzo di memoria. A differenza delle variabili primitive, il tipo associato a un puntatore non serve per il valore memorizzato, ma per interpretare correttamente i dati presenti all'indirizzo di memoria a cui punta.

==Il puntatore è una variabile con un **proprio** indirizzo in memoria che **memorizza l'indirizzo di un'altra variabile** e il tipo del puntatore specifica il tipo del valore contenuto nella variabile a cui punta.==

Gli errori che possono essere scaturiti dai puntatori non verranno segnalati dal compilatore ma saranno notati solo in fase di **esecuzione**.

### ASSEGNAZIONE DI UN VALORE 
Il puntatore, per la sua definizione, deve contenere l'indirizzo di memoria della variabile a cui punta; ma a noi è **impossibile** conoscere direttamente l'indirizzo della macchina, per questo non possiamo assegnare direttamente un valore alla variabile puntatore.
Per risolvere questo problema si utilizza **l'operatore d'indirizzo**.
Ex:
```
int main(){
	int a=5;
	float b=3.0;

	int* aPtr; // puntatore intero
	float* bPtr; // puntatore float

	aPtr=&a; //assegna l'indirizzo di memoria
	bPtr=&b;
	printf("\n a: %d  &a: %X", a, aPtr); 
	//avremo in output prima 5 e poi l'indirizzo di a
}
```
L'operatore di indirezione è posto automaticamente dal C, esso è utilizzato per **risalire al valore memorizzato** nella cella di memoria dell'indirizzo  puntato dalla variabile.
Seguendo l'esempio precedente attraverso l'operatore di indirezione posso risalire al valore memorizzato nella cella di memoria a cui punta aPtr.

### OPERATORE DI INDIREZIONE
L'operatore di indirezione si esprime ponendo l'operatore di dereferenziazione accanto alla variabile di tipo puntatore (\*aPtr).
<font color="red">!ATTENZIONE!</font>  Non bisogna confondere la posizione degli asterischi:
- **ASTERISCO AFFIANCO AL TIPO DELLA VARIABILE**: esprime la dichiarazione della variabile puntatore (int* aPtr).
- **ASTERISCO AFFIANCO ALLA VARIABILE**: esprime l'uso dell'operatore di indirezione sul puntatore (\*aPtr).
In una espressione, l'asterisco funge da operatore di **dereferenziazione** (b=\*pi).

### POLI OPPOSTI
L'operatore di dereferenziazione è l'inverso dell'operatore di indirizzo.
Gli operatori `*` e `&` si annullano a vicenda: 
1. L'operatore `&` restituisce l'indirizzo in memoria della variabile `a`.
   `*&a`: L'operatore `*` applicato sull'indirizzo di `a` restituisce il valore memorizzato all'indirizzo (cioè il valore di `a` stesso).  
   **In breve: `*&a` equivale a scrivere semplicemente `a`.**
2.  Se hai un puntatore `pi` dichiarato come `int *pi`, questo memorizza l'indirizzo di una variabile di tipo `int`.
    `*pi`: L'operatore `*` accede al valore memorizzato all'indirizzo puntato da `pi`. 
    `&*pi`: L'operatore `&` applicato al risultato di `*pi` (il valore) restituisce l'indirizzo che è stato dereferenziato, ovvero il valore originario di `pi`.  
    **In breve: `&*pi` equivale a scrivere semplicemente `pi`.**

Questa relazione riflette la **complementarità** dei due operatori:
- `&` trova un indirizzo.
- `*` accede al valore contenuto all'indirizzo

## UTILIZZO DEI PUNTATORI
Dopo aver definito come funzionano e la loro struttura, analizziamo dove vengono usati i puntatori.
Il loro scopo principale trova applicazione nel **passaggio dei parametri**. 
Come sappiamo ([PASSAGGIO DI PARAMETRI](file:///C:/Users/Milo/OneDrive%20-%20MSFT/PROGRAMMAZIONE%20APPUNTI%20BACKUP/PDF/ARGOMENTI%20ESONERO/7%20PROGRAMMAZIONE%20MODULARE%20E%20FUNZIONI/1%20PROGRAMMAZIONE%20MODULARE.pdf)) nel C il passaggio dei parametri tra funzioni avviene di default per valore, così da evitare modifiche indesiderate sui valori presenti nel programma chiamante.
Non sempre questo passaggio è sufficiente per la risoluzione dei problemi.
Per questo si usa il passaggio per riferimento, il quale trova perfetta espressione per la risoluzione dei suoi problemi attraverso l'uso dei puntatori.

*Ex. Funzione che attraverso il passaggio di valori non funzionerà mai:*
![[Pasted image 20241218144942.png]]
In questo esempio infatti possiamo usare i puntatori per poter passare il valore delle variabili in maniera tale che le modifiche vengano ereditate dalle variabili originali, direttamente accedendo al loro indirizzo di memoria.

![[Pasted image 20241218145214.png]]
Attraverso l'utilizzo dei puntatori possiamo **simulare il passaggio per riferimento**, passando alla funzione l'indirizzo delle variabili al posto dei loro valori. Generalmente questa tecnica viene usata nel momento in cui bisogna **modificare** i valore dei parametri. 
Un altro utilizzo lo troviamo nel caso in cui bisogni restituire più di un valore da una funzione.
Daremo (ipoteticamente) un solo valore di ritorno, modificando attraverso puntatore gli altri valori che vorremmo far ritornare al programma chiamante, in modo tale da modificare le variabili facendone uscire solo una.
