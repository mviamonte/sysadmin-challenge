# Sysadmin-challenge 
## Reto #2 

* 1  ¿Qué es una red ?
 
 > Es un mecanismo que permite la interconexión entre dispositivos los cuales se comunican entre si y comparten  información y recursos.
 ---
 
* 2 ¿ Qué es un protocolo TCP/IP ?

> Los protocolos son reglas y estándares que permiten a los dispositivos de una red comunicarse de manera efectiva. 
> El conjunto de protocolos `TCP/IP` es un conjunto de protocolos ampliamente usados en Internet.

> El protocolo `TCP (Protocolo de Control de Transmisión)` es responsable de dividir los datos en paquetes, enviarlos a través de la red y asegurarse de que lleguen correctamente al destino. 

> El protocolo `IP (Protocolo de Internet)` es uno de los protocolos más importantes en Internet. Es responsable de asignar direcciones únicas a cada dispositivo conectado a una red. Una dirección IP es una serie de números que identifica de manera única un dispositivo en una red. Hay dos versiones principales de IP: `IPv4` e `IPv6`. `IPv4` utiliza direcciones de `32 bits`, mientras que `IPv6` utiliza direcciones de `128 bits`.

> La composición de una dirección IP depende de la versión utilizada. En `IPv4`, una dirección IP se compone de cuatro números separados por puntos, por ejemplo, `192.168.0.1`. En `IPv6`, una dirección IP se compone de ocho grupos de cuatro dígitos hexadecimales separados por dos puntos, por ejemplo, `2001:0db8:85a3:0000:0000:8a2e:0370:7334`.

> `La máscara de red` se utiliza para determinar qué parte de una dirección IP corresponde a la red y qué parte corresponde al host. Es una serie de números que se aplica a una dirección IP para dividirla en una parte de red y una parte de host. `La máscara de red se representa en forma de una dirección IP también`.

> `La dirección de red` :  es la parte de una dirección IP que identifica la red a la que pertenece un dispositivo.
---

* 3 Resume brevemente, en el mismo archivo la funcionalidad de los siguientes comandos, de ser posible añade una salida de cada uno de ellos en tu equipo y cada paso que hayas ejecutado para obtener tal salida (recuerda utilizar el MARKDOWN)   `ip a `,  `lshw -class network `,   `ip route show `. ¿Que información importante destacarías de las salidas de los comandos indicados?

####   Comando : ip a 

> Este comando se utiliza para mostrar la configuración de red de tu sistema . Al ejecutarlo, obtendrás información sobre las interfaces de red disponibles en tu dispositivo, como   `direcciones IP  asignadas `,  `máscaras de red `,  `direcciones MAC ` . Es una forma útil de verificar la configuración de red de tu sistema.

```
ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000 link/loopback 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo 
valid_lft forever preferred_lft forever 
inet6 ::1/128 scope host 
<!--valid_lft forever preferred_lft forever
```

### lo: <LOOPBACK,UP,LOWER_UP>

> Indica el estado de la interfaz de red,  en este caso el estado de la interfaz de `BUCLE*  esta activa (  UP. LOWER_UP)`

### mtu 65536

> Esta linea muestra el tamaño máximo de de la unidad de transmisión  `MTU` en este caso el tamaño es de ` 65536 bites `

### qdisc noqueue state UNKNOWN group default qlen 1000

> Esta linea describe la disciplina de cola (`qdisc`) utilizada para la interfaz de bucle en este caso no hay cola `noqueue`, el estado es desconocido (`UNKNOWN`) el grupo predeterminado es (`group default`) y tiene una longitid `qlen ` de `1000`.

### link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00

> Esta linea muestra la dirección **MAC** `00:00:00:00:00:00`  y la dirección de difusion `00:00:00:00:00:00`  asociadas a la interfaz de bucle invertido 

### inet 127.0.0.1/8 scope host lo 

> Esta linea indica la dirección `IP : 127.0.0.1` ( asignada a la interfaz de bucle)  , la cual tiene una validez perpetua `forever` , el ámbito `scope` de la dirección IP es `host` ( lo que significa que puede acceder desde la propia maquina ) 

### valid_lft forever preferred_lft forever 

>  Estas lineas indican que la direccion IP tiene una validez perpetua `forever` y es la preferida para la interfaz de bucle invertido `preferred_lft forever`

### inet6 ::1/128 scope host

> Esta línea muestra la dirección `IPv6 (::1/128)` asignada a la interfaz de bucle invertido. Al igual que la dirección `IPv4`, el ámbito (`scope`) de la dirección `IPv6` es `host`.

