#  Reto#3 
## Ejercicio #1

> Crear 20 redes y que cada una disponga de aproximadamente 100 host habilitados para conectar 100 dispositivos (tables ,telefonos celulares, pcs etc.) ademas cada red debe indicar su "Gateway" reservando al menos 3 direcciones IP .

 ### Procedimiento: 

  **1.  Identificar con que clase de direccion IP trabajaremos.**

 **CLASE**  |**IP PREDETERMINADA**  | **RANGO** |
|:------------- |:---------------:| -------------:|
| A         | 255.0.0.0       |0.0.0.0 - 127.255.255.255      |
| B        | 255.255.0.0       |  128.0.0.0 - 191.255.255.255   |
| C         |255.255.255.0       | 192.0.0.0 - 223.255.255.255       |

 - Se procede a trabajar con una red de clase C especificamente la red con el `IP: 192.150.0.0` la cual nos permitira almacenar las 20 sub redes<

**2 Creacion de a nueva mascara de Red**


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

Donde : la cantidad de (0) representan la cantidad de bists del host (0) calculados anteriormente (7)

En decimal : 255.255.255.128  = /25

```
 **3. Calculo de host**

- Para calcular la cantidad de host que puede admitir mi nueva mascara de red se procede con la sigiente formula :
```
H =2^m-k 

Donde:

h= nuemero de host 

m = cantidad de bits disponibles para calcular el host (cantidad de (0) en el ultimo octeto de mi nueva mascara de red )

k= numero de direcciones IP que seran reservadas

H = 2^7-3

H= 128 - 3
H= 125 (HOST disponibles )
```

**4.Salto de Red**

- El salto de red no es mas que el cambio entre sub redes del host se calcula restando una constante a la cantidad total de direcciones Host
```
n= k-128

Donde:

k=256
128= es el numero de redes IP de host calculadas 

n=256-128=128(este es el salto de red )
```

