# -- WINDOWS POWERSHELL --

## - Sintaxis de los mandatos -

### Ejercicio 1:

###### A continuación se presenta la sintaxis del cmdlet `Clear-History`, tal como se muestra en la ayuda en línea de PowerShell:

```
Parameter Set: ID
Clear-History [[-Id] <Int32[]> ] [[-Count] <Int32> ]
[-Newest] [-Confirm] [-WhatIf] [<CommonParameters>]
```

```
Parameter Set: CommandLine
Clear-History [[-Count] <Int32> ] [-CommandLine <String[]> ]
[-Newest] [-Confirm] [-WhatIf] [<CommonParameters>]
```

###### Consultando la ayuda siempre que lo necesites, contesta las siguientes preguntas:

###### a) ¿Qué acción realiza este cmdlet en el sistema? Describe brevemente.

`Elimina entradas del historial de comandos.`

###### b) Explica brevemente en qué se diferencia el funcionamiento del cmdlet en ambos conjuntos de parámetros, y pon un ejemplo en cada caso.

```
PS C:\Windows\system32> Clear-History -Id
```

`	Especifica los ID de historial de los comandos que elimina este cmdlet.`

```
PS C:\Windows\system32> Clear-History -CommandLine
```

`	Especifica los comandos que este cmdlet elimina. Si ingresas más de una cadena, Clear-History elimina los comandos que tienen cualquiera de las cadenas.`

###### c) ¿Existe algún parámetro obligatorio en alguno de ambos conjuntos de parámetros? En caso afirmativo, identifícalos. En caso negativo, explica qué consecuencia tiene este hecho.

 ```
PS C:\Windows\system32> Clear-History -Id
 ```
​			`Falta el argumento <Int32[]> <<<<<<<<<<< obligatorio`
 ```
PS C:\Windows\system32> Clear-History -CommandLine
 ```

​			`Falta el argumento <String[]> <<<<<<<<<<< obligatorio`

###### d) Identifica los parámetros considerados conmutadores.

`[-Confirm] [-Newest] [-WhatIf]`

###### e) Clasifica cada uno de los siguientes parámetros en obligatorio u opcional, y en posicional o no posicional: -Id, -Count, -Commandline, -Newest.

`-ID -> opcional, no posicional`
`-Count -> opcional, posicional` 
`-Commandline -> opcional, no posicional`
`-Newest -> opcional, no posicional` 

###### f) Si invocamos el cmdlet de la siguiente forma: `Clear-History 15 5` ¿Se trata de una invocación correcta o errónea? ¿A qué parámetros corresponderían los valores 15 y 5? Justifica tus respuestas.

`Correcta`
`-ID -> opcional, no posicional`
`Elimina del histórico el id nº15 + los 4 anteriores (del 15)`

###### g) Si invocamos el cmdlet de la siguiente forma: `Clear-History 10 –CommandLine get*` ¿Se trata de una invocación correcta o errónea? ¿A qué parámetro correspondería el valor 10? Justifica tus respuestas.

`Es correcta.`
`El valor 10 es el "ID" del comando 10.`
`Elimina todos los comandos que empiecen por get.`

###### h) Si invocamos el cmdlet de la siguiente forma: `Clear-History 20 8 –CommandLine get*` ¿Se trata de una invocación correcta o errónea? ¿A qué parámetros corresponderían los valores 20 y 8? Justifica tus respuestas.

`No es correcta.`
`20 corresponde al parametro "ID" y 8 al count por lo que no se puede utlizar -commandline.`

### Ejercicio 2:

###### A continuación se presenta la sintaxis del cmdlet Clear-Content, tal como se muestra en la ayuda en línea de PowerShell (NOTA: Para simplificar la pregunta, se han eliminado algunos parámetros no relevantes):

```
Parameter Set: Path
Clear-Content [-Path] <String[]> [-Credential <PSCredential> ]
[-Exclude <String[]> ] [-Filter <String> ] [-Force]
[-Include <String[]> ] [-Confirm] [-WhatIf] [-UseTransaction]
[<CommonParameters>]
```

```
Parameter Set: LiteralPath
Clear-Content -LiteralPath <String[]> [-Credential <PSCredential> ]
[-Exclude <String[]> ] [-Filter <String> ] [-Force]
[-Include <String[]> ] [-Confirm] [-WhatIf] [-UseTransaction]
[ <CommonParameters>]
```

###### a) ¿Qué acción realiza este cmdlet en el sistema? Describe brevemente.

`Elimina el contenido de un elemento, pero no elimina el elemento.`

`El cmdlet Clear-Content elimina el contenido de un elemento, elimina el texto de un archivo, pero no elimina el elemento. Como resultado, el artículo existe, pero está vacío. El Clear-Content es similar a Clear-Item, pero funciona en elementos con contenido, en lugar de elementos con valores.`

###### b) Explica brevemente en qué se diferencia el funcionamiento del cmdlet en ambos conjuntos de parámetros, y pon un ejemplo en cada caso.

`-path:  Se introduce la ruta del documento cuyo contenido queremos borrar`

`-literalpath: Se introduce la ruta exactamente como se ha escrito, no se interpretan los caracteres comodin, si los hay, se introducen entre comillas simples.`

###### c) ¿Existe algún parámetro obligatorio en alguno de ambos conjuntos de parámetros? En caso afirmativo, identifícalos. En caso negativo, explica qué consecuencia tiene este hecho.

`No hay ningun campo obligatorio.`
`Pueden utilizarse los conmutadores opcionales.`
`De no utlizar ninguno, solicitará introducir un documento de la localizacion actual para borrar su contenido.`

###### d) Identifica los parámetros considerados conmutadores.

`[-Confirm] [-Force] [-UseTransaction] [-WhatIf]`

###### e) Clasifica cada uno de los siguientes parámetros en obligatorio u opcional, y en posicional o no posicional: -Path, -Credential, -LiteralPath, -Confirm.

`-Path: Opcional, no posicional`
`-Credential: Opcional, no posicional`
`-LiteralPath: Opcional, posicional`
`-Confirm: Opcional, no posicional`

###### f) Si invocamos el cmdlet de la siguiente forma: `Clear-Content c:\Datos\Dato1.txt` ¿Se trata de una invocación correcta o errónea? ¿A qué parámetro correspondería el valor “c:\Datos\Dato1.txt”? Justifica tus respuestas.

`Es correcta.`
`Corresponde al parametro -path`