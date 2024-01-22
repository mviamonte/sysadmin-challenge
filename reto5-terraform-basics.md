# Reto #5.  Automatizacion

La compañia ACME ha quedado totalmente convencida de que sus proximos pasos van a ser migrar su servidor web a la nube. Felicitaciones!! Por ahora, ACME decidio quedarse en el mismo proveedor de nube Digital Ocean Sin embargo, con la intencion de que la infraestructura (droplets) puede ser manejada por un sistema de control de versiones (VCS) como Git / Github ellos han decidido utilizar tecnologias basadas en IaC (Infrastructure as a Code). Una de ellas, es Terraform de Hashicorp. Asi que manos a la obra❗❗❗ Antes de hacer o escribir cualquier linea de código, vayamos investigando lo siguiente:

## Paso 1 (5.1)

1. ¿Que es IaC y cuales son sus principales características?


  Es una práctica en la que la infraestructura de TI se gestiona y provisiona a través de código y scripts, en lugar de realizar configuraciones manuales. Es como darle instrucciones a una computadora para que configure toda la infraestructura de una empresa usando un lenguaje de programación. Esto hace que la configuración sea más rápida, menos propensa a errores y fácil de entender para todos en el equipo.

Sus principales caracteristicas son :

- Automatizacion :  Permite la automatización de la creación, configuración y gestión de la infraestructura, lo que reduce errores y aumenta la eficiencia.

- Control de versiones: El código que define la infraestructura se puede gestionar a través de sistemas de control de versiones como Git, lo que facilita el seguimiento de cambios y la colaboración entre equipos.

- Consistencia: Al definir la infraestructura como código, se garantiza que los entornos sean consistentes y reproducibles, lo que facilita el despliegue y la gestión de la infraestructura.

- Escalabilidad: Permite escalar la infraestructura de manera más ágil y predecible, ya que los recursos se pueden aprovisionar y configurar de forma programática.


- Documentación viva: El código que define la infraestructura sirve como documentación viva, ya que describe de manera detallada cómo se configuran los recursos de infraestructura.

2. Ademas de Hashicorp Terraform ¿Que otras herramientas ofrecen capacidades similares?

- AWS cloud formation
- Google Cloud Deployment Manager 
- Azure Resource Manager 
- Pulumi

3. ¿Que tipo de lenguaje es Terraform?

Terraform utiliza un lenguaje de dominio específico (DSL, por sus siglas en inglés) para definir la infraestructura como código. Este lenguaje, llamado HCL (HashiCorp Configuration Language), está diseñado para ser fácil de leer y escribir, permitiendo a los usuarios describir la infraestructura y sus relaciones de manera clara y concisa.

4. ¿Cual es la principal utilidad de Terraform?
Menciona los comandos principales utilizados en Terraform.

La principal utilidad de Terraform es la automatización de la infraestructura, permitiendo a los equipos definir, configurar y desplegar recursos de infraestructura de forma predecible y repetible.

comandos :
```
- init : "inicia el modulo de trabajo en terraform preparando el directorio de trabajo para utilizar otros comandos.

- plan : muestra los cambios que terraformn realizara en la infraestructura, permitiendo revisarlos antes de aplicarlos.
 
- apply : ejecuta toda la configuracion y crea la infraestructura de la plataforma 

- destroy : elimina todos los recursos definidos en los archivos de configuracion de terraform.

```

5. ¿Cuales son los componentes principales en una configuracion de Terraform? Escribe el detalle de los componentes bases.
```
* Archivos de configuracion (.tf): contienen la descripcion de la infraestructura que se desea gestionar.

* Proveedores: Son componentes gestionan recursos del proveedor  y  que permiten a terraform interactuar con otros proveedores de servicios de la nube como AWS, Azure , Google Cloud, VMware, entre otros.

* Recursos: Los recursos representan los componentes de la infraestructura que se desean gestionar, como instancias de máquinas virtuales, bases de datos, redes, entre otros.

* Variables: Las variables en Terraform permiten parametrizar la configuración, lo que facilita la reutilización y la personalización de los archivos de configuración.

* Salidas: Las salidas permiten exponer información sobre los recursos creados o modificados por Terraform, lo que puede ser útil para otros sistemas o para el usuario final.
```
6. Indaga en el detalle de los siguientes conceptos de Terraform: Plugin, Providers, variables, data, resources y terraform state, Dentro del concepto de variables, investiga adicionalmente el orden de prioridad de las mismas.

