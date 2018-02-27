# -- WINDOWS POWERSHELL --

## - EJERCICIOS M3 L2 -

### Ejercicio 1:

###### Crea un script que calcule la suma de los volúmenes de dos cubos.

1. ###### Crea dos variables, asignando a cada una la longitud del lado de cada cubo.


```
$l1 = 3
$l2 = 4

Write-Host Lado cubo1 = $l1
Write-Host Lado cubo2 = $l2
```

```
PS C:\Windows\system32> C:\Users\Lescavi\Desktop\ASIR\ISO\GIT\isolabs1-lescavi\Ejercicios_M3\Ejercicios M3.ps1
Lado cubo1 = 3
Lado cubo2 = 4
```


2. ###### Asigna a una tercera variable una expresión que sea la suma de los volúmenes de ambos cubos.


```
$l1 = 3
$cl1 = ($l1*$l1*$l1)
$l2 = 4
$cl2 = ($l2*$l2*$l2)
$s = ($l1*$l1*$l1)+($l2*$l2*$l2)
```

```
PS C:\Windows\system32> C:\Users\Lescavi\Desktop\ASIR\ISO\GIT\isolabs1-lescavi\Ejercicios_M3\Ejercicios M3.ps1
Lado cubo1 = 3
Área de cubo1 = 27
Lado cubo2 = 4
Área de cubo2 = 64
Suma del área de ambos cubos = 91
```


3. ###### Muestra el valor de la tercera variable. 


```
PS C:\Windows\system32> $s
91
```

### Ejercicio 2:

###### Crea un script que compruebe si un número es estrictamente mayor que otros dos.

1. ###### Asigna un primer número a una variable.


```
$a = 2

Write-Host $a
```

2. ###### Asigna otros dos números a otras dos variables.


```
$a = 2
$b = 3
$c = 4

Write-Host $a
Write-Host $b
Write-Host $c
```

3. ###### Asigna a una cuarta variable una expresión que compruebe si el primer número es mayor que los otros dos.


```
$a = 2
$b = 3
$c = 4
$m = ($a -gt $b) -and ($a -gt $c)

Write-Host - Nº a comparar = $a
Write-Host - Nº a comparar = $b
Write-Host - Nº a comparar = $c
Write-Host - ¿a es mayor que b y c? = $m
```

```
PS C:\Windows\system32> C:\Users\Lescavi\Desktop\ASIR\ISO\GIT\isolabs1-lescavi\Ejercicios_M3\Ejercicios M3.ps1
- Nº a comparar = 2
- Nº a comparar = 3
- Nº a comparar = 4
- ¿a es mayor que b y c? = False
```

4. ###### Muestra el valor de la cuarta variable en pantalla.

```
PS C:\Windows\system32> $m
False
```

