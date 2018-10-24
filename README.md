
# Taller Docker October Tech Rancagua 2018

Descripción

## Parte 1: presentación

## 1. ¿Qué es Docker?

Docker es una plataforma orientada a desarrolladores y administradores de sistemas para
desarrollar, desplegar y correr aplicaciones con contenedores. Para comprenderlo existen
dos conceptos claves: imágenes y contenedores.

Un contenedor es lanzado cuando se corre una imagen. Esta imagen es un paquete
ejecutable que incluye todo lo necesario para correr una aplicación: el código, funciones,
librerías, variables de entorno y archivos de configuración.

Un contenedor es una instancia de una imagen. La imagen se convierte en un proceso del sistema.
Puedes ver la lista de contenedores corriendo con el comando docker ps (en Linux).

### 2. ¿Como funciona?

En un principio contamos con una imagen base , sobre la que realizaremos los diferentes cambios. Tras confirmar estos cambios mediante la aplicación Docker , crearemos la imagen que usaremos. Esta imagen contiene únicamente las diferencias que hemos añadido con respecto a la base. Cada vez que queramos ejecutar esta imagen necesitaremos la base y las 'capas' de la imagen. Docker se encargará de acoplar la base, la imagen y las diferentes capas con los cambios para darnos el entorno que queremos desplegar para empezar a trabajar.

### 3. ¿Qué ventajas tiene?

El uso de contenedores es muy popular debido que a son:

* Flexible: Incluso las aplicaciones mas complejas pueden ser puestas en contenedores.
* Liviano: Los contenedores aprovechan y comparten el kernel del host.(1)
* Intercambiable: Puedes desplegar y actualizar sobre la marcha.
* Portable: Puedes construir en local, desplegar en la nube y correrlo en cualquier parte.
* Escalable: Puedes incrementar y distribuir automáticamente replicas de los contenedores. (2)

### 4. ¿Quién lo usa?

Empresas como Visa, Ebay, Spotify, Amazon o Uber emplean el uso de contenedores para su software, siendo pioneros en la adopción de nuevas tecnologías y métodos productivos en el desarrollo de aplicaciones.

## Parte 2: demo con Docker Compose

> Notas:
	- El usuario del servidor es "docker" y la contraseña "admin".
	- El comando SUDO no requiere contraseña.
	- Esta instalación esta orientada a arquitecturas x86_64 sobre Ubuntu 18.04. A pesar de que otros
	sistemas operativos(Windows, MacOS) y arquitecturas(armhf, s390x, ppc64le) están soportados, no serán
	cubiertas en esta guía.

### 1. Instalación de Docker CE(Community Edition).

Antes de instalar Docker CE por primera vez en tu equipo, necesitas agregar
el repositorio de Docker. Después de eso, podrás instalar y actualizar Docker desde el repositorio.

#### Configurar el repositorio:

##### 1. Actualiza los repositorios con APT.

	$ sudo apt update

##### 2. Instala los siguientes paquetes para permitir a APT trabajar sobre HTTPS.

	$ sudo apt install apt-transport-https ca-certificates curl software-properties-common

##### 3. Añade la llave GPG del repositorio oficial.

	$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

#### 4. Añade el repositorio APT.

	$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"

##### 5. Actualiza la base de datos de paquetes.

	$ sudo apt update

##### 6. Finalmente instala Docker.

	$ sudo apt install docker-ce

Ahora que Docker esta instalado, el daemon corriendo y el proceso a sido habilitado en el inicio. Revisa si se encuentra corriendo:

	$ sudo systemctl status docker

#### Ejecutar Docker sin el comando sudo (opcional).

##### 1. Añade tu usuario al grupo de Docker.

	$ sudo usermod -aG docker ${USER}

##### 2. Para aplicar los cambios cierra sesión y vuelve a entrar con el siguiente comando.

	$ su - ${USER}

##### 3. Para añadir un usuario al grupo de Docker si no esta logeado usa el siguiente comando.

	$ sudo usermod -aG docker username

#### Desintalar Docker-CE

##### 1. Desinstalar el paquete Docker.

##### 2. Imágenes, contenedores, volúmenes o cualquier archivo de configuración modifica en tu equipo no son removidos automáticamente. Para borrar las imágenes, contenedores y volúmenes usa el comando:

	$ sudo rm -rf /var/lib/docker

Para cualquier archivo de configuración editado debes eliminarlo manualmente.

### 2. Explicación y descarga de imágenes

#### Instalación de Docker Compose

##### 1. Debes revisar la [version actual](https://github.com/docker/compose/releases "Versiones") y si es necesario, actualizar el comando mas abajo.

	$ sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose

##### 2. Otorgar permisos a docker-compose

	$ sudo chmod +x /usr/local/bin/docker-compose

#### Corriendo un contenedor con docker-compose.

##### 1. Primero, creamos un directorio para el archivo YAML y lo movemos dentro de el.

	$ mkdir hello-world
	$ cd hello-world

##### 2. Crear el archivo docker-compose.yml (se puede usar un editor como nano, vim, vscode, etc)

	$ nano docker-compose.yml

##### 3. Pon el siguiente contenido dentro del archivo, guardalo y sal del editor:

	my-test:
		image: hello-world

Es importante revisar que la indentación este correcta, pues de lo contrario arrojará error.

##### 4. Finalmente para levantar la imagen creada ejecutamos:

	$ docker-compose up

#### Comandos útiles:

##### 1. Para listar las imágenes instaladas usamos:

	$ docker images

##### 2. Para listar los contenedores que se están ejecutando en tiempo real usamos:

	$ docker ps

##### 3. Para mostrar todos los contenedores

	$ docker ps -a

##### 4. Para eliminar un contenedor usamos:

	$ docker rm ID_DE_LA_IMAGEN

##### 5. Para eliminar una imagen usamos:

	$ docker rmi NOMBRE_IMAGEN
