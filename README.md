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









