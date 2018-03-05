# | WINDOWS POWERSHELL | 

## - EJERCICIOS M3 L7 - 

## Gestión de directorios y archivos

###### En la operación de systemas (o administración), se requieren varios requisitos que están relacionados con la gestión de carpetas, tales como crearlas, borrarlas y comprobar si existen. Este tipo de acciones pueden realizarse fácilmente utilizando algunos de los cmdlets del módulo [Management](https://docs.microsoft.com/es-es/powershell/module/microsoft.powershell.management/?view=powershell-4.0) de Windows PowerShell. En los siguientes ejercicios practicarás con estas funcionalidades.

###### Es muy importante que accedas a la documentación de PowerShell, utilizando el `cmdlet Get-Help`, para obtener información sobre los `cmdlets` que necesites, así como qué parámetros son los adecuados para la tarea que te pide el ejercicio.

##  Procesar ficheros

###### Muchas veces vamos a tener que leer línea a línea ficheros de texto, ya sea en formato csv o texto y que nosotros tengamos que buscar alguna información.

###### Existen dos formas básicas para buscar en un fichero:

1. ###### Buscando en un fichero o línea. Tenemos el fichero **file1** con el siguiente contenido:

```
PS C:\Users\Administrador> Get-Content .\file1.txt
empleado, rol, proyecto
emp1,Ingeniero,ProyectoA
emp2,Operador,ProyectoB
emp3,Asistente,ProytectoA
```

###### Veamos ahora como procesar línea a línea:

* ###### Si queremos mostrar el fichero sin encabezado podemos hacer:

```
PS C:\Users\Administrador> Get-Content .\file1.txt | select -Skip 1
emp1,Ingeniero,ProyectoA
emp2,Operador,ProyectoB
emp3,Asistente,ProytectoA
```

* ###### También podemos procesar línea a línea un fichero y ...

`#Escribe línea a línea el fichero`

```
$file = Get-Content .\file1.txt

foreach($s in $file){

  Write "línea: " $s
 
}
```
`#Si queremos realizar un split en cada línea por la coma que separa cada uno de los campos`

```
$file = Get-Content .\file1.txt

foreach($s in $file){

  $s -split ","
 
}
```

#### --------------- (UPDATE) ---------------

2. ###### También existe la posibilidad de hacerlo con `Import-CSV`

```
PS C:\Users\Administrador> $file = Import-Csv .\file1.txt

PS C:\Users\Administrador> $file

empleado rol       proyecto  
-------- ---       --------  
emp1     Ingeniero ProyectoA 
emp2     Operador  ProyectoB 
emp3     Asistente ProytectoA
```

###### Y podemos acceder también así.

```
foreach($line in $file){
  $line.empleado; 
  $line.rol; 
  $line.proyecto
}
```

```
PS C:\Users\Administrador> C:\Users\Administrador\Ejercicios M3.ps1
emp1
Ingeniero
ProyectoA
emp2
Operador
ProyectoB
emp3
Asistente
ProytectoA
```

`Podemos incluso agregarlo a un vector en cada línea, las posibilidades son infinitas`

###### Ahora vamos a buscar patrones:

* ###### Utilizamos el commandlet ```select-string```

###### Por ejemplo, si queremos buscar en el fichero anterior una línea que comience por "emp" haríamos lo siguiente. 

###### Recordad que `(^)` es para comienzo de string y `($)` para finalizar string. Aunque también podemos utilizar patrones comodines `(*)` , etc.

```
PS C:\Users\Administrador> Get-Content .\file1.txt | Select-String -Pattern "^emp1"

emp1,Ingeniero,ProyectoA
```



### Como ejercicios realiza lo siguiente:

#### Ejercicio 1:

######  Tenemos el siguiente fichero contactos.txt:

```
nombre,apellidos,correo
Agustín, Espinosa Minguet, aespinos@upvnet.upv.es
Andrés, Terrasa Barrena, aterrasa@dsic.upv.es
Agustín, Marzal Navarro, amarlop@miempresa.com
```

1. ###### Necesitamos crear un script que pueda buscar el nombre de un usuario mediante entrada por teclado. El script debe pedirnos dicho nombre de teclado. 

   ###### a 



2. ###### Realizad otro script o en el mismo, la búsqueda de los correos con extensión "upv.es". 

   ######  



3. ###### Realizad otro script o en el mismo, que muestre sólo las cuentas de correo por pantalla.

   ###### 

#### Ejercicio 2:

1. ###### Codifica un script que cree una carpeta denominada C:\Proy-Pru . Puedes asumir que la carpeta todavía no existe.

   ###### 


2. ###### Las carpetas se crean con el cmdlet `New-Item`. Tendrás que utilizar el parámetro -itemType para indicar que quieres crear una carpeta.

   ###### 


3. ###### Una vez ejecutes el script la carpeta se habrá creado. Si lo ejecutas de nuevo se producirá un error porque la carpeta ya existe, así que tendrás que borrarla manualmente antes.

   ###### 

#### Ejercicio 3:

###### Codifica un script que muestre en pantalla si la carpeta `C:\Proy-Pru` existe o no. Puedes consultar la existencia de una carpeta con el cmdlet `Test-Path`



#### Ejercicio 4:

1. ###### Codifica un script que elimine una carpeta denominada `C:\Proy-Pru`, incluidos todos sus archivos y subcarpetas. Puedes asumir que la carpeta existe.

  ###### 

2. ###### Las carpetas se eliminan con el cmdlet Remove-Item. Tendrás que utilizar el parámetro `-recurse` para indicar que quieres eliminar todo su posible contenido.

  ###### 

3. ###### Para probar el script crea la carpeta y añade algunos archivos y subcarpetas. Una vez ejecutes el script la carpeta se habrá borrado. Si lo ejecutas de nuevo se producirá un error porque la carpeta ya no existe, así que tendrás que crearla manualmente antes.