### valid_lft forever preferred_lft forever

>  Al igual que en el caso de la dirección `IPv4`, estas líneas indican que la dirección `IPv6 (::1/128)` tiene una validez perpetua `(forever)` y es la preferida `(preferred_lft)` para la interfaz de bucle invertido.




```
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
link/ether 00:11:22:33:44:55 brd ff:ff:ff:ff:ff:ff
inet 192.168.1.100/24 brd 192.168.1.255 scope global eth0
valid_lft forever preferred_lft forever
inet6 fe80::211:22ff:fe33:4455/64 scope link
valid_lft forever preferred_lft forever.
```

### eth0

> Es el mombre de la interfaz de red 

### <BROADCAST,MULTICAST,UP,LOWER_UP>

> Estos son los estados de la interfaz de red. Indican que la interfaz está `habilitada (UP)` y `conectada (LOWER_UP)`. También indica que la interfaz puede `enviar y recibir paquetes de difusión (BROADCAST)` y `paquetes multicast (MULTICAST)`

### mtu 1500

> El valor `MTU (Unidad de Transmisión Máxima)` de la interfaz es `1500 bytes`. Esto especifica el tamaño máximo de los paquetes que se pueden enviar a través de la interfaz sin fragmentación.

### qdisc fq_codel state UP group default qlen 1000

> Esta línea describe el algoritmo de programación de colas utilizado por la interfaz de red. En este caso, se utiliza el algoritmo `fq_codel`. También indica que el estado de la interfaz es `UP` y que pertenece al `grupo predeterminado`. El valor `qlen 1000` especifica la longitud máxima de la cola de paquetes en la interfaz.

### link/ether 00:11:22:33:44:55

> Esta línea muestra la dirección `MAC (Media Access Control) 00:11:22:33:44:55` de la interfaz de red. La dirección MAC es un identificador `único` asignado a la interfaz de red.

### brd ff:ff:ff:ff:ff:ff

>  Esta es la dirección de difusión de capa 2 de la interfaz de red. Se utiliza para enviar paquetes a todos los dispositivos en la red local.

### inet 192.168.1.100/24 brd 192.168.1.255 scope global eth0

> Esta línea muestra `la dirección IP` asignada a la interfaz de red. En este caso, `la dirección IP es 192.168.1.100` con una `máscara de subred de /24`. La `dirección de difusión de capa 3 es 192.168.1.255`.

### valid_lft forever preferred_lft forever

> Estas líneas indican que la dirección IP asignada a la interfaz de red tiene una validez indefinida `(forever)`. Esto significa que la dirección IP no caducará automáticamente. La opción `preferred_lft` también se establece en `forever`, lo que indica que `esta dirección IP es la preferida`.

### inet6 fe80::211:22ff:fe33:4455/64 scope link

>  Esta línea muestra la dirección `IPv6` asignada a la interfaz de red. En este caso, `la dirección IPv6 es fe80::211:22ff:fe33:4455` con una `longitud de prefijo de /64`. Esta dirección IPv6 es una dirección de enlace local y se utiliza para la comunicación en la red local.

---

#### Comando : lshw -class network

> El comando `"lshw -class network"` es utilizado en sistemas operativos basados en `Linux` para obtener información detallada sobre los dispositivos de red presentes en el sistema.


```
lshw -class network

descripcion : Ethernet interface
producto : 82540EM Gigabit Ethernet Controller 
fabricante : Intell Corporation 
id fisico : 3
informacion del bus : pci@0000:00:03.0
nombre logico : emp0s3
version: 02
serie: 08:00:27:83:59:d6
tamaño : 1Gbit/s
capacidad : 1Gbit/s
anchura : 32bits
reloj: 66MHz
Capacidades : pm pcix bus_master cap_list ethernet physical top 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuracion : autonegotiation=on broadcast=yes driver=e1000 driverversion=6.2.0-31-generic duplex=full ip=10.0.2.15 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s recursos: irq:19 memoria: f0200000-f021ffff ioport:d020(size=8)

```

### Descripción
> Esta línea indica que se trata de una interfaz de red `Ethernet`.

### Producto

> Indica el `modelo del controlador de Ethernet`, en este caso, es un `"82540EM Gigabit Ethernet Controller"`.


### Fabricante

> Muestra el fabricante del `controlador de Ethernet`, que en este caso es `"Intel Corporation".`

## ID físico

> Es un identificador único asignado a la interfaz de red. En este caso, el `ID físico es "3"`.

