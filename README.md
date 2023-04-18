# WPFThreads

-cosa importante : tenere d’occhio che sia .net 6,dato che è LTS(supporto lungo termine)<br>
-Aggiungi proprio nome al titolo per riconoscimento immediato da chi apre il file.<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002455.png?raw=true)
## Codice per creare righe colonne e 2 bottoni <br>
```
<Grid>
<Grid.RowDefinitions>
<RowDefinition></RowDefinition>
<RowDefinition></RowDefinition>
<RowDefinition></RowDefinition>
</Grid.RowDefinitions>
<Grid.ColumnDefinitions> // elemento di "Grid"
<ColumnDefinition></ColumnDefinition> // elemento di "Grid.ColumnDefinitions"
<ColumnDefinition></ColumnDefinition>
<ColumnDefinition></ColumnDefinition>
</Grid.ColumnDefinitions>
<Button Height="100" Grid.Row="1" Grid.Column="1" Width="200" > Bottone
1</Button>
<Button Height="50" Width="100">Bottone 2</Button>
</Grid>
```
-tie bar<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002556.png?raw=true)<br>

-Bisogna prevedere per forza un pulsante chiudi.in caso contrario alt+f4 per killare il programma.<br>
-WindowStartupLocation per schermo a più monitor posiziona la finestra al centro del monitor centrale.<br>


## Attributi di button

![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002636.png?raw=true)

-per comodità si va a capo dopo ogni attributo<br>
-message box è una finestra modale ossia prima di andare avanti bisogna chiuderla<br>
-Windows style none è una finestra senza stile<br>
Windows startup location —> stai al centro della scena<br>

![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002649.png?raw=true)<br>
utilizzo della versione 6.0 

![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002636.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002714.png?raw=true)<br>
gira x volte ma ogni giro incrementa il counter<br>
fare la stessa cosa con un lblcounter 2


in modo da far partire contemporaneamente due thread cosi da avere due visualizzazioni diverse<br>

![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002726.png?raw=true)<br>
possiamo impostarli a velocità diverse<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002749.png?raw=true)<br>
il primo ha già fatto i suoi mille giri mentre il secondo continua questo crea un problema ossia:<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002757.png?raw=true)<br>
a conteggio finito non si hanno effettuato tutti gli incrementi<br>


## strumento lock<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002809.png?raw=true)<br>
per funzionare ha bisogno di un oggetto di tipo statico.<br>
Se noi volessimo stampare un numero che continua ad incrementarsi e volessimo vedere il numero che si incrementa dovremmo inserire un delay.<br>
Esiste la possibilità di "addormentare" il sistema per un tot di millisecondi.
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002820.png?raw=true)<br>
Ma questa istruzione blocca completamente tutto il sistema che gestisce l'interfaccia grafica, per questo generalmente non è buona pratica creare degli event handler che durano per molto tempo.<br>
Per questo motivo dovremmo lanciare un thread separato su cui spostare su di esso il pezzo di codice che vogliamo eseguire.<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002832.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002848.png?raw=true)<br>

Il thread chiamante non riesce ad accedere a questo oggetto perché quell'oggetto è proprietà del thread principale. Per consentire a diverse parti del codice di interagire in modo sicuro con il thread principale utilizziamo il Dispatcher.<br>
## Quale potrebbe essere il problema qui??
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002857.png?raw=true)<br>

non è un problema di conteggio
il problema è che quando si ferma il primo counter non ti scrive 500 questo perchè non avviene un aggiornamento alla label Counter1<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002906.png?raw=true)<br>

## IL SEMAFORO
il semaforo funziona con un intero positivo che non può essere assolutamente negativo. ha due istruzioni una si chiama signal decrementa il contatore fino a zero e non di meno con la wait si aspetta che diventi zero.<br>
in questo caso servirebbero due signal che terminano entrambi in un wait.<br>
Semaforo = CountdownEvent semaforo = new CountdownEvent(2);<br>
semaforo.Wait();<br>
ora mancano i due signal che lo portano a zero 
alla fine delle due istruzioni metteremo
semaforo.signal();<br>
una volta finito aggiorniamo i contatori

![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002925.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002934.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002943.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20002951.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20003001.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20003012.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20003022.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20003029.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20003041.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20003050.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20003101.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20003111.png?raw=true)<br>
![result](https://github.com/lucaferee/WPFThreads/blob/main/images/Screenshot%202023-04-16%20003122.png?raw=true)<br>




