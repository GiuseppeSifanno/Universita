
Algoritmo nasce da **Al-Khowarizmi**.
Per un informatico segue delle regole
- **SEQUENZIALITÀ
- **DETERMINISTICO**
- **GENERALITÀ**
Un algoritmo deve avere un punto di inizio e un punto di fine ed un numero finito di passi.
L’istruzione deve essere realizzabile dall’esecutore (macchina), ovvero comprensibile.
Un algoritmo trasforma dati in **informazioni**.
L'algoritmo descrive come risolvere una **classe di problemi** (ex. Costruire le funzioni), ovvero in modo tale che una soluzione si attui a più problemi dello stesso genere.

 <span style="color:blue"><b>SEQUENZIALITÀ</b></span>
In ogni algoritmo è presente una sequenza.

 <span style="color:blue"><b>DETERMINISTICO</b></span>
I passi devono essere eseguiti in modo univoco.

 <span style="color:blue"><b>GENERALITÀ</b></span>
La soluzione non deve dipendere da valori predefiniti di dati.

***TIPI DI ALGORITMI:***
- DETERMINISTICO
- PROBABILISTICO
- CONCORRENTI
Altre proprietà sono la **TERMINAZIONE e la REALIZZABILITÀ**.
1) Le istruzioni devono avere un numero finito  devono essere seguiti in un numero finito di volte.
2) L'esecutore dev'essere in grado di eseguire, attraverso le sue risorse, il programma.
*Lo scopo di un algoritmo è descrivere la risoluzione di una classe di problemi.*
Un algoritmo è una ==sequenza di operazioni== che facciamo ogni giorno in qualsiasi attività, ==non è un concetto== legato principalmente all'informatica.

### **TIPOLOGIE DI ALGORITMI**
L'algoritmo deve avere un inizio ed una fine ben definita. L'algoritmo può essere:
- **DETERMINISTICO** (ovvero un algoritmo che opera sugli stessi dati fornendo un output ben definito e medesimo) 
- **PROBABILISTICO** (ovvero l'esecuzione di un algoritmo che on gli stessi dati genererà risultati differenti)
Il modello di un algoritmo si chiama **astrazione**.
==L'esecutore di un algoritmo può essere sia un essere umano che una macchina;== per essere eseguito correttamente da tutti un algoritmo dev'essere ==ben implementato ed essere uniforme==, senza presentare così un comportamento non uniforme.

## <span style="color:red"><b>PROGRAMMAZIONE STRUTTURATA</b></span>
La metodologia utilizzata è l'approccio **TOP-DOWN**, ovvero la scompoizione del problema principale in *==sottoproblemi==*. L'approccio utilizzato per la risoluzione dei sottoproblemi è identico alla risoluzione del problema madre.
Il linguaggio utilizzato per la descrizione di questi problemi , ==non è un linguaggio di programmazione==, bensì linguaggi **grafici e lineari** (uso delle parole).
Le rappresentazioni che tratteremo sono:
- **Diagrammi di flusso**
- **Linguaggio lineare**
- **Alberi di Decomposizione**

### **DIAGRAMMI DI FLUSSO**
Si sviluppa graficamente su 2 dimensioni e si basa su pochi simboli; è un linguaggio universale e per questo elimina le ambiguità.
I ==blocchi== che caratterizzando il diagramma di flusso sono:
![[Pasted image 20241007163858.png]]
La risoluzione di un problema nei flow chart consiste nell'esecuzione ordinata delle operazioni, l'ordinamento è fondamentale ed è garantito attraverso le frecce che collegano i blocchi.
![[Screenshot_2024-10-07-17-00-26-183.jpeg]]
Uno stesso diagramma di flusso è trascivibile su più linguaggi di programmazione.
**SVANTAGGI DEI DIAGRAMMI DI FLUSSO**
1. I diagrammi sono ingombranti e non entrano mai in una singola pagina.
2. Le modifiche tendono a ==destrutturare== il grafico.

**SCHEMI FONDAMENTALI**
- *SEQUENZA* è una concatenazione delle azioni.
- *ITERAZIONE* è assieme alla sequenza l'unico blocco che rilascia uscite diverse e non singola, ma sempre con una singola entrata e con la stessa fine comune. Ripete l'azione fino alla variazione di uno specifico dato.
- *SELEZIONE* sono scelte alternative in dipendenza ad una condizione.

**TIPI DI ITERAZIONE:**
![[Screenshot_2024-10-07-17-17-08-813.jpeg]]
I diagrammi son strutturati se ogni azione si sussegue in modo ordinario e preciso.
## <span style="color:red"><b>TEOREMA DI BOHEM-JACOPINI</b></span>
*Dato un processo P e un diagramma che lo descrive, è sempre possibile determinare un
processo Q, equivalente a P, che sia descrivibile con un diagramma strutturato
• Processi equivalenti se producono lo stesso effetto
Un processo o metodo solutivo può essere sempre descritto tramite diagrammi strutturati
Un qualsiasi algoritmo può essere espresso usando solo combinazioni di sequenza,
selezione e iterazione*.