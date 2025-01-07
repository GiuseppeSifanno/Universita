**TRACCIA ES:**

La libreria BuonaLettura gestisce l'approvvigionamento e la vendita dei libri mediante una tabella che per ogni libro riporta: codice, titolo, autori, numero copie disponibili, numero copie minimo di scorta. I clienti della libreria effettuano le loro richieste inviando il codice del libro e il numero di copie da ordinare. Progettare una soluzione al problema di gestione delle richieste che fornisca in output:

- Per ogni richiesta tratta un messaggio di richiesta accettata o rifiutata
 
- Il codice del libro, titolo e autori della richiesta evasa con il maggior numero di copie.

- I codici di tutti i libri le cui copie disponibili sono in esaurimento e la quantità da riordinare per mantenere il numero minimo di scorta.

- La tabella aggiornata.

  

**ANALISI**

- **Chiarifica**:
	Il programma deve gestire l’approvvigionamento della vendita dei libri tramite una tabella, tabella che sarà nota ed implementata dal programmatore il quale deciderà la sua grandezza e quanti libri conterrà, supponendo che esistano dei libri noti al programmatore, il programma deve memorizzare i dati di ogni libro, i quali dati sono il codice del libro, il quale si presuppone sia un intero, il titolo sotto forma di stringa, gli autori che si supponga venga memorizzato solamente il primo, le copie disponibili nella libreria, il quale valore è un intero assieme a quello di scorta nel magazzino.
	Si imposta il nome e l’autore attraverso le funzioni stringa definite da libreria esterna.
	Durante le richieste dell’utente si gestiscono varie casistiche. Per ogni richiesta si tratta un messaggio di richiesta con esito positivo se il libro è presente o non esiste con un esito negativo. Si presuppone che si analizza una richiesta per volta.
	Per ogni richiesta verrà conservato il numero di copie richiesto in modo tale da salvare e memorizzare i dati della richiesta che è stata evasa con il maggior numero di copie. Si ipotizza che venga mostrato solo uno dei dati dei libri se 2 o più  libri hanno la stessa richiesta massima del numero di copie.
	Il programma controlla se le copie sono in esaurimento, ovvero se il valore della richiesta è inferiore alle copie presenti. Aggiornare la tabella dopo ogni richiesta effettuata con successo.

- **Dati**: 
    - **DATI INPUT:**

|                                                                                                                                                 | VARIABILI                                                                                                                                                   | TIPO                                                                                       | VINCOLI                                                         |
| ----------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | --------------------------------------------------------------- |
| Numero libri                                                                                                                                    | n                                                                                                                                                           | intero                                                                                     | >0                                                              |
| Tabella libri:<br><br>- Codice libro<br>    <br>- autore<br>    <br>- titolo<br>    <br>- numero copie disponibili<br>    <br>- libri in scorta | Lib array di record:<br><br>Lib\[i].codice<br><br>  <br><br>Lib\[i].autore<br><br>Lib\[i].titolo<br><br>Lib\[i].copie<br><br>  <br>  <br><br>Lib\[i].scorta | intero<br><br>  <br><br>stringa<br><br>stringa<br><br>intero<br><br>  <br>  <br><br>intero | <MAXLENGH<br><br><MAXLENGH<br><br>>=0<br><br>  <br>  <br><br>>0 |
| Codice del libro                                                                                                                                | cod_libro                                                                                                                                                   | stringa                                                                                    | <MAXLENGTH                                                      |
| Numero copie richieste                                                                                                                          | N_copie_richieste                                                                                                                                           | intero                                                                                     | >0                                                              |

- DATI OUTPUT:

