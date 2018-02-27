# 	-- WINDOWS POWERSHELL --

## 			- CMDLETS y ALIAS -

### Ejercicio 1:

###### Utilizando Get-Command, escribe un cmdlet que resuelva cada uno de los casos siguientes en la consola:

###### 	a) Consultar todos los comandos PowerShell disponibles en el sistema. 
```
PS C:\Windows\system32> Get-Command
```

###### 	b) Consultar los comandos que comiencen por “update”.
```
PS C:\Windows\system32> Get-Command Update*
```

###### 	c) Consultar los comandos cuyo verbo de acción sea “set”.
```
PS C:\Windows\system32> Get-Command set-*
PS C:\Windows\system32> Get-Command -verb set
```

###### 	d) Consultar los comandos cuyo nombre de objeto sea “process”.
```
PS C:\Windows\system32> Get-Command *-Process
PS C:\Windows\system32> Get-Command -noun Process
```



### Ejercicio 2:

###### Uno de los parámetros de Get-Command es “-CommandType”, que permite filtrar en la consulta los diferentes tipos de comandos de PowerShell (cmdlet, alias, function). Utiliza este parámetro para repetir las dos primeras búsquedas del ejercicio anterior, pero de forma que sólo se recuperen los cmdlets.

###### 	a) Consultar todos los comandos PowerShell disponibles en el sistema.
```
PS C:\Windows\system32> get-command -CommandType Cmdlet
```

###### 	b) Consultar los comandos que comiencen por “update”.
```
PS C:\Windows\system32> Get-Command -CommandType Cmdlet Update*
```



### Ejercicio 3:

###### Utilizando Get-Alias, escribe un cmdlet que resuelva cada uno de los casos siguientes en la consola:

###### 	a) Consultar todos los alias disponibles en el sistema.
```
PS C:\Windows\system32> Get-Alias
```

###### 	b) Consultar los alias que comiencen por “c”.
```
PS C:\Windows\system32> Get-Alias c*
```

###### 	c) Consultar todos los alias del cmdlet “Clear-Host”.
```
PS C:\Windows\system32> Get-Alias -Definition Clear-Host
```

###### 	d) Consultar el cmdlet cuyo alias es “copy”
```
PS C:\Windows\system32> Get-Alias copy
```



### Ejercicio 4:

###### Escribe una secuencia de cmdlets que resuelva la siguiente secuencia de acciones:

###### 	a) Situarse en “c:\”
```
PS C:\Windows\system32> Set-Location c:\
```

###### 	b) Crear una carpeta denominada “c:\Datos”.
```
PS C:\> New-Item -ItemType Directory Datos
```

###### 	c) Situarse en “c:\Datos ”.
```
PS C:\> Set-Location C:\Datos\
```

###### 	d) Crear un fichero vacío denominado “inf1.txt”.
```
PS C:\Datos> New-Item -ItemType File inf1.txt
```

###### 	e) Añadir al fichero anterior el contenido “IES Arcipreste de Hita - ASIR1”.
```
PS C:\Datos> Add-Content .\inf1.txt "IES Arcipreste de Hita - ASIR1"
```

###### 	f) Copiar el fichero anterior a otro denominado “inf2.txt”.
```
PS C:\Datos> Copy-Item .\inf1.txt .\inf2.txt
```

###### 	g) Borrar el fichero “inf1.txt”.
```
PS C:\Datos> Remove-Item .\inf1.txt
```

###### 	h) Visualizar por pantalla el contenido del fichero “inf2.txt”.
```
PS C:\Datos> Get-Content .\inf2.txt
```

###### 	i) Ejecutar la acción por defecto sobre el fichero “inf2.txt” (abrir el bloc de notas), y modificar el contenido del fichero como prefiera.
```
PS C:\Datos> Invoke-Item .\inf2.txt
```

###### 	j) Renombrar el fichero “inf2.txt” como “inf.txt”.
```
PS C:\Datos> Rename-Item .\inf2.txt .\inf.txt
```

###### 	k) Visualizar por pantalla el fichero “inf.txt”.
```
PS C:\Datos> Get-Content .\inf.txt
```

###### 	l) Borrar el fichero “inf.txt”.
```
PS C:\Datos> Remove-Item .\inf.txt
```

###### 	m) Situarse en “c:\”
```
PS C:\Datos> Set-Location c:\
```

###### 	n) Eliminar la carpeta “c:\Datos”.
```
PS C:\> Remove-Item .\Datos\
```



### Ejercicio 5:

###### Averigua posibles alias para los cmdlets utilizados en el ejercicio anterior, y repite la misma secuencia de acciones utilizando esos alias en lugar de los cmdlets originales.

###### 	a) Situarse en “c:\”
```
PS C:\Windows\System32> Get-Alias -Definition Set-Location
CommandType     Name
-----------     ----
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           sl -> Set-Location
```

```
PS C:\Windows\system32> cd c:\
```

```
PS C:\Windows\system32> chdir c:\
```

```
PS C:\Windows\system32> sl c:\
```

###### 	b) Crear una carpeta denominada “c:\Datos”.
```
PS C:\Windows\System32> Get-Alias -Definition New-Item
CommandType     Name
-----------     ----
Alias           ni -> New-Item
```

```
PS C:\> ni -ItemType Directory Datos
```

###### 	c) Situarse en “c:\Datos ”.
```
PS C:\Windows\System32> Get-Alias -Definition Set-Location
CommandType     Name
-----------     ----
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           sl -> Set-Location
```

```
PS C:\> cd C:\Datos\
```

```
PS C:\> chdir C:\Datos\
```