```
- plugin :Es  un componente de software que extiende las capacidades de una aplicación principal, en este caso Terraform, permitiéndole interactuar con distintos proveedores de servicios en la nube de manera consistente y eficiente.

- Providers: es un componente fundamental que permite a Terraform interactuar con distintos proveedores de servicios en la nube, como AWS, Azure, Google Cloud, entre otros. Cada proveedor es un plugin que proporciona a Terraform la capacidad de gestionar los recursos específicos de ese proveedor.

- Variables y su Orden de prioridad : Las variables son utilizadas para parametrizar la configuración y permitir la reutilización de código, su orden de priodidad :

1. variables definidas en los archivos de configuracion: Estas variables pueden tener un valor por defecto o ser definidas como obligatorias.

2. Archivos de variables: Estos archivos pueden ser utilizados para proporcionar valores específicos a las variables en diferentes entornos o situaciones.

3. Variables de entorno :  Si una variable no está definida en los archivos de configuración o en archivos de variables, Terraform buscará si existe una variable de entorno con el mismo nombre y la utilizará si está presente.
 
4. Flags en línea de comandos: Al ejecutar comandos de Terraform, se pueden proporcionar valores para las variables directamente en la línea de comandos utilizando flags específicos. 

- data : Se utiliza para consultar y obtener información sin necesariamente crear o modificar recursos.

- resouces: Son utilizados para definir y gestionar los componentes de la infraestructura que se desean crear, modificar o eliminar en un proveedor de infraestructura específico, permitiendo una gestión eficiente y escalable de la infraestructura como código.

- terraform state: se refiere al estado actual de la infraestructura gestionada por Terraform. Este estado incluye información sobre los recursos que Terraform está gestionando, como sus atributos, relaciones y metadatos
```

7. ¿Que son las expresiones dentro de Terraform? Explica el concepto de tipo y valores. Da ejemplos de los tipos string, number y bool
Segun esta documentacion, explica brevemente a que se le conoce como "referencias a valores".

 Las expresiones son utilizadas para representar y manipular valores
 Existen diferentes tipos de valores, como string (cadena de texto), number (número) y bool (booleano). Cada tipo de valor tiene sus propias reglas y operaciones asociadas. A continuación, algunos ejemplos de estos tipos de valores:
  ```
- string: (hola mundo)
- number: 82
- bool: true
 ```

8. ¿Puede Terraform resolver el problema inicial de nuestro cliente ACME?

si, ya que con el uso de terraforn no solo se pueden automatizar los procesos de contruccion de servidores sino que tambien se podria usar el recurso de control de versiones del mismo a travez de Git, lo cual tambien facilitaria la colaboracion entre equipos.

9. ¿Que pasaria si ACME, en un tiempo indeterminado, decide migrar su aplicacion a otro proveedor de Cloud tal como Amazon Web Service o Microsoft Azure? ¿Puede seguir utilizando Terraform? ¿Existe una herramienta que pueda sustituir el uso de Terraform? Si la respuesta es si. ¿Cuales son las ventajas y desventajas?

En el caso que ACME quiera migrar podria hacerlo sin ningun problema ya que Terraform es compatibe con multiples operadores de servicio en la nube. lo que significa que los archivos de configuracion pueden ser adaptados a otro entorno de infraestructura.

En cuanto a una herramienta que pueda sustituir el uso de Terraform, existen otras herramientas de infraestructura como código, como AWS CloudFormation, Azure Resource Manager, Google Cloud Deployment Manager, entre otras. Sin embargo, cada una de estas herramientas tiene sus propias ventajas y desventajas en comparación con Terraform.

