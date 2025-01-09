# Appunti-UNI
In questa repository sono presenti gli appunti di tutte le materie del CdS in Informatica suddivise in cartelle in base all'anno di corso. 

La repository utilizzata principalmente per contenere gli appunti/esercizi realizzati dagli studenti che hanno deciso di contribuire.

Gli appunti verranno caricati durante tutto l'anno scolastico di coloro che hanno realizzato e gestiscono il repository

---

Essendo la maggior parte dei file scritti con linguaggio **markdown** si consiglia l'utilizzo del software [obsidian](https://obsidian.md/) che offre l'integrazione con git e molto altri plugins realizzati dalla community per facilitare il lavoro

## Come importare il repository in locale

### Installare Git
Per prima cosa è necessario installare il software con il quale verrà gestito tutto il funzionamento, è possibile trovarlo [qui](https://git-scm.com/downloads), per settarlo correttamente è possibile seguire questa [guida](https://phoenixnap.com/kb/how-to-install-git-windows)  

Terminata l'installazione si scelga una qualsiasi directory dove voler importare la repository, una volta fatto bisogna seguire questi passaggi:
1. Posizionarsi all'interno della cartella, premere il tasto destro del mouse e poi selezionare la voce cerchiata nella foto sottostante ![](https://github.com/GiuseppeSifanno/Universita/blob/4f68a6d2e5cecf006d5c384547439cc0b88a5951/Immagini%20Tutorial/foto1.png)
2. Si aprirà un terminale con il quale sarà possibile, attraverso l'uso di comandi utilizzare git. Per poter clonare il repository sarà innanzitutto necessario recuperare il suo URL, per farlo è possibile copiare l'URL presente nella barra di ricerca del browser oppure cliccando sul pulsante *code* per poi copiare il link così come mostrato in figura. ![](https://github.com/GiuseppeSifanno/Universita/blob/4f68a6d2e5cecf006d5c384547439cc0b88a5951/Immagini%20Tutorial/foto2.png)
3. Ritornare nel terminale di *git* aperto in precedenze e digitare il comando: 
	```
	git clone <url copiato>
	```
	Premere invio e aspettare che venga scaricato tutto il contenuto
![](https://github.com/GiuseppeSifanno/Universita/blob/4f68a6d2e5cecf006d5c384547439cc0b88a5951/Immagini%20Tutorial/foto3.png)
4. Una volta terminato il download sarà presente la cartella, che rappresenta la repository con tutti i file aggiornati fino a quel momento. ![](https://github.com/GiuseppeSifanno/Universita/blob/4f68a6d2e5cecf006d5c384547439cc0b88a5951/Immagini%20Tutorial/foto4.png)

### Integrare obsidian con git
1. Una volta scaricato il software [obsidian](https://obsidian.md/), aprilo e selezionare la voce *Apri cartella come vault* ![](https://github.com/GiuseppeSifanno/Universita/blob/4f68a6d2e5cecf006d5c384547439cc0b88a5951/Immagini%20Tutorial/foto5.png)
2. Selezionare la cartella che è stata scaricata in precedenza e premere invio ![](https://github.com/GiuseppeSifanno/Universita/blob/4f68a6d2e5cecf006d5c384547439cc0b88a5951/Immagini%20Tutorial/foto6.png)
3. Si aprirà una nuova schermata, l'editor, dove saranno disponibili tutti i file presenti nella repository
#### Installare il plugin di git su obsidian
Per installare il plugin è necessario seguire questi passaggi: 
1. Cliccare sulla rotellina delle impostazioni ![](https://github.com/GiuseppeSifanno/Universita/blob/4f68a6d2e5cecf006d5c384547439cc0b88a5951/Immagini%20Tutorial/foto7.png)
2. Selezionare la voce *Plugin di terze parti* e poi *attiva i plugin della comunità* ![](https://github.com/GiuseppeSifanno/Universita/blob/4f68a6d2e5cecf006d5c384547439cc0b88a5951/Immagini%20Tutorial/foto8.png)
3. Cliccare il pulsante *Sfoglia* per cercare tutti i plugin caricati dalla community, digitare all'interno della barra di ricerca "*git*" e scaricare lo stesso plugin di quelle presente in foto ![](https://github.com/GiuseppeSifanno/Universita/blob/4f68a6d2e5cecf006d5c384547439cc0b88a5951/Immagini%20Tutorial/foto9.png)
4. Dopo aver cliccato sul riquadro, *scaricato* e *abilitato* il plugin, sarà possibile usufruire del sistema di versionamento che si sarà già collegato in automatico alla repository