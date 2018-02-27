# -- WINDOWS POWERSHELL --

## - OBJETOS Y VARIABLES -

### Ejercicio 1:

###### Ejecuta cada uno de los siguientes cmdlets en la consola:

###### A continuación, utiliza el cmdlet Get-Member para averiguar el tipo de objeto que devuelve cada una de esas ejecuciones, y compáralo con la salida obtenida previamente. ¿A qué tipo de elemento real del sistema crees que corresponde cada uno?

###### a) Get-Date

```
PS C:\Users\Lescavi> Get-Date

lunes, 5 de febrero de 2018 9:57:42
```

```
PS C:\Users\Lescavi> Get-Member -InputObject (Get-Date)


   TypeName: System.DateTime
```

###### b) Get-Location

```
PS C:\Users\Lescavi> Get-Location

Path
----
C:\Users\Lescavi
```

```
PS C:\Users\Lescavi> Get-Member -InputObject (Get-Location)


   TypeName: System.Management.Automation.PathInfo
```

###### c) Get-Alias cd

```
PS C:\Users\Lescavi> Get-Alias cd

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           cd -> Set-Location
```

```
PS C:\Windows\system32> Get-Member -InputObject (Get-Alias)


   TypeName: System.Object[]
```

###### d) Get-ChildItem c:\Windows\explorer.exe

```
PS C:\Users\Lescavi> Get-ChildItem C:\Windows\explorer.exe


    Directorio: C:\Windows


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       12/07/2017      7:55        4674872 explorer.exe
```

```
PS C:\Windows\system32> Get-Member -InputObject (Get-ChildItem)


   TypeName: System.Object[]
```

###### e) Get-Process system

```
PS C:\Users\Lescavi> Get-Process System

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
   1348       0      132       2284      73,58      4   0 System
```

```
PS C:\Windows\system32> Get-Member -InputObject (Get-Process)


   TypeName: System.Object[]
```

###### f) Get-Service w32time

```
PS C:\Users\Lescavi> Get-Service W32Time

Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Hora de Windows
```
```
PS C:\Windows\system32> Get-Member -InputObject (Get-Service)

   TypeName: System.Object[]
```



### Ejercicio 2:

###### En primer lugar, ejecuta el siguiente cmdlet:

​					`Set-Location c:\Windows`

```
PS C:\Windows\system32> Set-Location c:\Windows
PS C:\Windows>
```

###### Comprueba que efectivamente la ruta actual es la indicada, ejecutando Get-Location. A continuación, diseña cmdlets (o expresiones) para obtener la información siguiente, y compruébalas en la consola:

```
PS C:\Windows> Get-Location

Path
----
C:\Windows
```

###### a) Los nombres de las propiedades del objeto devuelto por Get-Location.

```
PS C:\Windows> Get-Member -InputObject (Get-Location) -MemberType Properties


   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

###### b) El valor actual de cada una de dichas propiedades.

```
PS C:\Windows> Get-Member -InputObject (Get-Location) -MemberType Properties -Name Drive


   TypeName: System.Management.Automation.PathInfo

Name  MemberType Definition
----  ---------- ----------
Drive Property   System.Management.Automation.PSDriveInfo Drive {get;}
```

```
PS C:\Windows> Get-Member -InputObject (Get-Location) -MemberType Properties -Name Path


   TypeName: System.Management.Automation.PathInfo

Name MemberType Definition
---- ---------- ----------
Path Property   string Path {get;}
```

```
PS C:\Windows> Get-Member -InputObject (Get-Location) -MemberType Properties -Name Provider


   TypeName: System.Management.Automation.PathInfo

Name     MemberType Definition
----     ---------- ----------
Provider Property   System.Management.Automation.ProviderInfo Provider {get;}
```

```
PS C:\Windows> Get-Member -InputObject (Get-Location) -MemberType Properties -Name ProviderPath


   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
ProviderPath Property   string ProviderPath {get;}
```



### Ejercicio 3:

###### En primer lugar, lanza el bloc de notas de Windows, ejecutando en la consola.

​							`notepad.exe`

```
PS C:\Windows> notepad.exe
PS C:\Windows>
```

###### Vuelve a la consola (sin cerrar el bloc de notas), y utiliza `Get-Process` para comprobar que efectivamente existe un proceso que ejecuta este programa. A continuación, ejecuta en la consola cmdlets (o expresiones) para conseguir lo siguiente:

```
PS C:\Windows> Get-Process -Name notepad

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    180      11     2528      12428       0,19    212   3 notepad
```

###### a) Obtener los nombres de los métodos del objeto devuelto por Get-Process notepad (NOTA: Asegúrate que sólo hay un proceso bloc de notas en ejecución; si hay más de uno, la salida de este cmdlet no será la adecuada).

```
PS C:\Windows> Get-Member -InputObject (Get-Process notepad) -MemberType Method


   TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     void BeginErrorReadLine()
