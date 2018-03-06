# | WINDOWS POWERSHELL |

## - EJERCICIOS M3 L5 -

### Ejercicio 2:

###### Codifica un script que defina:

1. ###### Que averigüe los números impares y pares entre dos dados como variables.


2. ###### Imprima "El número X es impar"

3. ###### Por defecto, la primera variable vale 1 y la segunda 7.

```
$a = 1
$b = 7

if ($a %2 -eq 0){
Write-Host $a "Es par"
}
else {
Write-Host $a "Es impar"
}
if ($b %2 -eq 0){
Write-Host $b "Es par"
}
else {
Write-Host $b "Es impar"
}
```

###### A continuación, tu script debería llamar con varios juegos de argumentos, probando casos distintos, para comprobar su correcto funcionamiento.

```
$a = Read-Host "Introduce un número: "

if ($a %2 -eq 0){
Write-Host $a "Es par"
}
else {
Write-Host $a "Es impar"
}
```