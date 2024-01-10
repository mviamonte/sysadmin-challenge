<center> <h1>Reto # 4</h1> </center>

_<center> <h2>**Servidores Web **</h2> </center>_


 
 _<center> <h2>**Definicion**</h2> </center>_

 _<center> <h3>¿ Que es un servidor Web ?</h2> </center>_

>Un servidor web es un programa de software o un sistema de hardware que proporciona contenido o servicios a los usuarios a través de internet, donde el  hardware juega un papel crucial en el rendimiento y la capacidad de un servidor web. Los componentes clave del hardware de un servidor web incluyen el procesador, la memoria RAM, el almacenamiento (disco duro o SSD), la tarjeta de red y, en algunos casos, tarjetas aceleradoras de red,  ayudando a proporcionar contenido a travez de internet. Este contenido puede ser páginas web, archivos, aplicaciones web, servicios de correo electrónico, entre otros.

_<center> <h3>Cloud servers </h2> </center>_

>Un cloud server, o servidor en la nube, es un servidor remoto que se encuentra alojado en un centro de datos y al que se puede acceder a través de internet. En lugar de estar físicamente presente en las instalaciones de una empresa o usuario, el servidor en la nube ofrece recursos informáticos, como capacidad de procesamiento, almacenamiento y aplicaciones, a través de una red. 


<center> <h3>¿ Cual es su Utilidad ?</h2> </center>

>Los servidores web son fundamentales para la operación de sitios web, aplicaciones web y servicios en línea, ya que permiten que estos sean accesibles desde cualquier lugar del mundo con conexión a internet.

_<center> <h3>Configuracion y creacion de un servidor web </h2> </center>_

>Hay varias maneras de configurar y crear un servidor web, dependiendo de tus necesidades y conocimientos técnicos. Aquí hay algunas opciones comunes:

1. Usar un proovedor de cloud  

> Se puede  contratar los servicios de un proveedor de alojamiento web, como `Amazon Web Services (AWS)`, `Google Cloud Platform`,  `Digital Ocean` , o un proveedor de alojamiento compartido. Estos proveedores suelen ofrecer herramientas para configurar fácilmente un servidor web y alojar nuestro sitio.

2. Configurar nuestro propio servidor fisico

>Con los conocimientos tecnicos necesrios se puede configuarar nuestro propio servidor web. Esto implica adquirir el software necesario , instalar un sistema operativo como `Linux` o `Windows Server`, configurar el software de servidor web (como `Apache`, `Nginx`, o `Microsoft IIS`), y asegurarte de tener una conexión a internet estable y segura.

3. Utilizar un servidor virtual privado (VPS)

>Un VPS es una opción intermedia entre un proveedor de alojamiento web y un servidor físico. Con un VPS, obtienes un entorno de servidor virtualizado que puedes configurar y administrar tú mismo, pero sin la necesidad de adquirir y mantener tu propio hardware físico.

4. Plataformas de alojamiento web gestionado
> Las plataformas de alojamiento web gestionado, como `WordPress.com`, `Wix`, o `Squarespace`. Estas plataformas ofrecen herramientas fáciles de usar para crear y alojar sitios web sin necesidad de configurar un servidor por tu cuenta.

_<center> <h3>Digital Ocean  </h3> </center>_

>Es un proveedor de servicios de infraestructura en la nube. Ofrece una variedad de servicios, incluyendo servidores virtuales, almacenamiento en la nube, bases de datos y otros recursos para alojar aplicaciones y sitios web.

_<center> <h3>¿ Como crear y configurar un servidor web usando Digital Ocean? </h2> </center>_

1. Crear una cuenta en DigitalOcean si aún no tienes una.

2. Iniciar sesión en tu cuenta y hacer clic en el botón "Create" (Crear) y seleccionar "Droplets" (Gotas) que es el término que DigitalOcean utiliza para sus servidores virtuales.

3. Elegir la distribución de Linux que deseas utilizar, como Ubuntu, CentOS, Debian, entre otros.

4. Seleccionar el plan de servidor que se ajuste a tus necesidades en cuanto a recursos (CPU, RAM, almacenamiento, etc.).

5. Elegir la región del centro de datos donde deseas que se ubique tu servidor.

6. Opcionalmente, puedes añadir opciones adicionales como copias de seguridad automáticas, monitoreo, o bloques de almacenamiento.

 7. Hacer clic en "Create Droplet" (Crear gota) para desplegar tu servidor.