BeginOutputReadLine       Method     void BeginOutputReadLine()
CancelErrorRead           Method     void CancelErrorRead()
CancelOutputRead          Method     void CancelOutputRead()
Close                     Method     void Close()
CloseMainWindow           Method     bool CloseMainWindow()
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type requestedType)
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Equals                    Method     bool Equals(System.Object obj)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Kill                      Method     void Kill()
Refresh                   Method     void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), void WaitForExit()
WaitForInputIdle          Method     bool WaitForInputIdle(int milliseconds), bool WaitForInputIdle()
```

###### b) De entre los métodos anteriores, invocar aquel que termina (“mata”) el proceso sobre el objeto anterior. En ese momento, el bloc de notas debe cerrarse automáticamente.

```
PS C:\Windows> (Get-Process notepad).Kill()
PS C:\Windows>
```



### Ejercicio 4:

###### En la consola, asigna a las variables siguientes los valores iniciales especificados en la tabla que se muestra a continuación, en el orden en que aparecen:

| Variable | Valor Inicial                                 |
| -------- | --------------------------------------------- |
| $num     | 1000                                          |
| $cadena1 | “En un lugar de la Mancha”                    |
| $cadena2 | “de cuyo nombre no quiero acordarme”          |
| $fecha   | Get-Date                                      |
| $file    | get-childitem c:\Windows\System32\Notepad.exe |
| $proceso | Start-Process $file -Passthru                 |

###### A continuación, resuelve cada uno de los ejercicios siguientes mediante un cmdlet o expresión que resulte adecuado, y ejecútalo en la consola para comprobarlo:

###### a) Suma 2000 a `$num`, y guarda el resultado en  `$num2`.

```
PS C:\Windows\system32> $num2=$num+2000
```

###### b) Visualiza en pantalla el valor de `$num2`.

```
PS C:\Windows\system32> $num2
3000
```

###### c) Inicializa la variable `$cadena3` como suma de `$cadena1`,  una cadena con un espacio en blanco y `$cadena2`.

```
PS C:\Windows\system32> $cadena3=$cadena1+" "+$cadena2
```

###### d) Obtén el tipo de objeto de `$cadena3`, así como sus propiedades y métodos.

```
PS C:\Windows\system32> $cadena3
En un lugar de la mancha de cuyo nombre no quiero acordarme
```

###### e) Localiza de entre las propiedades del ejercicio anterior una que devuelve la longitud de una cadena, y utilízala para averiguar la longitud de `$cadena3`.

```
PS C:\Windows\system32> $cadena3.Length
59
```

###### f) Localiza de entre los métodos del ejercicio c) uno que subdivide la cadena en subcadenas. Utiliza este método con la variable `$cadena3` en una expresión que muestre en pantalla su subdivisión en palabras.

###### `(NOTA: Este método, invocado sin parámetros, divide la cadena en subcadenas al encontrar el carácter “espacio en blanco”).`

```
PS C:\Windows\system32> $cadena3.Split(" ")
En
un
lugar
de
la
mancha
de
cuyo
nombre
no
quiero
acordarme
```

###### g) Visualiza en pantalla el contenido de `$fecha`.

```
PS C:\Windows\system32> $fecha

sábado, 10 de febrero de 2018 17:57:40
```

###### h) Localiza entre los miembros de `$fecha` la propiedad que representa el día (del mes), y escribe una expresión que sume 40 al valor de esta propiedad de `$fecha`.

```
PS C:\Windows\system32> $fecha=$fecha.Day+40
PS C:\Windows\system32> $fecha
50
```

###### i) Localiza entre los miembros de `$fecha` el método que permite añadir un número de días a una fecha. Invoca este método sobre `$fecha`, con 40 como argumento.

```
PS C:\Windows\system32> $fecha.AddDays(40)

jueves, 22 de marzo de 2018 19:05:39
```

###### ¿En qué se diferencia este resultado del obtenido en el apartado anterior?

`En el apartado h) la cantidad añadida se suma al resultado obtenido. Al sumar 40 muestra el resultado que da dicha suma.`
`En el apartado i) la suma da como resultado mostrar el dia/mes/año que corresponde. Lo suma como si fueran dias y muestra la fecha que da como resultado.`

###### j) Visualiza por pantalla el valor de `$proceso`. A continuación, escribe una expresión que visualice el identificador interno del proceso representado por la variable `$proceso`, utilizando la propiedad que expresa este identificador.

```
PS C:\Windows\system32> $proceso

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    174      12     2876      12308       0,14   2332   4 notepad
```

```
PS C:\Windows\system32> $proceso.Id
2332
```

###### k) Utiliza el método adecuado sobre la variable `$proceso` para finalizar la ejecución del proceso representado por esta variable.

```
PS C:\Windows\system32> $proceso.Kill()
```



### Ejercicio 5:

###### En el ejercicio anterior, la variable $proceso se ha inicializado mediante la salida del cmdlet Start-Process. Averigua el papel que juega el parámetro PassThru en esta invocación. ¿Qué habría ocurrido si no se hubiera utilizado?

```
PS C:\Windows\system32> Start-Process c:\Windows\System32\Notepad.exe
```

`Ejecuta notepad sin mostrar el proceso ejecutado por pantalla.`



```
PS C:\Windows\system32> Start-Process c:\Windows\System32\Notepad.exe -Passthru

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
     22       4      908       2160       0,11   8728   4 notepad
```

`Ejecuta notepad mostrando el proceso ejecutado en pantalla.`