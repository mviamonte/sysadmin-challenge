# Reto#3

## Ejercicio #1

> Crear 20 redes y que cada una disponga de aproximadamente 100 host habilitados para conectar 100 dispositivos (tables ,telefonos celulares, pcs etc.) ademas cada red debe indicar su "Gateway" reservando al menos 3 direcciones IP .

### Procedimiento

  **1.  Identificar con que clase de direccion IP trabajaremos.**

 **CLASE**  |**IP PREDETERMINADA**  | **RANGO** |
|:------------- |:---------------:| :-------------:|
| A         | 255.0.0.0       |0.0.0.0 - 127.255.255.255      |
| B        | 255.255.0.0       |  128.0.0.0 - 191.255.255.255   |
| C         |255.255.255.0       | 192.0.0.0 - 223.255.255.255       |

- Se procede a trabajar con una red de clase C especificamente la red con el `IP: 192.150.0.0`  la cual nos permitira almacenar las 20 sub redes

**2.  Creacion de a nueva mascara de Red**

- Para crear una mascara de red que pueda almacenar los 100 host se comienza  por escribir en `binario` la mascara general de una direccion IP de `clase C`

```
255.255.255.0 en decimal 
11111111.11111111.11111111.00000000 en binario notese que los (1) representan los bits de red y los (0) los bits pertenecientes al host.
```

- Para determinar la cantidad de bits que necesitamos para que esta red tenga 100 host aplicamos la formula

```text

n=log2(k+r) 
k= numero de host que dese conseguir (100)

n =numero de bits del host (0) necesarios 

r= numero de ip reservadas (3)

n=log2(100+3)=6.686 redondeando a 7 esto me quiere decir  que se necesitan 7 bits perteneciente al host para poder obtener aproximadamente 100 host para esta sub red 
```
...
- Mi nueva mascara de red seria

```text
11111111.11111111.11111111.10000000

Donde : la cantidad de (0) representan la cantidad de bists del host (0) calculados anteriormente (7)

En decimal : 255.255.255.128  = /25

```

 3.Calculo de host

- Para calcular la cantidad de redes IP pertenecientes al host que puede admitir mi nueva mascara de red se procede con la sigiente formula

```

H =2^m-2

Donde:

h= numero de host 


k= numero de direcciones IP que seran reservadas

H = 2^7-3

H= 128 - 3
H= 125 (HOST disponibles )
```

4.Salto de Red

- El salto de red no es mas que el cambio entre sub redes del host se calcula restando una constante a la cantidad total de direcciones Host

```text

n= k-128

Donde:

k=256
128= es el numero de redes IP de host calculadas 

n=256-128=128(este es el salto de red )
```

5.calculo de subredes

- En el ejercicio #1 se piedio crear una red que tuviese 20 sub redes distintas y que cada una almacenara aproximadamente 100 host

**Procedimiento:**

- Debemos saber  cuantos bits de nuestra direccion base se necesitan para poder crear las 20 sub redes, para eso se usa la formula :

```text

n= log2(s)

Donde:

n= cantidad de bits necesarios 
s= cantidad de sub redes solicitadas 

n=log2(20)= 4.32 redondeando a 5

n=5 se necesitan 5 bits de los 32 disponibles para la red 

```

**6. Separacion bits de red y bits de host**

- Para separar los bits que le pertenecen a una red y a su host se hace de la siguiente forma

> Entendiendo que si el utimo octeto en Ipv4 cuenta con solo 32 bits y ya calculamos anteriormente que 7 le pertencen al host y los que fueron calculados ahora, quedaria disponible solamente 20bits que serian usados para la direccion de red dando como resultado la siguiente tabla .

