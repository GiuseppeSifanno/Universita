La programmazione **modulare** significa suddividere problemi principali in **sottoproblemi** indipendenti tra loro.
Un problema caratterizzato da:
- **Algoritmo**
- **Dati di partenza**
- **Risultati**
viene suddiviso in un insieme finito di *n* sottoproblemi a differenti livelli caratterizzati dalla tripla formula:
<center>(D<sub>i</sub>,A<sub>i</sub>R<sub>i</sub>)</center>
Differenziamo gli algoritmi per garantire la comprensione del nostro programma, avendo:
- **Algoritmo coordinatore**: il main
- **Algoritmi secondari**: i sottoprogrammi, essi possono avere a loro volta livelli **inferiori** e/o **paralleli**. 
Si costruisce una gerarchia di **macchine astratte**, ove ciascuna delle quali realizza un compito specifico in modo autonomo, con le proprie variabili ed istruzioni, il quale compito sarà di utilitaria importanza per i livelli **soprastanti**. La macchina astratta si appoggia su un livello di **macchina inferiore** se esiste.

La **MACCHINA INFERIORE** rispetto a quella astratta è la base concreta su cui la macchina astratta si baserà. E' reindirizzabile al linguaggio macchina o assembly che viene eseguito dal processore del computer.

### MACCHINA CONCETTUALE
Anche chiamato **Notional Machine**:

==La **MACCHINA CONCETTUALE** è un **computer idealizzato e concettuale le cui proprietà sono implicate dai costrutti nel linguaggio di programmazione utilizzato**.==

