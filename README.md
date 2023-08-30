# sysadmin-challenge
## Instrucciones
En este primer paso, lo que vamos a hacer es refrescar tus conocimientos en **Git / Github**, esto, deberia ser el flujo "normal" de un ambiente de trabajo colaborativo. Es decir, vas a colaborar con otros ingenieros y su trabajo estara, posiblemente en un repositorio parecido a este.

### Reto 1 - Prueba colaboracion
1. Descarga este repositorio en tu equipo de trabajo
2. Verifica el contenido del repositorio
3. Añade un archivo llamado `reto1.MD` a tu repositorio local. Este archivo debe llevar nomenclatura "Markdown" (Ver Nota). 
4. Verifica el repositorio remoto (Nombre)
5. Colabora con este repositorio (Subir tu archivo a este repositorio). 

Nota:
Tu archivo, con el que vas a colaborar en este repositorio, deberia lucir algo asi:
1. Descarga este repositorio en tu equipo de trabajo  
` comando utilizado para descargar el repositorio `
2. Verifica el contenido del repositorio  
`cd nombre_del_repositorio`  
`ls -lart`  
Y asi con el resto de los pasos indicados. Ademas, tu archivo debe llevar formato tipo "MARKDOWN". --> [Ver esta referencia](https://www.markdownguide.org/basic-syntax/)  
Adicionalmente, indica en breves lineas la explicacion de los pasos que estes ejecutando, siempre respetando los formatos aceptados por el archivo MD.

### Reto 2 - Networking tools 🌎 
Aprendamos sobre la marcha. Piensa en el escenario en el que vas a administrar un servicio web. 
Para tal fin, necesitas entender las herramientas (comandos) que te permitiran entender el estado del servicio que quieres administrar. Es decir, te llaman y tienes que tener la habilidad de entender el escenario actual y poder emitir un diagnostico apropiado. Pero antes, tienes que entender conceptos basicos y conocer las herramientas que estan a tu disposicion.   
Asi que ahora, te toca hacer tu segundo aporte a este repositorio siguiendo estos pasos, trabajemos de la misma forma que en el `reto 1`.
1. Crea un archivo en tu repositorio local llamado `reto2.MD` y utilizando todas las propiedades de archivos MD (Markdown) que consideres necesarias para añadir legibilidad, escribe con tus propias palabras los siguientes conceptos. (Concepto basico de redes, protocolo IP, protocolos TCP/IP, direccion IP, mascara de red, direccion de red y composicion de una direccion IP)
2. Resume brevemente, en el mismo archivo la funcionalidad de los siguientes comandos, de ser posible añade una salida de cada uno de ellos en tu equipo y cada paso que hayas ejecutado para obtener tal salida (recuerda utilizar el MARKDOWN) `ip a` `lshw -class network` `ip route show`. ¿Que informacion importante destacarias de las salidas de los comandos indicados?
3. Describe brevemente para que se utiliza el protocolo HTTP / HTTPS (Prioridad, por ahora en HTTP) y el protocolo DNS.
4. ¿Que es un servidor web y cuales softwares podrias utilizar para implementar uno?
5. ¿Cual es la salida del comando `dig www.google.com`? En base a lo revisado en el punto 3 ¿Que puedes entender de la salida del comando?  


### Solo en extricto caso de emergencia, leer esto ⚠️
### Consejo
Investiga, se curioso, pero conciso, trata de llevar la idea inicial de lo que quieres expresar. Ante la duda, recuerda que puedes usar el comando `man`
Y como "ultima opcion" te dejo esto que basicamente tiene casi [todo lo que necesitas](https://ubuntu.com/server/docs/network-introduction) 

### Otra ayuda
La salida del comando `ip a` te muestras las interfaces y direcciones IP disponibles en tu equipo local, esta salida podra variar, dependiendo del sistema operativo, lo importante, que entiendas que significa cada uno de las interfaces de red y su configuracion. 
`lo` es un tipo de interfaz "especial". No investiguemos mucho al respecto, por ahora. 
`enp0s25` es una interfaz de red que tiene su componente `inet` e `inet6`. Por ahora obviemos el `inet6` y concentrate en `inet`. Viste la direccion IP de la interfaz de red `enp0s25`?
¿Puedes apreciar la mascara de sub red y la direccion de broadcast? Si, no te mande a investigar eso pero de seguro que te lo encontraste en el camino. 

    ip a
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
           valid_lft forever preferred_lft forever
        inet6 ::1/128 scope host
           valid_lft forever preferred_lft forever
    2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
        link/ether 00:16:3e:e2:52:42 brd ff:ff:ff:ff:ff:ff link-netnsid 0
        inet 10.102.66.200/24 brd 10.102.66.255 scope global dynamic eth0
           valid_lft 3257sec preferred_lft 3257sec
        inet6 fe80::216:3eff:fee2:5242/64 scope link
           valid_lft forever preferred_lft forever
