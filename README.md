# WPFThreads

-cosa importante : tenere d’occhio che sia .net 6,dato che è LTS(supporto lungo termine)<br>
-Aggiungi proprio nome al titolo per riconoscimento immediato da chi apre il file.<br>

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