### Información del bus

> Proporciona detalles sobre el bus al que está conectada la interfaz de red. En este caso, está conectada al `bus PCI con la dirección "pci@0000:00:03.0"`.

### Nombre lógico

> Es el nombre asignado a la interfaz de red. En este caso, `el nombre lógico es "emp0s3"`.

### Versión

> Indica la versión del controlador de `Ethernet`, que en este caso es `"02"`.

### Serie

> Muestra la dirección `MAC` de la interfaz de red. En este caso,` la dirección MAC es "08:00:27:83:59:d6"`.

### Tamaño

> Indica la `velocidad de la interfaz de red`, que en este caso es de `"1Gbit/s" (1 gigabit por segundo)`.

### Capacidad

> Es la capacidad máxima de la interfaz de red, que también es de `"1Gbit/s"`.

### Anchura

> Indica el ancho de datos de la interfaz de red, que en este caso es de `"32 bits"`.

### Reloj 

> Muestra la `frecuencia del reloj de la interfaz de red`, que es de `"66MHz"`.

### Capacidades

> Enumera las `capacidades de la interfaz de red`, como la `administración de energía (pm)`,` soporte para bus PCI-X (pcix)`, `capacidad de maestro de bus (bus_master)`, `lista de capacidades (cap_list)`, `soporte para Ethernet`.

### Configuración

> Proporciona información sobre la configuración actual de la interfaz de red, como la `negociación automática (autonegotiation)`, si se permite la `difusión (broadcast)`, el `controlador utilizado (driver)`, `la versión del controlador (driverversion)`, el modo `dúplex (duplex)`, la `dirección IP asignada (ip)`, `la latencia`, `el estado de la conexión (link)`.

### Recursos

> Muestra los recursos asignados a la `interfaz de red`, como la `interrupción (irq)`, la `memoria utilizada (memoria)`, el `puerto de E/S utilizado (ioport)`

---

#### Comando: ip route show

> El comando `"ip route show"` es útil para visualizar y verificar la configuración de `enrutamiento IP` en un sistema `Linux`. Proporciona información importante para comprender cómo se dirigen los paquetes de datos a través de la red.

```
ip rote show

default via 10.0.2.2 dev enp0s3 proto dhcp metric 100 
10.0.2.0/24 dev enp0s3 proto kernel scope link src 10.0.2.15 metric 100
169.254.0.0/16 dev enp0s3 scope link metric 1000
```

### default via 10.0.2.2 dev enp0s3 proto dhcp metric 100

> Esta línea establece la ruta predeterminada `(default)` para el tráfico saliente. El tráfico se enviará a través del dispositivo de red `enp0s3` hacia la dirección `IP 10.0.2.2`. El protocolo utilizado para la comunicación es `DHCP (proto dhcp)`. El `valor de la métrica es 100`, lo que indica la preferencia de esta ruta en comparación con otras rutas posibles.

### 10.0.2.0/24 dev enp0s3 proto kernel scope link src 10.0.2.15 metric 100

> Esta línea define una ruta para la red `10.0.2.0/24`. El tráfico destinado a esta red se enviará a través del dispositivo de red `enp0s3`. El protocolo utilizado es el `kernel (proto kernel)`. El `alcance (scope)` de esta ruta es de `enlace (link)`. `La dirección IP de origen (src)` asociada a esta ruta es `10.0.2.15`. Al igual que en la línea anterior, la métrica es `100`.

### 169.254.0.0/16 dev enp0s3 scope link metric 1000

> Esta línea establece una ruta para la red `169.254.0.0/16`. El tráfico destinado a esta red se enviará a través del dispositivo de `red enp0s3`. El alcance `(scope)` de esta ruta es de enlace `(link)`. La métrica para esta ruta es `1000`, lo que indica que tiene una preferencia más baja en comparación con las rutas anteriores.

> Estas líneas definen las rutas de red en un sistema y especifican cómo se debe enrutar el tráfico hacia diferentes destinos.


---
* 4 Describe brevemente para que se utiliza el protocolo HTTP / HTTPS (Prioridad, por ahora en HTTP) y el protocolo DNS.

> El protocolo `HTTP (Hypertext Transfer Protocol)` se utiliza para la comunicación entre un cliente (como un navegador web) y un servidor web. HTTP se utiliza para solicitar y enviar recursos, como páginas web, imágenes y archivos, a través de Internet. Es un protocolo sin estado, lo que significa que cada solicitud se trata de forma independiente sin tener en cuenta las solicitudes anteriores.