8. Una vez que el servidor esté desplegado, recibirás un correo electrónico con la información de acceso, como la dirección IP, nombre de usuario y contraseña.

9. Conectarte a tu servidor utilizando un cliente SSH y configurar el software de servidor web, como Apache, Nginx, o cualquier otro que desees utilizar.

 _<center> <h3>Configuracion de un Droplet </h2> </center>_

 1.  Conéctate a tu servidor utilizando un cliente SSH.

 2. Actualiza el sistema operativo de tu servidor ejecutando el comando : 

 ```
 sudo apt update 
 sudo apt upgrade
```
3.  Instala Apache ejecutando el siguiente comando:

```
sudo apt install apache2
```
4. Una vez instalado, se inicia el servicio de Apache y habilítalo para que se inicie automáticamente al arrancar el servidor con los siguientes comandos:

```
sudo systemctl start apache2
sudo systemctl enable apache2
```

5. Verificar que Apache esté funcionando visitando la dirección IP(la cual puede ser antes configurada en Digital Ocean o elegida por el servidor entre las direcciones IP establecidas) de tu servidor en un navegador web. Deberías ver la página de inicio predeterminada de Apache.

6. Configura la seguridad de tu servidor y del software de servidor web según las mejores prácticas de seguridad.

_<center> <h2>Ejercicio Practico 1.</h3> </center>_

La empresa ACME, esta interesada en migrar su pagina web hacia la nube, para esto, solo cuentan inicialmente con un presupuesto de USD$ 25 💵 para una Prueba de conceptos of "Proof of Concept(PoC) y asi, evaluar si un modelo de Cloud 🌩️ se adapta a sus necesidades, actualmente su servidor web se encuentra sobre Ubuntu. 
Inicialmente, sus usuarios van a estar ubicados en la ciudad de New York. No hay ningun requerimiento en especifico respecto a los recursos del servidor (CPU, Memoria o disco). Como nota adicional, el servidor debe llevar un nombre personalizado y tener una(s) etiqueta(s) o "tags" para poder identificarlo. Sugerencia, podria usar `ACME` y `POC` (Proof of Concept) como etiquetas, tambien podrias agregar algo como `webserver`. 

1. .Configura un servidor web solo el protocolo `HTTP` sin nivel adicional de seguridad. Puedes utilizar `Apache` o `NGINX`
> 1.1 Intalacion de  Apache
```
Si se desea configurar un servidor web apache usando solo el protocolo HTTP  se deben hacer los siguientes pasos 

sudo apt update  (actualiza la lista de paquetes del  sistema operativo )

sudo apt install apache2 ( instala apache en nuestra consola )
```
>1.2  Instalar el servicio Apache.
```
sudo systemctl start apache2
```
>1.3 `Habilitar Apache` para que se inicie automáticamente al arrancar el servidor
```
sudo systemctl enable apache2
```
>1.4 Verificar el estado de Apache
```
sudo systemctl status apache2

Este comando te mostrará el estado actual de Apache en el servidor. Si Apache está en ejecución, verás información sobre su estado, incluyendo si está activo o inactivo, y algunos registros de actividad reciente. Si Apache no está en ejecución, te mostrará un mensaje indicando que el servicio no está corriendo.
```


2. Debe llevar una direccion IP (privada) dentro de los rangos calculados en el **Reto #3** (de ser posible) y debe ser accesible, al menos internamente. Debes encontrar al menos dos metodos de poder verificar que el servidor web esta funcional desde el mismo servidor o desde el exterior. Verifica la disponibilidad de tu IP Base y segmentos calculados.


Para este ejerccio decidi utilizar una **direccion IP** que estuvuese dentro del rango estipulado como red privada. 
 La direccion `IP 172.16.0.2/20` la cual por ser una red cuya mascara /20 podria tener hasta un maximo de 4096 subredes.

 Entre los metodos exitentes para verificar si un servidor esta funcional estan : 

 - **Comando ping** : Puedes usar el comando ping seguido de la dirección IP o el nombre de dominio del servidor para verificar si responde a las solicitudes de ping. Por ejemplo, ping `<dirección IP o nombre de dominio>`.

 - **Comando systemctl** : Puedes utilizar el comando `systemctl` para verificar el estado de los servicios en el servidor. Por ejemplo, systemctl status <nombre del servicio> te mostrará si un servicio específico está en ejecución (en este caso cargo la pagina de `Apache`).


 - **Navegador web**: Si el servidor aloja un sitio web, puedes intentar acceder a él desde un navegador web. Si el sitio web carga correctamente, nuestro servidor web estaria operativo.

