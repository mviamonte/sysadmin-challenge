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

### Reto 3 - Utilizando conceptos de direccionamiento IP -  🌎 
Hagamos, de forma practica algunos ejercicios de Networking. Digamos que necesitamos crear veinte redes distintas, es una empresa relativamente mediana asi que vamos a tener que separar logicamente, los departamentos y grupos de trabajo por red. 
Queremos tener una direccion IP base adecuada para alojar las veinte (20) redes indicadas y la cantidad de host o dispositivos dentro de cada red. Estos dispositivos pueden ser laptops, pcs, telefonos moviles, etc. 
Dentro de cada red, existiran al menos unos 100 dispositivos que se van a conectar a cada red. Es decir
Red 1 - 100 usuarios
Red 2 - 100 usuarios
Y asi hasta llegar a la red 20. 
Para esto necesitas planificar el direccionamiento IP. ¿Como haces eso? Bueno, esa es la parte del reto. Tienes que aplicar los conocimientos adquiridos en redes y realizar este ejercicio, especificamente como separar o crear sub-redes. El resultado, seran las veinte redes con sus correspondientes segmentos y el comienzo y final de cada segmento de red asi como segmentos para los dispositivos o host. Adicionalmente, cada red debe indicar su "Gateway", y reservar al menos tres (3) direcciones IP. 

## Un ejemplo simple
Una (1) red y ciento cincuenta (150) host
Direccion IP base 192.168.1.0/24
Direcciones IP reservadas: GW 192.168.1.1. .2, .3 y .4 estan reservadas. 
Rango util 192.168.1.5 - 192.168.1.254. 
Pregunta. ¿Cuantas direcciones IP disponibles tiene el ejemplo? 

Ahora, basado en este ejemplo, tienes que plantear igual, una direccion IP base con mascara /24 y otra direccion base con mascara /20. 
Sugerencia, puedes usar la misma 192.168.1.0 como base, pero con las mascaras indicadas. Es decir 192.168.1.0/24 y 192.168.1.0/20. Evidentemente, los rangos van a ser distintos para los dos cosas. Tampoco hagas los "calculos" de manera manual, busca herramientas online que te permitan ejecutar la tarea, lo mas importante, entender que estas haciendo. 

Una vez resuelto esto, responde las siguientes preguntas, todas asociadas al segundo caso, el de /20. 
1. ¿Cual es la direccion de red de la red numero cuatro (4)?    
2. ¿Cual seria el gateway de la ultima red, es decir de la red numero veinte (20)?   
3. ¿Si la red diez (10) es la red de servidores web , cual seria una direccion IP valida para un servidor Apache a ser desplegado en dicha red?     
4. Imagina que la re ocho (8) va a ser la red de "servicios" y decides instalar un DNS, indica dos direcciones IP para tal servicio.
5. Indica la direccion de broadcast the la red doce (12).

Un tip. Piensa que en el archivo MD puedes agregar tablas para que la informacion este mas organizada. 
Exito y suerte!! 

### Reto 4 - Poniendo a prueba los conocimientos -  🧠
La empresa ACME, esta interesada en migrar su pagina web hacia la nube, para esto, solo cuentan inicialmente con un presupuesto de USD$ 25 💵 para una Prueba de conceptos of "Proof of Concept(PoC) y asi, evaluar si un modelo de Cloud 🌩️ se adapta a sus necesidades, actualmente su servidor web se encuentra sobre Ubuntu. 
Inicialmente, sus usuarios van a estar ubicados en la ciudad de New York. No hay ningun requerimiento en especifico respecto a los recursos del servidor (CPU, Memoria o disco). Como nota adicional, el servidor debe llevar un nombre personalizado y tener una(s) etiqueta(s) o "tags" para poder identificarlo. Sugerencia, podria usar `ACME` y `POC` (Proof of Concept) como etiquetas, tambien podrias agregar algo como `webserver`. 