> El protocolo `HTTPS (Hypertext Transfer Protocol Secure)` es una versión segura de HTTP que utiliza cifrado `SSL/TLS` para proteger la comunicación entre el cliente y el servidor. `HTTPS` se utiliza para garantizar la confidencialidad e integridad de los datos transmitidos, especialmente en transacciones en línea y sitios web que manejan información sensible.

> El protocolo `DNS (Domain Name System)` se utiliza para traducir los nombres de dominio legibles por humanos, como `"www.google.com"`, en direcciones IP numéricas que las computadoras pueden entender. DNS actúa como una especie de directorio telefónico de Internet, permitiendo que los usuarios accedan a los recursos en línea utilizando nombres de dominio en lugar de tener que recordar direcciones IP complicadas.
---

* 5 ¿Que es un servidor web y cuales softwares podrias utilizar para implementar uno?

> `Un servidor web` es un software que se ejecuta en un servidor y responde a las solicitudes `HTTP` de los clientes. Algunos de los softwares más comunes utilizados para implementar un servidor web son `Apache HTTP Server, Nginx, Microsoft Internet Information Services (IIS) y LiteSpeed`.
---

* 6 ¿Cual es la salida del comando dig www.google.com? En base a lo revisado en el punto 3 ¿Que puedes entender de la salida del comando?


```
dig www.google.com

; <<>> DiG 9.18.120ubuntu0.22.04.2-Ubuntu <<>> www.google.com
;; global options : +cmd
;; Got answer:
;; ->>HEADER<<- opcode : QUERY, status: NOERROR, id: 8134
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORYTY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION: 
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION: 
;www.google.com.              IN            A

www.google.com  278           IN      A     64.233.186.104
www.google.com  278           IN      A     64.233.186.105
www.google.com  278           IN      A     64.233.186.147
www.google.com  278           IN      A     64.233.186.103

;; Query time : 67 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Wed Sep 06 06:11:07 -03  2023
;; MSG SIZE rcvd: 139
```

### "; <<>> DiG 9.18.120ubuntu0.22.04.2-Ubuntu <<>> www.google.com":

> Esta línea muestra la versión de DiG que se está utilizando y el dominio sobre el cual se está realizando la consulta.

### ";; global options : +cmd"

> Esta línea indica las opciones globales que se han configurado para la consulta. En este caso, "+cmd" indica que se deben mostrar los resultados de la consulta.

### ";; Got answer:"

> Esta línea indica que se ha recibido una respuesta del servidor DNS.

### ";; ->>HEADER<<- opcode : QUERY, status: NOERROR, id: 8134"

> Esta línea muestra el encabezado de la respuesta. El opcode indica que se trata de una consulta y el status indica que no se produjo ningún error. El ID es un número de identificación único para esta consulta.

### ";; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 1":

> Esta línea muestra las banderas y los recuentos de secciones en la respuesta. Las banderas "qr" indican que es una respuesta, "rd" indica que se solicitó recursividad y "ra" indica que la recursividad está disponible. En este caso, hay 1 consulta, 6 respuestas, 0 autoridades y 1 adicional.

### ";; OPT PSEUDOSECTION:"

> Esta línea indica que sección OPT es una sección pseudo-óptica.

### "; EDNS: version: 0, flags:; udp: 65494"

> Esta línea muestra información adicional sobre la sección OPT. En este caso, la versión es 0 y el puerto UDP utilizado es 65494.

### ";; QUESTION SECTION: ;www.google.com. IN A"

> Esta línea muestra la sección de pregunta de la consulta. Indica que se está buscando el registro de tipo A (dirección IP) para el dominio "www.google.com".

### "www.google.com 278 IN A 64.233.186.104"

> Estas líneas muestran las respuestas a la consulta. En este caso, se proporcionan cuatro direcciones IP asociadas al dominio "www.google.com".

### ";; Query time : 67 msec"
> Esta línea indica el tiempo que tomó realizar la consulta, en este caso, 67 milisegundos.

### ";; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)"

> Esta línea muestra el servidor DNS utilizado para realizar la consulta. En este caso, se utilizó el servidor local en la dirección IP 127.0.0.53 y el puerto 53.

### ";; WHEN: Wed Sep 06 06:11:07 -03 2023"

> Esta línea indica la fecha y hora en que se realizó la consulta.

### ";; MSG SIZE rcvd: 139"

> Esta línea muestra el tamaño del mensaje recibido en bytes.

---




