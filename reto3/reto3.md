#  Reto#3 
## Ejercicio #1

> Crear 20 redes y que cada una disponga de aproximadamente 100 host habilitados para conectar 100 dispositivos (tables ,telefonos celulares, pcs etc.) ademas cada red debe indicar su "Gateway" reservando al menos 3 direcciones IP .

 #### Procedimiento: 

 > 1 El primer paso seria identificar con que clase de direccion IP trabajaremos; se mostraran las clases principales 

 **CLASE**  |**IP PREDETERMINADA**  | **RANGO** |
|:------------- |:---------------:| -------------:|
| A         | 255.0.0.0       |0.0.0.0 - 127.255.255.255      |
| B        | 255.255.0.0       |  128.0.0.0 - 191.255.255.255   |
| C         |255.255.255.0       | 192.0.0.0 - 223.255.255.255       |

> 2 Se procede a trabajar con una red de clase C especificamente la red con el `IP: 192.150.0.0` la cual nos permitira almacenar las 20 sub redes<

>3 Se procede a crear la mascara de red que soportara no solo a las 20 sub redes sino tambien a los 100 host o dispositivos que estaran conectados a cada sub red<

- Para crear una mascara de red que pueda almacenar los 100 host se comienza  por escribir en `binario` la mascara general de una direccion IP de `clase C`

```
255.255.255.0 en decimal 
11111111.11111111.11111111.00000000 en binario notese que los (1) representan los bits de red y los (0) los bits pertenecientes al host.
```

- Para determinar la cantidad de bits que necesitamos para que esta red tenga 100 host aplicamos la formula 

```
n=log2(k+r) 
k= numero de host que dese conseguir (100)

n =numero de bits del host (0) necesarios 

r= numero de ip reservadas (3)

n=log2(100+3)=6.686 redondeando a 7 esto me quiere decir  que se necesitan 7 bits perteneciente al host para poder obtener aproximadamente 100 host para esta sub red 
```
- Mi nueva mascara de red seria 
```
11111111.11111111.11111111.10000000

donde : la cantidad de (0) representan la cantidad de bists del host calculados anteriormente 

en decimal : 255.255.255.128  = /25