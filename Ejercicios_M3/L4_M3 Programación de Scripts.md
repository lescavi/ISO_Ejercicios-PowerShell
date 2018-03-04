# -- WINDOWS POWERSHELL --

## - EJERCICIOS M3 L4 -

###### Crea pequeños scripts iguales o similares a los de las transparencias y comprueba su funcionamiento. Haz especial hincapié en aspectos como la codificación de sentencias en más de una línea, el uso de subexpresiones y la evaluación de variables y subexpresiones dentro de strings, ya que en estos aspectos es donde PowerShell difiere más de los lenguajes de programación de propósito general.

## - TIPOS Y OPERADORES -

- #### MI PRIMER SCRIPT.

```
$n = "Javier"

Write-Host "Mi primer script"
Write-Host Mi nombre es $n
```

1. #### TIPOS

```
$a = 1 <<<<<<<< Entero
$b = "Hola" <<<<<<<< String
$c = 5,6,7,8 <<<<<<<< Array
$d = $true <<<<<<<< Booleano
$e = @{Nombre = "Valor"; Pelo = "rubio"; Sexo = "varón"} <<<<<<<< Hash
$f = Get-Date <<<<<<<< Tipo .NET
```

###### Método `GetType()`

```
$a = 1
$b = "Hola"
$c = 5,6,7,8
$d = $true
$e = @{Nombre = "Valor"; Aquí_ponemos_el_nombre = "Aquí su valor"; color = "verde"; forma = "circulo"; pelo = "rubio"; sexo = "Varón"}
$f = Get-Date

Write-Host "Esto es un número: "$a
Write-Host $a.GetType().name
Write-Host "Esto es un String: "$b
Write-Host $b.GetType().name
Write-Host "Esto es una ARRAY (Una serie de elementos del mismo tipo): "$c
Write-Host $c.GetType().name
Write-Host "Este  es del tipo Booleano (Sólo admite 2 respuestas true/false): "$d
Write-Host $d.GetType().name
Format-Table -inputObject $e
Write-Host $e.GetType().name
Write-Host $f
Write-Host $f.GetType().name
```

```
$a = 1
$b = "Hola"
$c = 5,6,7,8
$d = $true
$e = @{$a.GetType().name = $a; $b.GetType().name = $b; $c.GetType().name = $c; $d.GetType().name = $d; $e.GetType().name = $e; $f.GetType().name = $f;}
$f = Get-Date
Format-Table -inputObject $e
```

###### Restringiendo el tipo de variable.

```
[string]$d1 = "Hola"
[datetime]$d2 = "01/01/2001"
[int]$d3 = 1999

$d1 = "Esto es un string"
$d2 = "Esto tiene formato fecha"
$d3 = "123456"

Write-Host $d1 "Tipo:"$d1.GetType().Name
Write-Host $d2 "Tipo:"$d2.GetType().Name
Write-Host $d3 "Tipo:"$d3.GetType().Name
```

2. #### OPERADORES ARITMÉTICOS

```
$a = 3 + 6
$b = 8 - 2
$c = 6 * 4
$d = 21 / 3

Write-Host "Suma: 3 + 6 ="$a
Write-Host "Resta: 8 - 2 ="$b
Write-Host "Multiplicación: 6 x 4 ="$c
Write-Host "División: 21 : 3 ="$d
```

3. #### OPERADORES DE ASIGNACIÓN

```
$a = 2
$b = 2; $b++
$c = 2; $c--
$d = 2; $d += 5
$e = 2; $e -= 5
$f = 10; $f *= 2
$g = 10; $g /= 2
$h = 10; $h %= 3

Write-Host "Se asigna un valor fijo a una variable: "$a
Write-Host "Incrementa el valor en uno: "$b
Write-Host "Decrementa el valor en uno: "$c
Write-Host "Incrementa el valor sumando (x): "$d
Write-Host "Decrementa el valor restando (x): "$e
Write-Host "Multiplica el valor por (x): "$f
Write-Host "Divide el valor entre (x): "$g
Write-Host "Devuelve el resto de una división: "$h
```

4. #### OPERADORES DE COMPARACIÓN