Para verificar la disponibilidad de mi IP base use el comando : 
```
ping 172.16.0.2

 Si la dirección IP está disponible y responde a las solicitudes de ping, se vera mensajes indicando el tiempo de ida y vuelta de los paquetes. Si la dirección IP no está disponible, se vera  un mensaje indicando que los paquetes se han perdido.
```

3. Utiliza los creditos disponibles en **Digital Ocean**. Recuerda, que al encender un servidor (o cualquier servicio), por cada minuto que este encendido (esto depende del servicio), el mismo estara consumiendo los creditos gratis con los que ahora cuentas. Recuerda que hay un limite de presupuesto del cliente. Toma las medidas necesarias para que no se exceda el presupuesto del cliente.
 
 Entre las medidas necesarias disponibles para evitar el consumo excesivo en el presupuesto use el de apagar el servidor cuando no esta en uso sin embargo existen otras medidas para evitar el consumo excesivo de presupuesto como : 
  
  - **Establecer límites de gasto**: Utiliza las herramientas de control de costos proporcionadas por DigitalOcean para establecer límites de gasto en tu cuenta. Puedes configurar alertas y límites para ... evitar gastos inesperado.

  - **Monitoreo constante**: Utiliza las herramientas de monitoreo de costos de DigitalOcean para supervisar el gasto en recursos como servidores, almacenamiento y ancho de banda. Esto te permitirá identificar y abordar cualquier aumento inesperado en el consumo de recursos.

  - **Automatización de apagado**: Si tienes entornos de desarrollo o pruebas que no necesitan estar ... en funcionamiento todo el tiempo, considera automatizar el apagado de estos recursos fuera del horario laboral para reducir los costos.


4. Crea el / los acceso(s) necesario(s) para poder administrar el **droplet** remotamente

 Pasos para poder administrar el droplet de manera remota : 

 - **Paso 1**: Acceder a la cuenta de DigitalOcean a través de su sitio web.

- **Paso 2**: En el panel de control, seleccionar la sección "Droplets" y eligir el droplet al que deseas acceder de forma remota.

- **Paso 3**: Una vez que estemos en la página de detalles de nuestro droplet, buscamos la sección de "Acceso" o "Access" en el menú lateral.

- **Paso 4**: En la sección de "Acceso", encontraremos la opción de "Consola" que nos permite acceder a nuestro droplet a través de una interfaz de línea de comandos en el navegador. También encontraremos la opción de "Acceso SSH" que nos permite conectar a nuestro droplet a través de SSH.

- **Paso 6**: Copiamos la dirección IP de nuestro droplet desde la página de detalles y utilizamos el cliente SSH para conectarnos a nuestro droplet. Por ejemplo, en el terminal, escribimos ssh root@tu_direccion_ip y presionamos Enter. Reemplazamos "tu_direccion_ip" con la dirección IP real de tu droplet.

- **Paso 7**: Si es la primera vez que nos conectamos a nuestro droplet desde la  computadora, es posible que se nos pida confirmar la autenticidad de la conexión. Respondemos "yes" para continuar.

- **Paso 8**: Luego, se nos pedirá que ingresemos la contraseña de nuestro droplet. Una vez que ingresamos la contraseña, habremos establecido una conexión remota a nuestro droplet y podremos administrarlo a través de la línea de comandos.


5. Considera, que existe la posibilidad de que tengas que configurar el `firewall` interno del sistema operativo para permitir el tráfico del servidor web (entrante y saliente)

Para configurar el fireware desde una consola y asi permitir el trafico saliente y entrante se realizan los siguientes pasos 

- **Paso 1** : Verificar el estado actual del firewall.

Puedes verificar el estado actual del firewall ejecutando el siguiente comando:
``` 
sudo ufw status
```
Esto mostrara en que estado se encuentra el firewall y las reglas que estan en vigor .
 - **Paso 2**: Habilitar el firewall
 ```
 sudo ufw enable
 ```
 - **Paso 3**: Permitir el tráfico para servicios específicos

 ```
 sudo ufw allow 80/tcp (habilita el trafico entrante en el puerto 80 http)

 sudo ufw allow 443/tcp (habilita el trafico entrante para el puerto 443 HTTPS)
 ```
 - **Paso 4**: Verificar las reglas
 ```
 sudo ufw status
 ```

 - **Paso 5**: Habilitar el firewall para que se inicie en el arranque del sistema

 ```
 sudo ufw enable 
 ```

