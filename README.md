# Remake-Practica1-SRI

## Descripción 📋

Queremos automatizar la creación de la siguiente infraestructura usando Vagrant, el esquema que queremos desarrollar, que vemos en la imagen, tiene las siguientes características:

Es escenario tiene dos máquinas:

* `router`: que está conectada a una red pública y a una red privada (muy aislada).
* `cliente`: esta máquina está conectada a la misma red privada que la máquina anterior.
* La máquina `router` debe salir por la red pública. **Esta máquina no va a utilizar eth0 para acceder al exterior**.

Queremos configurar el escenario con ansible, para que cumpla lo siguiente:

* La máquina `cliente` debe tener acceso a internet. Para ello debe salir por `eth1` y la máquina `router` debe estar configurada para enrutar las peticiones de las máquinas conectadas a la red privada. Del mismo modo, `eth0` sólo se utiliza para acceder con `vagrant ssh`. Debes pensar qué configuración debe tener la máquina cliente: puerta de enlace, configuración dns,...
* La máquina `cliente` tendrá un servidor web instalado, la máquina `router` hará DNAT para que podamos acceder a la página usando su IP pública.

La receta ansible debe tener al menos 4 roles:

* `common`: Estas tareas se deben ejecutar en **todos** los nodos: actualizar los paquetes y añadir tu clave pública a la máquinas para poder acceder a ellas con ssh. ¿Existe algún módulo de ansible que te permita copiar claves públicas?.
* `router`: Todas las tareas necesarias para configurar `router` cómo router-nat y que salga a internet por `eth1`. Las configuraciones deben ser permanentes. ¿Existe algún módulo de ansible que te permita ejecutar `sysctl`?.
* `cliente`: Todas las tareas necesarias para que **las máquinas conectadas a la red privada** salgan a internet por `eth1`.
* `web`: Las tareas necesarias para instalar y configurar un servidor web con una página estática en la máquina `cliente`.

## Entrega 📋

1. Entrega la URL del repositorio GitHub donde has alojado todos los ficheros.
2. Entrega una captura de pantalla accediendo por ssh a las dos máquinas (**sin utilizar `vagrant ssh`, es decir sin hacer conexiones a `eth0`**). Usa la opción `-A`  de ssh para acceder al `cliente`.
3. Entrega capturas de pantalla donde se vean las puertas de enlaces de los dos equipos.
4. Entrega capturas de pantalla donde se vean las máquinas haciendo ping al exterior.
5. Entrega una captura de pantalla donde se vea un acceso a la página web alojada en la máquina `cliente`.
6. Estudia la forma de integrar la receta ansible en vagrant, de tal manera que una vez se cree el escenario se ejecuta la configuración.

🔗 **Información de la tarea extraída de: https://fp.josedomingo.org/sri2223/1_iac/practica.html**

## Autor ✒️

* **Juan Jesús A. S.** - *Gonzalo Nazareno*