Algunas ventajas de Terraform incluyen su sintaxis clara y legible, su soporte para múltiples proveedores de servicios en la nube, su comunidad activa y su capacidad para gestionar recursos de forma modular y reutilizable.
Por otro lado, algunas desventajas de Terraform podrían incluir una curva de aprendizaje inicial para aquellos que no están familiarizados con su sintaxis y conceptos, así como posibles limitaciones en la gestión de recursos específicos de ciertos proveedores de servicios en la nube.


## Paso 2 (5.2)

Teniendo claros todos los conceptos, hagamos una pequeña prueba con `Terraform`. Recuerda, crear un procedimiento paso a paso incluyendo las salidas de los comandos que consideres necesarios, comandos utilizados, etc.

1. Instalar la version mas reciente de `terraform` en tu computadora.

 ```
sudo snap install terraform --classic
 ```

2. Crea un directorio llamado `proyecto_final`

 ```
 mkdir proyecto_final 
 ```


3. En el directorio creado anteriormente, crea un archivo llamado `main.tf`. Este archivo debe llevar la configuracion con la capacidad de crear un recurso `random` (este archivo realmente se puede llamar `pepito.tf`y `Terraform` lo entendera igual). La intencion de este recurso es crear una cadena de texto (string) aleatoria en base a los argumentos que le proporciones. [Revisa esta documentacion para entender el ejemplo](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/string). [^1] 

 ```
 touch main.tf
 ```
  - Usando Visual Studio Code 
  En el archivo  `main.tf `:
   ```
  terraform {
  required_providers {
    random = {
      source = "hashicorp/random"
      version = "3.6.0"
    }
  }
}
 ```
 - Nota: Aca ya se creo la instancia para una configuracion genral o random en terraform 

4. Crea un archivo llamado `versions.tf` dentro del mismo directorio y agrega los bloques de codigo correspondientes que te permitan crear el recurso anterior utilizando el `provider` random, en el mismo link anterior pero yendo a la documentacion del [provider](https://registry.terraform.io/providers/hashicorp/random/latest/docs) en si, valida como se utiliza este `provider`. Especificamente, revisa el boton morado en la parte superior que indica **USE PROVIDER**

 ```
 touch versions.tf
  ```
   ```
provider "random" {
  # No se requiere ninguna configuración específica para el proveedor "random" en este ejemplo
}

resource "random_string" "name" {
  length = 12
  special = true
}
```
- Nota : Aca ya se leindico a terraform cual seria el poovedor ademas del recurso a utilizar en este caso es random_string el cual imprimira cualquier conjunto de textos aleatorio, ademas otra sentencia como la longitud y si se desearia algun caracter especial (especial =true)

5. Utiliza todos los comandos de `terraform` necesarios, para que tu configuracion, pueda crear satisfactoriamente, una cadena del tipo random de acuerdo a lo expresado en el archivo `main.tf`. Recuerda que necesitas el contenido de ambos archivos, es decir el de `main.tf` y el de `versions.tf`
```
terraform init
terraform plan
terraform apply
```

6. ¿Cual secuencia basica de comandos `terraform` te permiten validar la creacion de ese recurso `random` dentro de tu proyecto?
```
terraform show: se utiliza para inspeccionar el estado actual de la infraestructura gestionada por Terraform.
terraform state list :  Muestra una lista de todos los recursos gestionados por Terraform y sus direcciones en el estado
```
7. Examina y analiza, de haber sido ejecutado satisfactoriamente, la salida de cada uno de estos tres comandos de la secuencia básica de comandos `terraform`

8. Luego de haber ejecutado satisfactoriamente los tres comandos básicos de `terraform`. ¿Notas alguna diferencia dentro del directorio `proyecto_final`? Comenta cuales archivos o directorios llaman tu atencion y agrega tus conclusiones. 

Si, despues de ejecutar el comando `terraform apply` se creo un archivo en el directorio `proyecto_final` 
Terraform crea un archivo llamado `terraform.tfstate` en el directorio de trabajo. Este archivo es el estado actual de la infraestructura, incluyendo información sobre los recursos que Terraform ha creado, modificado o eliminado...