```
$a = 1 -eq 1
$b = 2 -gt 1
$c = 3 -lt 4
$d = 1 -ge 1
$e = 1 -le 1
$f = "hola" -like "*ola"
$g = "adiós" -NotLike "*ola"
$h = "cara" -Match ".a.a"
$i = "caro" -NotMatch ".a.a"

Write-Host "(-eq) Es igual a...: " $a "(=)"
Write-Host "(-gt) Es mayor que...: " $b "(>)"
Write-Host "(-lt) Es menor que...: " $c "(<)"
Write-Host "(-ge) Es mayor o igual que...: " $d "(>=)"
Write-Host "(-le) Es menor o igual que...: " $e "(<=)"
Write-Host "Buscan coincidencias:"
Write-Host $f
Write-Host $h
Write-Host "Buscan lo que no coincide:"
Write-Host $g
Write-Host $i
```

5. #### OPERADORES LÓGICOS


```
$a = (1 -eq 1) -and (2 -eq 2)
$aa = (1 -eq 1) -and (2 -eq 9)

$b = (2 -gt 1) -or (1 -eq 5)
$bb = (2 -gt 6) -or (1 -eq 5)

$c = (1 -lt 2) -xor (1 -eq 5)
$cc = (3 -lt 2) -xor (1 -eq 5)

$d = -not (1 -eq 5)
$dd = -not (1 -eq 1)

$e = ! (1 -eq 5)
$ee = ! (1 -eq 1)

Write-Host 
Write-Host "-and (y): Se tiene que complir ambas condiciones" = $a
Write-Host "-and (y): Se tiene que complir ambas condiciones" = $aa
Write-Host
Write-Host "-or (ó): Se tiene que complir una de las 2 condiciones" = $b
Write-Host "-or (ó): Se tiene que complir una de las 2 condiciones" = $bb
Write-Host
Write-Host "-xor (una/o de): No se tiene que complir una de las 2 condiciones" = $c
Write-Host "-xor (una/o de): No se tiene que complir una de las 2 condiciones" = $cc
Write-Host
Write-Host "-not (no): No se tiene que complir la condición" = $d
Write-Host "-not (no): No se tiene que complir la condición" = $dd
Write-Host
Write-Host "! (distinto): Distinto de" = $e
Write-Host "! (distinto): Distinto de" = $ee
```

6. #### OPERADORES SOBRE STRINGS

```
$a = "perro-gato-pájaro-pez-perro-flauta" -split "-", 5;
$b = "a","b","c" -join "-"
$bb = "a","b","c" -join ""
$bbb = "a","b","c"

Write-Host
Write-Host "Cuenta string separados por (-)" = $a.Length $a
Write-Host "El 5 delimita los string a contar. Le dice que el 5º y 6º string van juntos"
Write-Host "---------------------------------------------"
Write-Host "Separamos los string con el carácter (-):" $b
Write-Host "No ponemos carácter, no separa. Lo muestra todo junto:" $bb
Write-Host "Si no ponemos (-join) lo separa con un espacio por defecto:" $bbb
```

###### Más información: (Mas consultas)

```
`get-help`
	`about_arithmetic_operators`
	`about_assignment_operators`
	`about_comparison_operators`
	`about_Logical_Operators`
	`about_Split`
	`about_Join`	
```

​	



## - ESTRUCTURAS DE CONTROL -

1. #### ESTRUCTURAS DE SELECCIÓN

###### Sentencia `if`

```
Write-Host
Write-Host - "(if + condición) Es como preguntar ""si..."" (se cumple, muestra...)"
Write-Host - "(elseif + condición) Es como preguntar ""o esta..."" (si no se cumple la anterior, comprueba esta otra...)"
Write-Host - "(else) Es como preguntar ""si no..."" (si no cumple ninguna, muestra esta...)"
Write-Host

if (1 -eq 2)
{
Write-Host "Resultado: 1ª alternativa"
}
elseif (2 -gt 1){
Write-Host "Resultado: 2ª alternativa"
}
else {
Write-Host "Resultado: 3ª alternativa"
}
```

###### Sentencia `swich`

```
switch (3){

1 {Write-Host "Es uno"} 
2 {Write-Host "Es dos"}
3 {Write-Host "Es tres"}
4 {Write-Host "Es cuatro"}
3 {Write-Host "Es cinco menos dos"}

}
```

```
Write-Host
Write-Host "(break) fuerza la terminación de la sentencia ""switch"""
Write-Host

switch (3) {

1 {Write-Host "- Es uno"} 
2 {Write-Host "- Es dos"}
3 {Write-Host "- Es tres"; break}
4 {Write-Host "- Es cuatro"}
3 {Write-Host "- Es cinco menos dos"}

}
```

```
Write-Host
Write-Host "(Default) se ejecuta si no se cumple ninguna de las otras condiciones"
Write-Host

switch (24) {

1 {Write-Host "- Es uno"} 
2 {Write-Host "- Es dos"}
3 {Write-Host "- Es tres"}
4 {Write-Host "- Es cuatro"}
3 {Write-Host "- Es cinco menos dos"}
Default {Write-Host "- ¡ Es otro valor !"}

}
```