|                                       | VARIABILI                                                                                                                                                   | TIPO                                                                                       | VINCOLI                                                         |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | --------------------------------------------------------------- |
| Messaggio accettazione/rifiuto        |                                                                                                                                                             |                                                                                            |                                                                 |
| Libro più richiesto                   | Libromax: record:<br><br>- Codice<br>    <br>- Autore<br>    <br>- Titolo<br>    <br>- Numero copie<br>    <br>- Scorta                                     |                                                                                            |                                                                 |
| Tabella aggiornata                    | Lib array di record:<br><br>Lib\[i].codice<br><br>  <br><br>Lib\[i].autore<br><br>Lib\[i].titolo<br><br>Lib\[i].copie<br><br>  <br>  <br><br>Lib\[i].scorta | intero<br><br>  <br><br>stringa<br><br>stringa<br><br>intero<br><br>  <br>  <br><br>intero | <MAXLENGH<br><br><MAXLENGH<br><br>>=0<br><br>  <br>  <br><br>>0 |
| Codice di tutti i libri più richiesto |                                                                                                                                                             |                                                                                            |                                                                 |

- **DATI DI LAVORO:**
<table>  
  <tr>  
    <td></td>  
    <td><b>VARIABILI</b></td>  
    <td><b>TIPO</b></td>
    <td><b>VICNOLI</b></td>  
  </tr> 
  <tr>
   <td>Contatore</td>
   <td>i</td>
   <td>intero</td>
   <td>a seconda dei casi >0</td>
  </tr>
  <tr>
   <td>Contatore ciclo 2</td>
   <td>j</td>
   <td>intero</td>
   <td>a seconda dei casi >0</td>
  </tr>
  <tr>
   <td>Sentinella per i controlli</td>
   <td>flag</td>
   <td>bool (short)</td>
   <td>0 o 1</td>
  </tr>
</table>
  

**Sottoproblemi**:

- Gestione Libreria
	- P1: Acquisizione Tabella
		- P1.1: Lettura numero libri
		- P1.2: ∀ Acquisizione libri
			- P1.2.1: Acquisisci codice
			- P1.2.2: Acquisici titolo
			- P1.2.3: Acquisci autore
			- P1.2.4: Lettura disponibile
			- P1.2.5: Lettura scorta
	- P2:  Gestire richieste
		- P2.1: Inizializiamo il massimo
		- P2.2: ∀ Acquisizione delle richieste
			- P2.2.1: Acquisire codice libro
			- P2.2.2: Acquisire numero copie
			- P2.2.3: Ricerca libro
			- P2.2.4: (Selezione) Ricerca riuscita
				- P2.2.4.1: (Selezione) Richiesta accettata **SI**
				- P2.2.4.1.1: Aggiornamento massimo
				- P2.2.4.2: Richiesta rifiutata **NO**
	- P3: Gestione approvvigionamento
		- P3.1: ∀ Scansione tabella libri
			- P3.1.1: (Selezione) Copie in esaurimento? 
			- **SI:**
				- P3.1.1.1: Output codice libro
				- P3.1.1.2: Calcolo quantità da riordinare
				- P3.1.1.3: Output quantità da riordinare
			- **NO**:
				- P3.1.1.4: Null
	- P4: Tabella aggiornata
		-  P4.1: ∀ Output tabella appionate
			- P4.1.1: Output codice libro
			- P4.1.2: Output titolo
			- P4.1.3: Output autori
			- P4.1.4: Output numero copie
			- P4.1.5: Output numero scorta
		- P4.2: Output copie massimo
			- P4.2.1: Codice libro
			- P4.2.2: Numero max

**ALBERO GRAFICO**
![[Pasted image 20241209141859.png]]
![[Pasted image 20241209142215.png]]
![[Pasted image 20241209142250.png]]

**FLOWCHART**
![[P1.jpg]]
![[P2.jpg]]
![[P2,2.jpg]]
![[P3 1.jpg]]
![[P4.jpg]]

