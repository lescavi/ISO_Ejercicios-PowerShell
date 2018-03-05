# | WINDOWS POWERSHELL |

## - EJERCICIOS M3 L6 -

### Ejercicio 1:

###### Codifica un script que realice lo siguiente:

1. ###### Cree una variable colleción `$v` que será un array de enteros.


```
$v = @(1,16,5,48,6,9,24,4,13,3)
```

2. ###### Retorne un array en el que aparezcan en primer lugar los valores pares, ordenados de menor a mayor, y a continuación los valores impares, también ordenados de menor a mayor del array `$v`. Por ejemplo, si partimos del array 21,20,19,18,17,16 el array resultante será 16,18,20,17,19,21.

```
Write-Host
Write-Host "Números ""PARES"" de menor a mayor:"
Write-Host

$v = @(1,16,5,48,6,9,24,4,13,3) | sort

foreach ($a in $v) {
        
    if ($a %2 -eq 0){
    
    Write-Host $a

}

}
Write-Host
Write-Host "Números ""IMPARES"" de menor a mayor:"
Write-Host
foreach ($a in $v) {
    
    if ($a %2 -gt 0){
    
    Write-Host $a

}

}
```

###### A continuación, tu script debería llamar a dicha función con varios juegos de argumentos, probando casos distintos, para comprobar su correcto funcionamiento.



