# 		-- WINDOWS POWERSHELL --

## 				- El sistema de ayuda -



### Ejercicio 1:

###### Ejecuta Get-Update, para instalar los ficheros actualizados de ayuda. A partir de ahí, utiliza los cmdlets Get-Help y Get-Command para averiguar la información necesaria para contestar el resto de las siguientes cuestiones.

```
PS C:\Windows\system32> Update-Help
```



### Ejercicio 2:

###### En PowerShell, los cmdlets que permiten interactuar con los procesos en ejecución en el sistema se nombran con el nombre de objeto “process”. Mediante Get-Command, averigua el nombre de todos esos cmdlets. 

###### A partir de ahí, utiliza dichos cmdlets para resolver los siguientes ejercicios, consultando la ayuda disponible sobre ellos para saber cuál utilizar en cada caso, y cómo:

###### 	a) Lanzar a ejecución un proceso que ejecute el programa notepad.exe (bloc de notas).
```
PS C:\Windows\system32> Start-Process notepad.exe
```

###### 	b) Obtener el listado de los procesos en ejecución en el sistema.
```
PS C:\Windows\system32> Get-Process
```

###### 	c) Listar exclusivamente el proceso que ejecuta el bloc de notas, utilizando su nombre de proceso (columna “ProcessName” en el listado anterior).
```
PS C:\Windows\system32> get-process -name notepad
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    195      13     3024      14724       0,17   1276   1 notepad
```

```
PS C:\Windows\system32> get-process -ProcessName notepad
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    195      13     3024      14724       0,17   1276   1 notepad
```

###### 	d) Finalizar el proceso que ejecuta el bloc de notas, utilizando su identificador interno (“Id”).
```
PS C:\Windows\system32> Stop-Process -id 7124
```

###### 		e) Volver a listar todos los procesos en ejecución del sistema, y localizar el que más CPU ha consumido y aquel que está utilizando más memoria virtual (NOTA: consulta la ayuda completa del cmdlet para averiguar el significado de las columnas del listado).
```
PS C:\Windows\system32> Get-Process | Sort CPU -Descending | Select-Object name, CPU
- System <<<<< El que mas CPU consume
```

```
PS C:\Windows\system32> Get-Process | Sort VM -Descending |Select-Object name, VM
- SearchUI <<<<< Mas memoria usada
```



### Ejercicio 3:

###### Consulta la ayuda sobre el concepto “about_History”, y contesta a las siguientes preguntas:

###### 	a) ¿Qué hace el cmdlet Get-History?
```
PS C:\Windows\system32> Get-History
```

`Muestra el historial de los comandos que han sido usados`

###### b) ¿Qué hace el cmdlet Invoke-History?

```
PS C:\Windows\system32> Invoke-History
```

`Ejecuta el último comando usado`

###### c) Averigua los alias, si existen, de los dos cmdlets anteriores.

```
PS C:\Windows\system32> Get-Alias -Definition Get-History
CommandType     Name
-----------     ----
Alias           ghy -> Get-History
Alias           h -> Get-History
Alias           history -> Get-History
```

```
PS C:\Windows\system32> Get-Alias -Definition Invoke-History
CommandType     Name
-----------     ----
Alias           ihy -> Invoke-History
Alias           r -> Invoke-History
```

###### 		d) Utilizando ambos cmdlets (y/o sus alias), vuelve a ejecutar los cmdlets que has utilizado para resolver el ejercicio 2.
	a)
		PS C:\Windows\system32> Get-Alias -Definition Start-Process
		CommandType     Name
		-----------     ----
		Alias           saps -> Start-Process
		Alias           start -> Start-Process	

```
	PS C:\Windows\system32> saps notepad.exe
	PS C:\Windows\system32> start notepad.exe
```

```
b)
	PS C:\Windows\system32> Get-Alias -Definition Get-Process
	CommandType     Name
	-----------     ----
	Alias           gps -> Get-Process
	Alias           ps -> Get-Process
```

```
	PS C:\Windows\system32> gps
	PS C:\Windows\system32> ps
```

```
c)
    PS C:\Windows\system32> Get-Alias -Definition Get-Process
    CommandType     Name
    -----------     ----
    Alias           gps -> Get-Process
    Alias           ps -> Get-Process
```

```
    PS C:\Windows\system32> gps -name notepad
    Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
    -------  ------    -----      -----     ------     --  -- -----------
        195      13     3024      14724       0,17   1276   1 notepad
```

```
    PS C:\Windows\system32> ps -name notepad
    Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
    -------  ------    -----      -----     ------     --  -- -----------
        195      13     3024      14724       0,17   1276   1 notepad
```

```
d)
	PS C:\Windows\system32> Get-Alias -Definition Stop-Process
    CommandType     Name
    -----------     ----
    Alias           kill -> Stop-Process
    Alias           spps -> Stop-Process
```

```
    PS C:\Windows\system32> kill -id 1276
    PS C:\Windows\system32> spps -id 1276
```

```
e) 
PS C:\Windows\system32> Get-Process | Sort CPU -Descending | Select-Object name, CPU
- System <<<<< El que mas CPU consume

PS C:\Windows\system32> Get-Process | Sort VM -Descending |Select-Object name, VM
- SearchUI <<<<< Mas memoria usada
```

###### 		e) Indica cuáles son los atajos de teclado que se mencionan en la ayuda del concepto “about_History”, y practica brevemente con ellos.

```
Use this key      To perform this action
-------------     ----------------------------------------------
UP ARROW          Displays the previous command.

DOWN ARROW        Displays the next command.

F7                Displays the command history.
                  To hide the history, press ESC.

F8                Finds a command. Type one or more characters,
                  and then press F8. For the next instance,
                  press F8 again.

F9                Find a command by history ID. Type the history
                  ID, and then press F9. To find the ID, press F7.
```



### Ejercicio 4:

###### Consulta la ayuda sobre el concepto “about_line_editing”, y contesta brevemente qué tipo de ayuda incorpora este concepto. ¿Qué se consigue exactamente con las siguientes combinaciones de teclas?

###### 		a) CTRL + Cursor izquierdo.

```
key. To move the cursor one word to the left, press CTRL+LEFT ARROW
- Para mover el cursor una palabra hacia la izquierda
```

###### 		b) CTRL + cursor derecho.

```
key. To move the cursor one word to the right, press CTRL+RIGHT ARROW
- Para mover el cursor una palabra hacia la derecha
```

###### 		c) CTRL + Fin.

```
To delete all the characters in the line after the cursor, press CTRL+END.
- Para eliminar todos los caracteres en la línea después del cursor
```

###### 		d) Tabulador.

```
To complete a command, such as the name of a cmdlet, a cmdlet parameter, or a path
- Para completar un comando, como el nombre de un cmdlet, un cmdlet parámetro, o una ruta
```



### Ejercicio 5:

###### Utiliza la ayuda sobre el cmdlet “New-Alias” (y en particular, la ayuda que incluye ejemplos de uso) para averiguar cómo crear nuevos alias para un cmdlet existente. A continuación, crea un alias del cmdlet “Get-Childitem” denominado “l”. Crea otros alias a tu gusto para alguno de los cmdlets que hayas utilizado hasta ahora.

```
PS C:\Windows\system32> New-Alias -Name "uno" -value Get-ChildItem
```

```
Alias           type -> Get-Content
Alias           uno -> Get-ChildItem  <<<<<<<<<<<<<<<<<<<
Alias           wget -> Invoke-WebRequest
Alias           where -> Where-Object
Alias           wjb -> Wait-Job
Alias           write -> Write-Output
```