```TABLE

IP base : 192.150.0.0


|     SUBRED    	|   BROADCAST   	|    GATEWAY    	|             RANGO             	|
|:-------------:	|:-------------:	|:-------------:	|:-----------------------------:	|
|  192.150.0.0  	| 192.150.0.127 	|  192.150.126  	|   192.150.0.1 - 192.150.125   	|
| 192.150.0.128 	| 192.150.0.255 	| 192.150.0.254 	| 192.150.0.129 - 192.150.0.253 	|
|  192.150.1.0  	| 192.150.1.127 	| 192.150.1.126 	|  192.150.1.1 - 192.150.1.125  	|
| 192.150.1.128 	| 192.150.1.255 	| 192.150.1.254 	| 192.150.1.129 - 192.150.1.253 	|
|  192.150.2.0  	| 192.150.2.127 	| 192.150.2.126 	|  192.150.2.1 - -192.150.2.125 	|
| 192.150.2.128 	| 192.150.2.255 	| 192.150.2.254 	| 192.150.2.129 - 192.150.2.253 	|
|  192.150.3.0  	| 192.150.3.127 	| 192.150.3.126 	|  192.150.3.1 - 192.150.3.125  	|
| 192.150.3.128 	| 192.150.3.255 	| 192.150.3.254 	| 192.150.3.129 - 192.150.3.253 	|
|  192.150.4.0  	| 192.150.4.127 	| 192.150.4.126 	|  192.150.4.1 - 192.150.4.125  	|
| 192.150.4.128 	| 192.150.4.255 	| 192.150.4.254 	| 192.150.4.129 - 192.150.4.253 	|
|  192.150.5.0  	| 192.150.5.127 	| 192.150.5.126 	|  192.150.5.1 - 192.150.5.125  	|
| 192.150.5.128 	| 192.150.5.255 	| 192.150.5.254 	| 192.150.5.129 - 192.150.5.253 	|
|  192.150.6.0  	| 192.150.6.127 	| 192.150.6.126 	|  192.150.6.1 - 192.150.6.125  	|
| 192.150.6.128 	| 192.150.6.255 	| 192.150.6.254 	| 192.150.6.129 - 192.150.6.253 	|
|  192.150.7.0  	| 192.150.7.127 	| 192.150.7.126 	|  192.150.7.1 - 192.150.7.125  	|
| 192.150.7.128 	| 192.150.7.255 	| 192.150.7.254 	| 192.150.7.129 - 192.150.7.253 	|
|  192.150.8.0  	| 192.150.8.127 	| 192.150.8.126 	|  192.150.8.1 - 192.150.8.125  	|
| 192.150.8.128 	| 192.150.8.255 	| 192.150.8.254 	|  192.150.8.129 - 192.150.253  	|
|  192.150.9.0  	| 192.150.9.127 	| 192.150.9.126 	|   192.150.9.1 - 192.150.125   	|
| 192.150.9.128 	| 192.150.9.255 	| 192.150.9.254 	|  192.150.9.129 - 192.150.253  	|

```

## Ejercicio #2

- Una (1) red y ciento cincuenta (150) host Direccion IP base 192.168.1.0/24 Direcciones IP reservadas: GW 192.168.1.1. .2, .3 y .4 estan reservadas. Rango util 192.168.1.5 - 192.168.1.254. Pregunta. ¿Cuantas direcciones IP disponibles tiene el ejemplo?

```text

En este ejemplo hay 250 direcciones IP disponibles 

```

## Ejerccio #3

-¿Cual es la direccion de red de la red numero cuatro (4)?

> 192.150.1.128

¿Cual seria el gateway de la ultima red, es decir de la red numero veinte (20)?

> 192.150.9.254


¿Si la red diez (10) es la red de servidores web , cual seria una direccion IP valida para un servidor Apache a ser desplegado en dicha red?

> si la red 192.150.4.128 es la red de servidores web .. se usaria la direccion IP 192.150.4.135 ya que no esta reservada y es una red valida

Imagina que la red ocho (8) va a ser la red de "servicios" y decides instalar un DNS, indica dos direcciones IP para tal servicio.

>si la red 192.150.3.128 va  a ser una red de servicios las direcciones ip que utilizaria serian 192.150.3.131 - 192.150.3.132

Indica la direccion de broadcast the la red doce (12)

> 192.150.5.255