6. ¿Cuales son los comandos necesarios para verificar el estado del servicio asociado al servidor web?

Para verificar el estado del servicio asociado al servidor web, puedemos utilizar el siguiente comando en un sistema Linux:

```
sudo systemctl status apache2
```

8. Dentro de los conceptos de Cloud revisados previamente ¿Dentro de que modelo (`IaaS`, `PaaS`, `SaaS`,etc) encaja el servicio de **droplet**?

El servicio de "droplet" de DigitalOcean encaja dentro del modelo de infraestructura como servicio (IaaS).

#### Paso 2 (4.2)

1. ACME, ha decidido NO utilizar passwords para acceder a sus servidores, es decir, debes crear el procedimiento o pasos para poder acceder y administar el servidor web SIN uso de contraseñas.

Para administrar un servidor web sin el uso de contraseñas, puedemos utilizar la autenticación basada en llaves SSH. Los pasos para configurarla son los siguientes :

- **Generar un par de llaves SSH:**  En la máquina local se ejecuta el siguiente comando:

```
ssh-keygen 
```
- **Copiar la llave pública al servidor:**  Una vez generadas las llaves, copia la llaves pública a tu servidor web. Puedes hacerlo con el siguiente comando:

```
   
cat ~/.ssh/id_rsa.pub

```
- Iniciar sesión sin contraseña: 
```
ssh daniel@webserverAcmeny3
```

2. Adicionalmente, se debe idear una manera de automatizar el proceso de creacion de los **droplets** es decir. ¿Hay alguna manera de desplegar al menos tres (3) **droplets** en un mismo Datacenter de manera NO interactiva? Estos **droplets** deberan tener la misma configuracion del servidor web, es decir, una vez inicializados y creados, la disponibilidad del servicio web debe ser inmediata.

Para crear varios droplets de manera simultanea en el mismo Datacenter y con la misma configuracion se puede utilizar el siguiente comando :

```
doctl compute droplet create nombre-del-droplet --size tamaño-del-droplet --image imagen-del-droplet --region nombre-del-datacenter llave ssh 
```
Donde se debe tener en consideracion los siguientes argumentos 

- **Nombre-del-droplet**: el nombre del droplet que se ha elegido.

- **size** : tamaño del droplet a utilizar.

- **image** : es un instantanea que contiene el sistema operativo y su configuracion.

- **region**: lugar donde se encuentra el database del servidor 

- **llave ssh** : llave de nuestro servior o llave finger print ustilizada para ingresar a nuestro servidor y por ende para crear el droplet.

#### Ejercicio: Utilizando los datos anteriores crear 3 droplets que esten dentro del mismo datacenter ademas que tengan la misma configuracion.

>doctl compute droplet create ny1 ny2 ny3 --size s-1vcpu-1gb --image 146561575 --region nyc3


¿Crees que si el despliegue de estos tres servidores fuese distribuido en tres Datacenters distintos tendrias algun tipo de ventaja o desventaja? De ser asi ¿Como desplegarias los tres servidores de manera simultanea, con los mismos principios mencionados en tres datacenters distintos?  
*Pista*: Utiliza la siguiente [utilidad desarrollada](https://docs.digitalocean.com/reference/doctl/reference/compute/droplet/create/) por `Digital Ocean` para poder interactuar con las API del servicio de `droplet`

Desplegar los servidores en tres datacenters distintos puede tener ventajas y desventajas dependiendo de tus necesidades y el contexto específico de tu aplicación.
#### Ventajas:
- Redundancia geográfica: 

Al distribuir los servidores en diferentes datacenters, reduces el riesgo de que un evento localizado (como un corte de energía o un desastre natural) afecte a todos tus servidores al mismo tiempo.

- Mejor rendimiento para usuarios 
geográficamente dispersos: Si tus usuarios están distribuidos en diferentes regiones geográficas, desplegar servidores en datacenters cercanos a ellos puede mejorar la latencia y la velocidad de carga de tu aplicación.

#### Desventajas 

- Complejidad operativa: 
Mantener y coordinar servidores distribuidos en múltiples datacenters puede ser más complejo que tenerlos todos en un solo lugar.
- Costos adicionales:
 Desplegar en múltiples datacenters puede implicar costos adicionales, tanto en términos de infraestructura como de operaciones.

- Cumplimiento normativo:
 Algunas regulaciones requieren que los datos se almacenen en ubicaciones geográficas específicas. Distribuir los servidores en diferentes datacenters puede ayudarte a cumplir con estas regulaciones.