```
Write-Host
Write-Host "(-Wildcard) Cuando se comparan string, pueden usarse carácteres comodín"
Write-Host
switch -Wildcard ("cara") {

"cor*" {Write-Host "- Empieza por ""cor"""} 
"cer*" {Write-Host "- Empieza por ""cer"""}
"car*" {Write-Host "- Empieza por ""car"""}

Default {Write-Host "- ¡ Es otro valor !"}

}
```

```
Write-Host
Write-Host "(-Regex) También es posible utilizar expresiones regulares"
Write-Host
switch -Regex ("coro") {

"^c,*r*,*o" {Write-Host "- Empieza por ""c"", tiene una ""r"" y acaba en ""o"""} 
"^c,*r*,*a" {Write-Host "- Empieza por ""c"", tiene una ""r"" y acaba en ""a"""}

Default {Write-Host "- ¡ Es otro valor !"}

}
```

2. #### ESTRUCTURAS DE ITERACIÓN

###### Sentencia `while`

```
Write-Host
Write-Host "Sentencia: while"
Write-Host

$a = 0

while ($a -lt 5) {
Write-Host $a
$a++

}
Write-Host
Write-Host "Resultado: ""Mientras"" el valor de la variable sea menor que 5, este incrementa en 1 y muestra el siguente"
```

###### Sentencia `for`

```
Write-Host
Write-Host "Sentencia: for"
Write-Host
Write-Host "* En este caso la variable la declaramos dentro del ""for"""
Write-Host

for ($a = 0; $a -lt 5; $a++){
Write-Host $a
}
Write-Host
Write-Host "Resultado: ""Para"" que el valor de la variable se muestre, este ha de ser menor de 5 e irá incrementando en 1, luego repite el bucle"

```

###### Sentencia `do`

```
Write-Host
Write-Host "Sentencia: do"
Write-Host

$a = 0
do {
    Write-Host $a
    $a++
} while ($a -lt 5)

Write-Host 
Write-Host "Resultado: (do + while) Hace/muestra el resultado de la variable, incrementando en 1, mientras sea menor de 5"
Write-Host

$a = 20
do {
    Write-Host $a
    $a++
} while ($a -lt 5)

Write-Host 
Write-Host "Resultado: (do + while) Si es mayor que 5 sólo pinta el valor"
Write-Host

$a = 0
do {
    Write-Host $a
    $a++
} until ($a -eq 5)

Write-Host 
Write-Host "Resultado: (do + until) Hace/muestra el resultado de la variable, incrementando en 1, mientras ""NO"" sea igual a 5"
Write-Host
```

###### Sentencia `foreach`

```
Write-Host
Write-Host "Sentencia: foreach"
Write-Host

$colores = @("amarillo", "azul", "rojo", "verde")
foreach ($c in $colores) {
    Write-Host $c
}
Write-Host
Write-Host "Resultado: ""Para cada"" elemento almacenado en el array, lo almacena de nuevo en otra variable y muestra el contenido de la nueva variable"
```

###### Sentencia `break`

```
Write-Host
Write-Host "Sentencia: foreach + break"
Write-Host

$colores = @("amarillo", "azul", "rojo", "verde")
foreach ($c in $colores) {
    Write-Host $c
    if ($c -eq "rojo") {break}
}
Write-Host
Write-Host "Resultado: ""Para cada"" elemento almacenado en el array, lo almacena de nuevo en otra variable y muestra el contenido de la nueva variable"
Write-Host
Write-Host "* (break) fuerza la terminación de la sentencia cuando encuentra la coincidencia ""rojo"""
```

3. #### Cmdlet ForEach-Object

###### Cmdlet ForEach-Object

```
Write-Host
Write-Host "Cmdlet: ForEach-Object"
Write-Host

$colores = @("amarillo", "azul", "rojo", "verde")
Write-Output $colores | ForEach-Object {
Write-Host $_
}

Write-Host
Write-Host "Resultado: ""Para cada objeto"" se realiza una operación contra cada elemento en una colección de objetos de entrada, adquiriendo el valor de la propiedad del objeto."
```

###### Mas información:

```
`get-help`
​	`about_If`
​	`about_Switch`
​	`about_While`
​	`about_For`
​	`about_Do`
​	`about_Foreach`
​	`about_Break`
​	`ForEach-Object`
```



## - SINTAXIS -

