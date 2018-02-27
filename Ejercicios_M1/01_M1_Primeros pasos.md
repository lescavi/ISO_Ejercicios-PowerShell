# 		-- WINDOWS POWERSHELL --
## 				- Primeros pasos -  

### Ejercicio 1: 

###### Inicia sesión como Administrador y ejecuta la consola de PowerShell mediante el acceso directo de la barra de tareas. A continuación, configura algunas de las propiedades de la consola. Comienza por seleccionar el estilo y tamaño de letra que prefiera. A continuación, ajusta el tamaño del búfer de pantalla y la ventana para que ocupen exactamente el escritorio, sin solaparse con la barra de tareas. Cierra la consola y vuelva a abrirla, y contesta: ¿las propiedades que has ajustado se mantienen entre sesiones de la consola o no?.

`Las propiedades se mantienen correctamente.`

### Ejercicio 2:

###### Ejecuta los siguientes cmdlets en la consola de PowerShell, en orden, y marca con una “X” aquellos que provocan un error.

| Nº   | cmdlets               | resultado |
| ---- | -------------------------- | ---- |
| 1    | get-location               | OK   |
| 2    | getlocation                | x    |
| 3    | Get-Location               | OK   |
| 4    | set-location               | OK   |
| 5    | clearhost                  | x    |
| 6    | get-childitem c:\          | OK   |
| 7    | get-childitem c:/          | OK   |
| 8    | get-childitem  abcdefghijk | x    |

### Ejercicio 3:

###### ¿Cómo has sabido cuáles de los cmdlets del ejercicio anterior eran erróneos? Explica brevemente el motivo por el cual los erróneos han fallado.

- `Los errores 2 y 5 falta el guión entre verbo y nombre:`

  `get-location y clear-host serían los correctos`

- `El error 8:`

  `No existe la ubicación`

### Ejercicio 4:

###### Vuelve a ejecutar los cmdlets no erróneos del ejercicio 2, utilizando los atajos de teclado mencionados en el vídeo. ¿Cuáles son esos atajos?

- `F7`


- `El tabulador y las flechas`
- `Teclas superior-inferior para repetir orden anterior o posterior`

### Ejercicio 5:

###### Intenta ejecutar correctamente el siguiente cmdlet en dos líneas, ubicando el nombre del cmdlet (get-childitem) en la primera, y el argumento (c:\Windows) en la segunda. Explica brevemente cómo has podido conseguirlo.	 

###### 					`get-childitem c:\Windows` 

```
PS C:\Windows\system32> Get-ChildItem `
>> C:\Windows\
```

`Utilizando la comilla simple continuamos el comando en la linea de abajo.`
`Evita tener que seguir escribiendo en la misma linea.`