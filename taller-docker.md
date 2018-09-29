# Taller Docker October Tech Rancagua 2018

Descripción
   
## Parte 1: presentación

### 1. ¿Qué es Docker?

Docker es una plataforma orientada a desarroladores y administradores de sistemas para
desarrollar, desplegar y correr aplicaciones con contenedores. Para comprenderlo existen
dos conceptos claves: imagenes y contenedores.

Un contenedor es lanzado cuando se corre una imagen. Esta imagen es un paquete
ejecutable que incluye todo lo necesario para correr una aplicacion: el codigo, funciones,
librerias, variables de entorno y archivos de configuracion.

Un contenedor es una instancia de una imagen. La imagen se convierte enn un proceso del sistema.
Puedes ver la lsita de contenedores corriendo con el comando docker ps (en Linux).

El uso de contenedores es muy popular debido que a son:

* Flexible: Incluso las aplicaciones mas complejas pueden ser puestas en contenedores.
* Liviano: Los contenedores aprovechan y comparten el kernel del host.(1)
* Intercambiable: Puedes desplegar y actualizar sobre la marcha.
* Portable: Puedes construir en local, desplegar en la nube y correrlo en cualquier parte.
* Escalable: Puedes incrementar y distribuir automaticamente replicas de los contenedores. (2)

Conceptos:
* (1) Kernel:
* (1) Host:
* (2) Escalabilidad Horizontal:

### 2. ¿Como funciona?



### 3. ¿Qué ventajas tiene?
### 4. ¿Quién lo usa?
### 5. ¿Como mejora la productividad?
### 6. Ecosistema Docker
### 7. Workflow

## Parte 2: demo con Docker Compose

> Notas: 
	- El usuario del servidor es "docker" y la contraseña "admin".
	- El comando SUDO no requiere contraseña.
	- Esta instalacion esta orientada a arquitecturas x86_64 sobre Ubuntu 18.04. A pesar de que otros
	sistemas operativos(Windows, MacOS) y arquitecturas(armhf, s390x, ppc64le) estan soportados, no seran
	cubiertas en esta guía.

### 1. Instalación de Docker CE(Community Edition).

Antes de install Docker CE por primera vez en tu equipo, necesitas agregar
el repositorio de Docker. Despues de eso, podras instalar y actualizar Docker desde el repositorio.

#### Configurar el repositorio:

##### 1. Actualiza los repositorios con APT.
	$ sudo apt update

##### 2. Instala los siguientes paquetes para permitir a APT trabajar sobre HTTPS.

	$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

##### 3. Añade la llave GPG oficial de Docker.

	$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

Verifica que tienes la llave con la huella "9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88", buscando
los ulitmos 8 caracteres de la huella.

	$ sudo apt-key fingerprint 0EBFCD88

	pub   4096R/0EBFCD88 2017-02-22
    	Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
	uid                  Docker Release (CE deb) <docker@docker.com>
	sub   4096R/F273FCD8 2017-02-22

##### 4. Usa el siguiente comando para configurar el repositorio "estable". Siempre necesitaras el repositorio estable, incluso si necesitas instalar Docker desde los repositorio "edge" o "test". Para añadir el repositorio "edge" o "test"(o los dos) añade la palabra "edge" o "test" despues de la palabra "stable" en los comandos siguientes.

> Nota: El subcomando[...]

	$ sudo add-apt-repository \
	   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
	   $(lsb_release -cs) \
	   stable"

Leer Acerca de los canales "stable" y "edge". (Poner link)

#### Instalar Docker CE.

##### 1. Actualiza los repositorios con APT.

	$ sudo apt update

##### 2. Instala la ultima version de Docker CE.

	$ sudo apt-get install docker-ce

##### 3. Para instalar una versión especifica de Docker CE, lista las versiones disponibles en el repo,  selecionala e instala.

##### 4. Verifica que Docker esta correctamente instalado corriendo la imagen "hello-world".

	$ sudo docker run hello-world

#### Desinstalar Docker CE.

##### 1. Desinstalar el paquete Docker.

##### 2. Imagenes, contenedores, volumenes o cualquier archivo de configuracion modifica en tu equipo no son removidos automaticamente. Para borrar las imagenes, contenedores y volumenes usa el comando:

	$ sudo rm -rf /var/lib/docker

Para cualquier archivo de configuracion editado debes eliminarlo manualmente.

### 2. Explicación y descarga de imagenes
### 3. Instalación de Docker Compose
### 4. Creación de archivo docker-compose.yml
### 5. Despliegue de aplicación