La macchina concettuale è l'insieme delle regole e dei meccanismi che definiscono il funzionamento interno di un linguaggio.
Ogni volta che si crea un programma si genera una macchina *virtuale*/*astratta/concettuale*, la quale dipende dal linguaggio utilizzato e definisce come la macchina utilizzerà i dati presenti nel codice, poiché ogni linguaggio di programmazione ha una propria Macchina Concettuale. Questo ci fa comprende come è fondamentale comprendere che linguaggio utilizzare a seconda del problema che bisognerà risolvere.

### ASTRAZIONE FUNZIONALE
Il programma viene visto come un **nuovo operatore**, il quale può gestire i dati.

==L'astrazione funzionale è la tecnica che permette di **ampliare** il repertorio di operatori disponibili.==

Le astrazioni funzionali sono fornite dal **linguaggio di programmazione ad alto livello** e prendono nomi differenti a seconda del linguaggio usato.
Il loro scopo è creare diverse **macchine astratte**, dando un nome ad un gruppo di istruzioni e stabilendo il metodo per **comunicare** tra la macchina astratta e il resto del programma.
Esse sono paragonabili a **nuove istruzioni** definite dall'utente per determinate esigenze; sono più **complesse** delle istruzioni base e ciascuna risolve uno **specifico** compito.
### TECNICHE PER INDIVIDUARE I SOTTOPROBLEMI
Sono basate sul metodo di soluzione dei problemi affrontati
nella lezione [4 PROBLEMI COMPLESSI](file:///C:/Users/Scassone/Desktop/Universit%C3%A0/MATERIE/PROGRAMMAZIONE/File%20PDF/4%20PROBLEMI%20E%20SOTTOPROBLEMI/PROBLEMI%20COMPLESSI.pdf):
- Sviluppo top-down:
	- **Metodo trial and error**: Provare costantemente fino alla ricerca della scomposizione ottimale.
- Bottom-up:
	- Usato soprattutto nell'adattamento di algoritmi codificati già esistenti a nuove situazioni
- Sandwitch: Basato sulla cooperazione tra top-down e bottom-up.

## SOTTOPROGRAMMA
Corrisponde ad un algoritmo *secondario* che risolve un sottoproblema.
Il sottoprogramma è individuato da un **nome** (identificatore) e concorre alla risoluzione di un problema **minore** il quale è di supporto per la risoluzione di problemi più **complessi**, ben definito e non necessariamente fine a **se stesso**. 
Il sottoprogramma rappresenta una **unità concettuale con significato più ampio**. 
Il sottoprogramma:
- prevede l'uso di risorse come le variabili
- è costituito da istruzioni semplici e composte
- Specifica come altri pezzi del programma possono utilizzarlo

### UTILITA' DEI SOTTOPROGRAMMI
Un programma viene diviso in sottoprogrammi, per rispettare la decomposizione creata nella fase di progettazione dell'algoritmo, ma specialmente perché lo stesso gruppo di istruzioni che rappresentano il sottoprogramma devono essere **ripetute più volte** durante il corso del programma, per questo si definiscono anche come **blocchi ripetibili**.

I sottoprogrammi sono fondamentali nella tecnica della programmazione poiché rendono ancora più qualitativo il software, aumentando la sua:
- Leggibilità
- Manutenibilità
- Riuso
### DEFINIZIONE DI SOTTOPROGRAMMA 
==Il SOTTOPROGRAMMA è un'astrazione funzionale che consente di individuare gruppi di istruzioni che possono essere invocate esplicitamente e la cui chiamata garantisce che il flusso di controllo ritorni al punto successivo all'invocazione.==
### CHIAMATA DI SOTTOPROGRAMMI
La chiamata di un sottoprogramma provoca l'esecuzione delle istruzioni del sottoprogramma, sarà il programma chiamante ad attivarla.

1. All'atto dell'**attivazione** dell'unità di programma, ovvero alla sua chiamata nel main o in altro sottoprgramma, viene sospesa l'esecuzione del **programma chiamante** e il controllo passa all'attività del sottoproblema (**unità attivata**).
2. All'atto del **completamento** della sua esecuzione, l'attività termina portando il flusso di controllo al programma chiamante.

	![[Pasted image 20241126122151.png]]

### NIDIFICAZIONE SOTTOPROGRAMMI
Le risorse che usa un sottoprogramma, possono includere altri sottoprogrammi. Questo porta alla creazione di una **gerarchia** tra i programmi, realizzando una struttura ad albero con relazione **padre-figlio**.
![[Pasted image 20241126122330.png]]

### COMUNICAZIONE TRA SOTTOPROGRAMMI
I sottoprogrammi tra di loro comunicano attraverso lo **scambio di dati** e può avvenire con:
- L'**ambiente esterno** (con l'utente in output/input)
- Con **l'ambiente chiamante** in modo:
	- **Implicito**(sconsigliato) --> attraverso variabili **globali**
	- **Esplicitamente**(consigliato) --> attraverso l'uso dei **parametri** **locali** che inserirà in input dal programma chiamante e che verranno tramutate in output dal sottoprogramma.
La comunicazione esplicita avviene **sempre** per un buon programma.
![[Pasted image 20241126122728.png]]

### VARIABILI DEL SOTTOPROGRAMMA
Ciascun sottoprogramma può utilizzare le proprie **variabili locali** (tra cui quelle interne al sottoprogramma e quelle temporanee all'avvio del sottoprogramma, queste ultime saranno distrutte alla fine del sottoprogramma per liberare spazio in memoria), le variabili **globali**, poiché definiti nel programma principale e le variabili dichiarate dai sottoprogrammi attualmente in esecuzioni, questo fenomeno prende il nome di **visiblità dipendente**.
La visibilità dipendente può essere di due tipi **statico e dinamico**:
##### STATICA
==La variabile statica dipende dalla struttura gerarchica delle dichiarazioni del sottoprogramma, ovvero da dove e come sono dichiarati i sottoprogrammi nel codice sorgente==
Il compilatore determina quali variabili sono visibili e accessibili in base alla loro posizione nel codice. Avviene in fase di **compilazione**, per ciò definita **statica**.
*Ex:*
```
void funzioneA(){
	int x=10;
	funzioneB(){
		printf(x);
	}
	funzioneB();
}
```
In questo caso *funzioneB* può visualizzare *x* poiché il sottoprogramma è stato definito all'interno di *funzioneA*.

##### DINAMICA
==La visibilità dinamica dipende dall'ordine di chiamata dei sottoprogrammi durante l'esecuzione del programma==
Ovvero, le variabili accessibili dipendono da quali sottoprogrammi sono stati chiamati e in che ordine. Ciò viene determinato durante la fase di **esecuzione**, per ciò definita **dinamica**.
*Ex:*
```
void funzioneB(int y){
	printf(y);
}

void funzioneA(){
	int x=10;
	funzioneB(x);
}

int main(){
	funzioneA();
}
```
In output riceveremo il valore *10*, poiché il programma *funzionaA* è stato chiamato prima di *funzioneB*, inoltre *funzioneA* passa come **argomento** *x*, in modo tale che sia visibile anche a *funzioneB*.

Come si evince anche i sottoprogrammi restituiscono un risultato e se ne deve specificare il tipo richiesto, il più comune e presente negli esempi precedenti è
la procedura **VOID**.
==La procedura **VOID** è un valore di un sottoprgromma in cui non esiste area di memoria in cui sarà restituito un risultato, non è presente un allocazione di memoria per essa. ==

### SHADOWING (OSCURAMENTO)
Diversi sottoprogrammi possono dichiarare risorse aventi lo stesso nome ma totalmente scorrelati tra loro, potendo avere anche tipo differente.
E' necessario verificare determinare quale variabile con lo stesso nome si sta facendo riferimento in un dato momento. La variabile considerata quindi sarà quella che è più vicina nel contesto di dichiarazione, ovvero la variabile dichiarata nel contesto più interno nella gerarchia dei sottoprogrammi sarà quella accessibile per il sottoprogramma; un altro fattore che determina la scelta della variabile considerata sarà l'ordine in cui i sottoprogrammi vengono chiamati.

### VISIBILITA' DEI SOTTOPROGRAMMI
Regole per la visibilità dei sottoprogrammi:
- Un identificatore è visibile nel sottoprogramma in cui è dichiarato e in tutti i sottoprogrammi locali ad esso nei quali è stato ridichiarato
- Le risorse di un sottoprogramma devono essere dichiarate prima di essere usate (come un programma normale)
- Le variabili globali possono essere viste da main e sottoprogrammi
- Una risorsa (variabile) locale è visibile ad un sottoprogramma P solo dalle istruzioni di P e dagli eventuali sottoprogrammi che sono stati definiti in P

Verifichiamo secondo questo *esempio:*
![[Pasted image 20241127092133.png]]
La risposta per V sarà:
- *x*
- *y* locale
- *d* locale
- *a* tramite **eredità** di S
- *c* e *z*

### DELIMITATORI DI UN SOTTOPROGRAM
Si dividono in due tipi di delimitatori:
- **DELIMITAZIONE SPAZIALE DI UNA RISORSA**: 
	La zona o **campo di visibilità** di codice in cui nel programma è possibile fare riferimento ad un identificatore è data dalle **regole di visibilità** 
- **DELIMITAZIONE TEMPORALE DI UNA RISORSA**:
	Le regole di **visibilità** definiscono anche quanto tempo rimane **in vita una variabile**, ovvero il tempo in cui un area della RAM è allocata per essa. Per questo la fase in cui è definita un'area di memoria per una variabile viene detta **FASE DI ALLOCAZIONE**.
	Normalmente il tempo di durata di una variabile è **pari alla durata d'esecuzione del programma in cui è definita**.
Possiamo quindi aggiungere alla classifica della costituzione di una variabile
([LEZIONE 5: LINGUAGGI DI PROGRAMMAZIONE](file:///C:/Users/Utente/Desktop/andrea%20milo/Scuola/Universit%C3%A0/PROGRAMMAZIONE/PDF%20FINITI/5%20LINGUAGGIO/1.%20LINGUAGGI%20DI%20PROGRAMMAZIONE%20(DALL_INIZIO).pdf)) altri 2 elementi, rendendo la struttura di una variabile a 6 **caratteristiche**:
- **nome(identificatore)
- **valore**
- **indirizzo**
- **tipo**
- **ambito**
- **durata**
## DURATA E AMBITO DI UNA VARIABILE
Ogni volta che si definisce una variabile si stabilisce:
- La durata della sua vita con la corrispettiva creazione e distruzione attraverso particolari istruzioni
- La sua visibilità (se globale, locale o estesa ad altri blocchi)
### ALLOCAZIONE DELLE VARIABILI NELLA RAM
![[Pasted image 20241127092214.png]]
Definiamo le nuove due aree incontrate.
L'**area di Stack** è utilizzata per memorizzare il record di attivazione dei programmi, costituito da:
- Indirizzo del codice dell'istruzione successiva
- Parametri del sottoprogramma
- Variabili locali al sottoprogramma
L'**area di memoria Heap** è utilizzata per l'allocazione dinamica, per questo più grande e lenta di quella stack, essa rimane valida finché non viene deallocata.

### EFFETTI COLLATERALI DI UN SOTTOPROGRAMMA
E' importante precisare alcuni fattori durante la modifica di variabili globali apportate da un sottoprogramma; ovvero quando esso modifica una variabile globale non si può definire totalmente **indipendente e autonomo**, ma dipende da elementi esterni.
<font color="red">!ATTENZIONE!</font> Le variabili globali vanno usate con cautela, poiché dobbiamo garantire sempre la **chiarezza e la sicurezza**, azioni non sempre garantite con l'uso di variabili globali.

## PARAMETRI
Come abbiamo visto negli esempi precedenti, ci sono diversi modi di passare i dati tra un sottoprogramma e l'altro, questo fenomeno viene definito **PASSAGGIO DI PARAMETRI**, esso si divide in diverse tipologie: 
- **PARAMETRI FORMALI** 
- **PARAMETRI ATTUALI** o **EFFETTIVI**
### PARAMETRI FORMALI
Sono il **segnaposto** per indicare simbolicamente gli oggetti (con il loro tipo e struttura) su cui il sottoprogramma lavora. I loro nomi compaiono nell'**intestazione del sottoprogramma**, non hanno legami con nomi usati altrove.

Sono specificati all'atto della **definizione del sottoprogramma**, sono quindi simbolici e consentono di definire i dati e i loro tipi che devono essere passati al sottoprogramma quando sarà invocato.
All'atto della **chiamata** vengono sostituiti dai **parametri effettivi**, ovvero i dati su cui effettivamente il sottoprogramma adopererà.

### PARAMETRI EFFETTIVI
Sono i parametri su cui il sottoprogramma lavorerà e coincidono con i parametri formali. 
L'esecuzione dell'istruzione di chiamata comporta la **sostituzione** dei parametri **formali** con quelli **reali**.

## TIPI DI PASSAGGIO
Esistono vari tipi di passaggio di parametri:
- **PER VALORE** --> Si calcola il valore del parametro reale e lo si **sostituisce** al corrispondente formale. Usato generalmente per parametri che rappresentano un **argomento** e NON il risultato di un sottoprogramma.

- **PER REFERENZA** --> Il parametro **effettivo** è una variabile ed ha a disposizione una locazione di memoria il cui **indirizzo** viene **passato** al parametro **formale**. Usato più spesso quando il parametro rappresenta il risultato e ha dimensioni notevoli. E' potenzialmente sottoposto a grandi margini di **errori**, data l'uso della stessa variabile usata sotto diverse **nominazioni**.

- **PER NOME(o VALORE)** --> Il nome del parametro **formale** viene sostituito col **nome** del parametro **reale**
*Ex:*
Supponiamo di avere un sottoprogramma P a cui passiamo un parametro formale *pf* e viene chiamato con parametro attuale *pe*.
- Per valore: *pf* si comporta come una variabile **locale** a P
- Per riferimento: Al momento dell'attivazione di P viene calcolato **l'indirizzo** di *pe*, e *pf* viene creato con riferimento alla stessa **locazione di memoria**.
- Per nome: Al momento dell'attivazione di P il valore di *pe* viene calcolato e memorizzato in una nuova **locazione assegnata a *pf***.
<font color="red">!ATTENZIONE!</font> Il passaggio per nome **non esiste in C**.

### PRO E CONTRO DEL PASSAGGIO DI PARAMETRI
Tabella aggiornata con i **Pro** e i **Contro** per ciascun metodo:

|**Metodo**|**Pro**|**Contro**|
|---|---|---|
|**Valore**|- Permette la trasmissione del valore di un parametro dal chiamante|- Aumenta l'occupazione di memoria e il tempo|
||- Consente la separazione tra programma chiamante e programma chiamato|- Rende difficile la gestione di parametri di dimensione variabile|
|**Riferimento**|- Evita problemi di passaggio grazie al trattamento degli indirizzi gestito dal compilatore|- Causa effetti collaterali spesso imprevedibili|
||- Non occupa memoria aggiuntiva||