#### CODICE
```
/*
 ============================================================================
 Name        : ESERCIZIO.c
 Author      : 
 Version     :
 Copyright   : Your copyright notice
 Description : Hello World in C, Ansi-style
 ============================================================================
 */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#define MAXLUNGH 50
#define MAXLIBRI 10

typedef struct {
	char codice[MAXLUNGH];
	char titolo[MAXLUNGH];
	char autore[MAXLUNGH];
	int copie;
	int scorta;
}Lib_t;

void acquisisciTabella(Lib_t Libreria [], int dim);
void stampa(Lib_t libro);

int main(void) {

	int n_lib;
	Lib_t Lib[MAXLIBRI];
	Lib_t libMax;
	char codiceRichiesta[MAXLUNGH];
	int copieRichiesta;
	char risp;
	short flag=0, i;



	do {
		printf("\nQuanti libri inserire --> ");
		scanf("%d", &n_lib);
		getchar();
	} while (n_lib<=0 || n_lib >MAXLIBRI);

	acquisisciTabella(Lib, n_lib);

	libMax.copie=-1;
	do {
		printf("\nInserire codice libro da cercare --> ");
		scanf("\n%5s", codiceRichiesta);
		printf("\nQuanti libri acquistare --> ");
		scanf("%d", &copieRichiesta);
		flag=0;
		i=0;
		do{
			if(strcmp(codiceRichiesta,Lib[i].codice)==0)
				flag=1;
			i++;
		} while (i<n_lib && flag==0);
		i--; // torniamo indietro all'elemento trovato
		if(flag==1){
			printf("\n Libro trovato!");
			if (Lib[i].copie >= copieRichiesta){
				printf("\nOrdine evaso!\n");
				Lib[i].copie-=copieRichiesta;
				if (copieRichiesta>libMax.copie)
				{
					libMax=Lib[i];
					libMax.copie=copieRichiesta;
				}
			}
			else{
				printf("\n Ordine non evadibile\n");
			}
		} else
			printf("\n libro non trovato");

		printf("Vuoi continuare (s/n)?");
		scanf("\n%c", &risp);
	}while(risp=='s' || risp=='S');
	
	printf("\n Il libro più richiesto è: ");
	stampa(libMax);
    
    /*Secondo l'analisi non si gestirà il caso di errore
    in caso avessimo 2 libri con stesso codice o 2 massimi uguali
    per permette la riuscita di un esame rapito ed efficente.*/
    
	return EXIT_SUCCESS;
}

void acquisisciTabella(Lib_t Libreria [], int dim) {

	for(int i=0; i<dim;i++){
		printf("\n Inserire i dati del libro: \n");
		printf("\t Codice (solo 5 caratteri)--> ");
		fgets(Libreria[i].codice, sizeof(Libreria[i].codice), stdin); 
		//uso di fgets per prevenire gli spazzi tra caratteri nei nomi dei libri
		Libreria[i].codice[strcspn(Libreria[i].codice, "\n")] = '\0'; // Rimuove newline
		
		printf("\t Titolo -->");
		fgets(Libreria[i].titolo, sizeof(Libreria[i].titolo), stdin); 
		//uso di fgets per prevenire gli spazzi tra caratteri nei nomi dei libri
		Libreria[i].titolo[strcspn(Libreria[i].titolo, "\n")] = '\0'; // Rimuove newline
		
		printf("\t Autore -->");
		fgets(Libreria[i].autore, sizeof(Libreria[i].autore), stdin); 
		//uso di fgets per prevenire gli spazzi tra caratteri nei nomi dei libri
		Libreria[i].autore[strcspn(Libreria[i].autore, "\n")] = '\0'; // Rimuove newline
		
		printf("\t NumCopie -->");
		scanf("%d", &Libreria[i].copie);
		getchar();
		
		printf("\t Scorta minima -->");
		scanf("%d", &Libreria[i].scorta);
	    getchar();
	}
}

void stampa(Lib_t libro) {

	printf("\t Codice --> %s\n", libro.codice);
	printf("\t Titolo --> %s\n", libro.titolo);
	printf("\t Autore --> %s\n", libro.autore);
	printf("\t NumCopie --> %d\n", libro.copie);
	printf("\t Scorta minima -->%d\n", libro.scorta);

}

```
[link per visualizzare su GDB il codice](https://onlinegdb.com/PKtoa_gEl)
