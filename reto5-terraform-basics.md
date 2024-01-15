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

7. ¿Que son las expresiones dentro de Terraform? Explica el concepto de tipo y valores. Da ejemplos de los tipos string, number y bool
Segun esta documentacion, explica brevemente a que se le conoce como "referencias a valores".

8. ¿Puede Terraform resolver el problema inicial de nuestro cliente ACME?

9. ¿Que pasaria si ACME, en un tiempo indeterminado, decide migrar su aplicacion a otro proveedor de Cloud tal como Amazon Web Service o Microsoft Azure? ¿Puede seguir utilizando Terraform? ¿Existe una herramienta que pueda sustituir el uso de Terraform? Si la respuesta es si. ¿Cuales son las ventajas y desventajas?

## Paso 2 (5.2)