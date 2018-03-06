# | Ejercicios de Repaso |

# -- Simulacro de Examen --

###### 1) Escribe un scrip en Powershell que, dado un proceso por teclado emita un mensaje que diga:

```
Proceso X encontrado
Id  Name CPU
--  ---- ----
2   scss   22.22
```
###### Si no lo encuentra: `Proceso X no encontrado`

###### -------------------------------------------- Respuesta 1:

```
Get-Process
Write-Host

$n = Read-Host "Intrduce un nº de proceso"
$p = Get-Process -Id $n

Write-Host
foreach ($r in $p){
       
    Write-Host $r.Product":"
    echo $r
        
    }

        Write-Host

        if ($r -eq $p){

        Write-Host "- Proceso ""$n"" encontrado !!!"

        }
        else {
            Write-Host "- Proceso ""$n"" no encontrado..."
            Write-Host "¡ Ese proceso no existe o no se está ejecutando !"
        }
```

###### 2) Crea un fichero y dale nombre y lo guardas en `C:\users\usuaro\Documents.`

```
PS C:\Windows\system32> New-Item -ItemType File C:\Users\Lescavi\Documents\"Ejercicio_2.txt"


    Directorio: C:\Users\Lescavi\Documents


Mode                LastWriteTime         Length Name                             
----                -------------         ------ ----                             
-a----       06/03/2018      9:09              0 Ejercicio_2.txt                  
```

###### Ahora haz un script que realice una búsqueda de un fichero introducido por teclado (utilizamos el anteriormente creado) sobre `C:\Users\usuario`. El script debe enviar un mensaje de encontrado y visualizar su ubicación. Si no lo encuentra, emite un mensaje de `fichero X no econtrado`

###### -------------------------------------------- Respuesta 2:

```
Get-ChildItem C:\Users\Lescavi\Documents\

Write-Host
Write-Host ---------------------------------------------------------
Write-Host
Write-Host "Del directorio mostrado."
Write-Host 
[String]$a = Read-Host "# Intrduce nombre de fichero"
[String]$b = Get-ChildItem C:\Users\Lescavi\Documents\ -Name $a


Write-Host
foreach ($x in $b){   

        if ($x -eq $a) {

        write-host ---------------------------------------------------------
        write-host
        write-host "Fichero buscado: $a"
        write-host

        Write-Host "- Fichero ""$x"" encontrado !!!"
        Write-Host
        Write-Host "Ruta relativa: " 
        Resolve-Path -Relative C:\Users\Lescavi\Documents\$x
        Write-Host
        Write-Host "Ruta absoluta: " 
        Split-Path C:\Users\Lescavi\Documents\$x

    }
    else {

        Get-ChildItem C:\Users\Lescavi\Documents\
        Write-Host
        Write-Host ---------------------------------------------------------
        Write-Host
        Write-Host "- Fichero ""$a"" no encontrado..."
        Write-Host
        Write-Host "Ruta: ¿?¿?¿?¿?¿?¿?"
        Write-Host
        Write-Host "Comprueba que está bien escrito"

    }

    }
```

###### 3) Te han encargado que obtengas información acerca de los 10 procesos que más CPU han  consumido en un momento dado en un sistema Windows. En primer lugar, escribe un script que realice lo siguiente (se puede utilizar un menú):

    a) Visualizar solamente el nombre de los procesos implicados y los consumos de  CPU.
    b) Visualizar el resultado en una ventana distinta a la consola (ver Out- GridView).
    c) Guardar el resultado en un fichero de texto denominado MasCPU.txt. (Abrir fichero)
    d) Guardar el resultado en un fichero HTML denominado MasCPU.html. (Abrir fichero)
    e) Guardar el resultado en un fichero CSV denominado MasCPU.csv. (Abrir fichero)

###### 4) Tenemos el siguiente fichero:

```
Nombre,cuenta,email,id,grupo
abc,user1,a@mail.com,122,users
def,user2,b@mail.com,133,users
ghi,user3,c@mail.com,222,admin
jkl,user4,d@mail.com,333,users
mnp,user7,e@mail.com,444,admin
```

###### Realiza un script que:

    a) Cuente las líneas
    b) Busque un usuario cuyo patrón sea introducido por teclado
    d) Diga si existe y muestre la línea
    e) Si no, emita un resultado negativo.