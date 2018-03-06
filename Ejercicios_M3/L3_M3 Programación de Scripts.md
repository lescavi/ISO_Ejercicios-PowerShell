# | WINDOWS POWERSHELL |

## - EJERCICIOS M3 L3 -

### Ejercicio 1:

###### Crea un script que averigüe cual es el mayor de tres números. Para ello:

1. ###### Crea tres variables, asignando a cada una un número. 


```
$a = 5
$b = 9
$c = 4
```

2. ###### Con una sola sentencia "if", muestra el valor de la variable cuyo valor sea superior al de las otras dos variables.

```
$a = 5
$b = 2
$c = 9

if ($a -gt $b -and $a -gt $c) {
Write-Host - El nº mayor es: $a
}
elseif ($b -gt $a -and $b -gt $c) {
Write-Host - El nº mayor es: $b
}
else{
Write-Host - El nº mayor es: $c
}
```

```
PS C:\Windows\system32> C:\Users\Lescavi\Downloads\Scripts\Ejercicios M3.ps1
- El nº mayor es: 10
```

### Ejercicio 2:

###### Crea un script que dado un color del arcoíris muestre su número de orden.

1. ###### Crea una variable y asígnale un color


2. ###### Con una sentencia switch, compara el valor de la variable anterior con todos los colores del arcoíris para averiguar su número de orden.


3. ###### Muestra el número de orden.


4. ###### Informa acerca de colores que no existan en el arcoíris.


```
$color = Read-Host

Switch ($color)
{
"Rojo" {Write-Host "Color nº: 1"}
"Naranja" {Write-Host "Color nº: 2"}
"Amarillo" {Write-Host "Color nº: 3"}
"Verde" {Write-Host "Color nº: 4"}
"Celeste" {Write-Host "Color nº: 5"}
"Azul" {Write-Host "Color nº: 6"}
"violeta" {Write-Host "Color nº: 7"}
Default {Write-Host "¡Este color no pertenece al Arco Iris!"}
}
```


`AYUDA: Puedes buscar "arcoíris" en Wikipedia para consultar el órden de los colores`



### Ejercicio 3:

###### Crea un script que concatene en orden inverso una lista de strings.

1. ###### Crea una variable y asígnale una lista de strings (separados por comas).


```
$c1 = "a","b","c","d","e","f"
```

2. ###### Crea otra variable asignándole un string nulo. La utilizarás para ir construyendo la concatenación de la lista de strings.


```
$c1 = "a","b","c","d","e","f"
$c2 = ""
```

3. ###### Con una sentencia foreach, itera sobre el array creado en el paso anterior, concatena el string en curso al principio del string que has ido construyendo previamente.


```
$c1 = "a","b","c","d","e","f"
$c2 = ""
foreach ($x in $c1)
{
$c2 = $x + $c2
}
Write-Host $c2
```

4. ###### Finalmente muestra el string.


```
PS C:\Windows\system32> $c2
fedcba
```

`AYUDA: Puedes concatenar strings utilizando el operador +`


### Ejercicio 4:

###### Crea un script que muestre las librerías de enlace dinámico (ficheros con extensión .dll) del directorio c:\windows\system32 cuyo tamaño sea superior a 10 Mb.

- ###### Utiliza el cmdlet `ForEach-Object` para procesar el resultado de ejecutar `Get ChildItem "C:\windows\System32\*.dll"`

`AYUDA: Get-ChildItem devuelve objetos en los que la propiedad .Length indica la longitud en bytes del fichero y la propiedad .Name su nombre`

```
$str = Get-ChildItem C:\windows\System32\*.dll
foreach ($x in $str){
if ($x.Length -gt 10240){

echo $x
}

}
```