```
PS C:\> sl C:\Datos\
```

###### 	d) Crear un fichero vacío denominado “inf1.txt”.
```
PS C:\Windows\System32> Get-Alias -Definition New-Item
CommandType     Name
-----------     ----
Alias           ni -> New-Item
```

```
PS C:\Datos> ni -ItemType File inf1.txt
```

###### 	e) Añadir al fichero anterior el contenido “IES Arcipreste de Hita - ASIR1”.
```
PS C:\Windows\System32> Get-Alias -Definition Add-Content
CommandType     Name
-----------     ----
Alias           ac -> Add-Content
```

```
PS C:\Datos> ac .\inf1.txt "IES Arcipreste de Hita - ASIR1"
```

###### 	f) Copiar el fichero anterior a otro denominado “inf2.txt”.
```
PS C:\Windows\System32> Get-Alias -Definition Copy-Item
CommandType     Name
-----------     ----
Alias           copy -> Copy-Item
Alias           cp -> Copy-Item
Alias           cpi -> Copy-Item
```

```
PS C:\Datos> copy .\inf1.txt .\inf2.txt
```

```
PS C:\Datos> cp .\inf1.txt .\inf2.txt
```

```
PS C:\Datos> cpi .\inf1.txt .\inf2.txt
```

###### 	g) Borrar el fichero “inf1.txt”.
```
PS C:\Windows\System32> Get-Alias -Definition Remove-Item
CommandType     Name
-----------     ----
Alias           del -> Remove-Item
Alias           erase -> Remove-Item
Alias           rd -> Remove-Item
Alias           ri -> Remove-Item
Alias           rm -> Remove-Item
Alias           rmdir -> Remove-Item
```

```
PS C:\Datos> del .\inf1.txt
```

```
PS C:\Datos> erase .\inf1.txt
```

```
PS C:\Datos> rd .\inf1.txt
```

```
PS C:\Datos> ri .\inf1.txt
```

```
PS C:\Datos> rm .\inf1.txt
```

```
PS C:\Datos> rmdir .\inf1.txt
```

###### 	h) Visualizar por pantalla el contenido del fichero “inf2.txt”.
```
PS C:\Windows\System32> Get-Alias -Definition Get-Content
CommandType     Name
-----------     ----
Alias           cat -> Get-Content
Alias           gc -> Get-Content
Alias           type -> Get-Content
```

```
PS C:\Datos> cat .\inf2.txt
```

```
PS C:\Datos> gc .\inf2.txt
```

```
PS C:\Datos> type .\inf2.txt
```

###### 	i) Ejecutar la acción por defecto sobre el fichero “inf2.txt” (abrir el bloc de notas), y modificar el contenido del fichero como prefiera.
```
PS C:\Windows\System32> Get-Alias -Definition Invoke-Item
CommandType     Name
-----------     ----
Alias           ii -> Invoke-Item
```

```
PS C:\Datos> ii .\inf2.txt
```

###### 	j) Renombrar el fichero “inf2.txt” como “inf.txt”.
```
PS C:\Windows\System32> Get-Alias -Definition Rename-Item
CommandType     Name
-----------     ----
Alias           ren -> Rename-Item
Alias           rni -> Rename-Item
```

```
PS C:\Datos> ren .\inf2.txt .\inf.txt
```

```
PS C:\Datos> rni .\inf2.txt .\inf.txt
```

###### 	k) Visualizar por pantalla el fichero “inf.txt”.
```
PS C:\Windows\System32> Get-Alias -Definition Get-Content
CommandType     Name
-----------     ----
Alias           cat -> Get-Content
Alias           gc -> Get-Content
Alias           type -> Get-Content
```

```
PS C:\Datos> cat .\inf.txt
```

```
PS C:\Datos> gc .\inf.txt
```

```
PS C:\Datos> type .\inf.txt
```

###### 	l) Borrar el fichero “inf.txt”.
```
PS C:\Windows\System32> Get-Alias -Definition Remove-Item
CommandType     Name
-----------     ----
Alias           del -> Remove-Item
Alias           erase -> Remove-Item
Alias           rd -> Remove-Item
Alias           ri -> Remove-Item
Alias           rm -> Remove-Item
Alias           rmdir -> Remove-Item
```

```
PS C:\Datos> del .\inf.txt
```

```
PS C:\Datos> erase .\inf.txt
```

```
PS C:\Datos> rd .\inf.txt
```

```
PS C:\Datos> ri .\inf.txt
```

```
PS C:\Datos> rm .\inf.txt
```

```
PS C:\Datos> rmdir .\inf.txt
```

###### 	m) Situarse en “c:\”
```
PS C:\Windows\System32> Get-Alias -Definition Set-Location
CommandType     Name
-----------     ----
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           sl -> Set-Location
```

```
PS C:\Datos> cd c:\
```

```
PS C:\Datos> chdir c:\
```

```
PS C:\Datos> sl c:\
```

###### 	n) Eliminar la carpeta “c:\Datos”.
```
PS C:\Windows\System32> Get-Alias -Definition Remove-Item
CommandType     Name
-----------     ----
Alias           del -> Remove-Item
Alias           erase -> Remove-Item
Alias           rd -> Remove-Item
Alias           ri -> Remove-Item
Alias           rm -> Remove-Item
Alias           rmdir -> Remove-Item
```

```
PS C:\> del .\Datos\
```

```
PS C:\> erase .\Datos\
```

```
PS C:\> rd .\Datos\
```

```
PS C:\> ri .\Datos\
```

```
PS C:\> rm .\Datos\
```

```
PS C:\> rmdir .\Datos\
```