#### Paso 1 (4.1)
Utilizando el servicio **Droplet** de `Digital Ocean` [algo de ayuda aqui](https://www.digitalocean.com/community/conceptual-articles/introduction-to-web-servers)
1. Configura un servidor web solo el protocolo `HTTP` sin nivel adicional de seguridad. Puedes utilizar `Apache` o `NGINX`
2. Debe llevar una direccion IP (privada) dentro de los rangos calculados en el **Reto #3** (de ser posible) y debe ser accesible, al menos internamente. Debes encontrar al menos dos metodos de poder verificar que el servidor web esta funcional desde el mismo servidor o desde el exterior. Verifica la disponibilidad de tu IP Base y segmentos calculados [aqui](https://docs.digitalocean.com/products/networking/vpc/concepts/plan-your-network/). 
3. Utiliza los creditos disponibles en **Digital Ocean**. Recuerda, que al encender un servidor (o cualquier servicio), por cada minuto que este encendido (esto depende del servicio), el mismo estara consumiendo los creditos gratis con los que ahora cuentas. Recuerda que hay un limite de presupuesto del cliente. Toma las medidas necesarias para que no se exceda el presupuesto del cliente. 
4. Crea el / los acceso(s) necesario(s) para poder administrar el **droplet** remotamente
5. Considera, que existe la posibilidad de que tengas que configurar el `firewall` interno del sistema operativo para permitir el tráfico del servidor web (entrante y saliente)
6. ¿Cuales son los comandos necesarios para verificar el estado del servicio asociado al servidor web?
7. Genera un procedimiento completo de los pasos a ejecutar para la configuracion del servidor web. (solo los comandos) Nota: Te van a servir en el paso 4.2
8. Dentro de los conceptos de Cloud revisados previamente ¿Dentro de que modelo (`IaaS`, `PaaS`, `SaaS`,etc) encaja el servicio de **droplet**?

#### Paso 2 (4.2)

1. ACME, ha decidido NO utilizar passwords para acceder a sus servidores, es decir, debes crear el procedimiento o pasos para poder acceder y administar el servidor web SIN uso de contraseñas.
2. Adicionalmente, se debe idear una manera de automatizar el proceso de creacion de los **droplets** es decir. ¿Hay alguna manera de desplegar al menos tres (3) **droplets** en un mismo Datacenter de manera NO interactiva? Estos **droplets** deberan tener la misma configuracion del servidor web, es decir, una vez inicializados y creados, la disponibilidad del servicio web debe ser inmediata. ¿Crees que si el despliegue de estos tres servidores fuese distribuido en tres Datacenters distintos tendrias algun tipo de ventaja o desventaja? De ser asi ¿Como desplegarias los tres servidores de manera simultanea, con los mismos principios mencionados en tres datacenters distintos?  
*Pista*: Utiliza la siguiente [utilidad desarrollada](https://docs.digitalocean.com/reference/doctl/reference/compute/droplet/create/) por `Digital Ocean` para poder interactuar con las API del servicio de `droplet`

Nota: solo en casos de emergencias, la mayoria de las soluciones para lo que se pide esta [aqui](https://www.digitalocean.com/community/tutorial-series/getting-started-with-cloud-computing) ⚠️

### Reto 5 - Automaticemos - 💻
La compañia ACME ha quedado totalmente convencida de que sus proximos pasos van a ser migrar su servidor web a la nube. Felicitaciones!! Por ahora, ACME decidio quedarse en la misma plataforma de nube de `Digital Ocean`
Sin embargo, con la intencion de que la infraestructura a crearse puede ser manejada por un sistema de control de versiones (VCS) como Git / Github ellos han decidido utilizar tecnologias basadas en IaC (Infrastructure as a Code). Una de ellas, es `Terraform` de Hashicorp. Asi que manos a la obra. Antes de hacer escribir cualquier linea de código, vayamos investigando lo siguiente:
#### Paso 1 (5.1)
1. ¿Que es IaC y cuales son sus principales características?
2. Ademas de Hashicorp Terraform ¿Que otras herramientas ofrecen capacidades similares?
3. ¿Que tipo de lenguaje es `Terraform`?
4. ¿Cuales son los componentes principales de la arquitectura de Terraform? Escribe el detalle de cada uno.
5. Indaga en el detalle de los siguientes conceptos: Plugin, Providers, variables y el orden de prioridad de las mismas.
6. ¿Que son las expresiones dentro de terraform?
7. ¿Cuales son los pasos a ejecutar para utilizar apropiadamente Terraform?
8. ¿Cual es la principal utilidad de Terraform?
9. ¿Puede Terraform resolver el problema inicial de nuestro cliente ACME?
10. ¿Que pasaria si ACME, en un tiempo indeterminado, decide migrar su aplicacion a otro proveedor de Cloud tal como Amazon Web Service o Microsoft Azure? ¿Puede seguir utilizando Terraform? ¿Existe una herramienta que pueda sustituir el uso de Terraform? Si la respuesta es si. ¿Cuales son las ventajas y desventajas?

#### Paso 2 (5.2)
Teniendo claros todos los conceptos, hagamos una pequeña prueba con `Terraform`
1. Instalar la version mas reciente de `terraform` en tu computadora.
2. Crea un directorio llamado `proyecto_final`
3. Crear una configuracion que tenga la capacidad de crear un recurso `random` dentro del archivo `main.tf` (este archivo realmente se puede llamar `pepito.tf`y Terraform lo entendera igual) en el directorio previamente creado. Este recurso creara una cadena de texto (string) aleatoria. [Revisa esta documentacion para entender el ejemplo](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/string). Ten en cuenta que para cada recurso, hay argumentos, expresiones y atributos. ¿Sabes cual es la diferencia entre ellos? Tambien, ten en cuenta que inicialmente, solo deberias conocer los argumentos requeridos, para crear cada recurso, posteriormente y dependiendo del caso, usaras algunos argumentos adicionales. 
4. Crea un archivo llamado `versions.tf` dentro del mismo directorio y agrega los bloques de codigo correspondientes que te permitan crear el recurso anterior utilizando el `provider` random, en el mismo link anterior, valida como se utiliza este proveedor. 
5. Utiliza todos los comandos de `terraform` necesarios, para que tu configuracion, pueda crear satisfactoriamente, una cadena del tipo random de acuerdo a lo expresado en el archivo `main.tf`.
6. ¿Que comandos o utilidades te permiten validar la creacion de ese recurso tipo `random`? ¿Tienes todos los archivos necesarios dentro de tu proyecto?
7. Ten en cuenta que reciemente, si hiciste el paso de `git fetch` o de `git pull` en el repositorio, ahora encontraras un archivo llamado `.gitignore`. ¿Que te llama la atencion de ese archivo? ¿Cual crees que sea su finalidad?

