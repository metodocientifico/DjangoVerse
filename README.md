
# DjangoVerse

DjangoVerse es un ecosistema completo para el desarrollo de aplicaciones web en Django con una infraestructura escalable y extensible. Este stack de Docker incluye Django, PostgreSQL, Redis, Celery para tareas asíncronas, Nginx como proxy inverso, Adminer para administración de bases de datos, y Swagger-UI para la documentación y prueba de APIs.

## Estructura del proyecto

```bash
DjangoVerse/
├── app/
│   ├── manage.py                 # Script de administración de Django
│   ├── myapp/                    # Carpeta principal de la app Django
│   │   ├── __init__.py
│   │   ├── settings.py           # Configuración de Django
│   │   ├── urls.py               # Rutas de la aplicación
│   │   ├── wsgi.py               # Configuración para servidores WSGI
│   │   ├── asgi.py               # Configuración para servidores ASGI
│   └── Dockerfile                # Dockerfile para el contenedor Django
├── nginx/
│   └── nginx.conf                # Configuración de Nginx como proxy inverso
├── swagger/
│   └── swagger.yaml              # Especificación de API para Swagger-UI
├── docker-compose.yml            # Archivo de configuración de Docker Compose
├── requirements.txt              # Dependencias de Python para el proyecto
└── .env                          # Variables de entorno para PostgreSQL
```

## Servicios incluidos

Este stack incluye los siguientes servicios:

1. **Django**: El framework principal para el desarrollo web.
2. **PostgreSQL**: Base de datos relacional.
3. **Redis**: Almacenamiento en caché y backend para Celery.
4. **Celery**: Sistema de tareas asíncronas integrado con Redis.
5. **Nginx**: Proxy inverso para manejar el tráfico hacia el servidor Django.
6. **Adminer**: Herramienta para la administración visual de bases de datos.
7. **Swagger-UI**: Interfaz para documentar y probar las APIs.

## Requisitos previos

Para poder utilizar este stack, necesitas tener instalados los siguientes programas en tu máquina:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Instalación

1. **Clonar el repositorio**:

```bash
git clone https://github.com/tu-repo/DjangoVerse.git
cd DjangoVerse
```

2. **Crear un entorno de Python y gestionar las dependencias**:

Dentro del directorio `app`, tenemos un archivo `requirements.txt` donde se encuentran las dependencias de Python necesarias:

```bash
Django==4.2
psycopg2==2.9.3
celery==5.2.7
redis==4.3.3
```

Estas dependencias se instalan automáticamente cuando se construyen los contenedores con Docker.

3. **Configurar las variables de entorno**:

Asegúrate de que el archivo `.env` contenga las siguientes variables:

```bash
POSTGRES_DB=django_db
POSTGRES_USER=django_user
POSTGRES_PASSWORD=django_password
```

4. **Construir y levantar los contenedores**:

Ejecuta el siguiente comando para construir y levantar los servicios:

```bash
docker-compose up --build
```

5. **Acceso a los servicios**:

- Django estará disponible en: `http://localhost:8000`
- Adminer estará disponible en: `http://localhost:8080`
- Swagger-UI estará disponible en: `http://localhost:8081`

## Uso

- Puedes empezar a desarrollar en el directorio `app`, ya que todo lo que hagas en tu máquina local se reflejará dentro del contenedor.
- Utiliza Adminer para administrar tu base de datos PostgreSQL.
- Swagger-UI está listo para documentar y probar tus APIs.

## Tareas Asíncronas

Celery está configurado para funcionar con Redis. Para ejecutar tareas asíncronas, asegúrate de tener definidas las tareas en tu aplicación Django y ejecuta:

```bash
docker-compose run celery
```

## Contribución

Este proyecto es escalable y extensible. Si quieres agregar más servicios o mejorar la infraestructura, siéntete libre de enviar PRs o sugerencias.
