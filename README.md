# Prueba Técnica – Arquitectura de Microservicios

Solución desarrollada con **Java 21, Spring Boot y Spring Cloud**, orientada a la gestión de clientes, cuentas y movimientos mediante una arquitectura de microservicios.

La solución incorpora descubrimiento de servicios, enrutamiento centralizado, persistencia en PostgreSQL, infraestructura de mensajería con RabbitMQ y despliegue automatizado mediante Docker Compose.

## Arquitectura

La solución está compuesta por los siguientes servicios e infraestructura:

| Componente | Descripción |
|---|---|
| **Discovery Server** | Registro y descubrimiento de microservicios mediante Netflix Eureka. |
| **API Gateway** | Punto de entrada para las solicitudes HTTP y enrutamiento hacia los servicios correspondientes. |
| **Microservicio de Clientes** | Gestión de personas y clientes. |
| **Microservicio de Cuentas** | Gestión de cuentas y movimientos bancarios. |
| **PostgreSQL** | Persistencia de datos en bases de datos independientes. |
| **RabbitMQ** | Infraestructura de mensajería para la comunicación asíncrona. |

## Repositorios de código fuente

Cada microservicio se encuentra desarrollado y versionado en su propio repositorio de GitHub.

| Microservicio | Repositorio |
|---|---|
| Discovery Server | [RetoTecnicoDiscover](https://github.com/IsmaelBoada/RetoTecnicoTataDiscover) |
| API Gateway | [RetoTecnicoGateway](https://github.com/IsmaelBoada/RetoTecnicoTataGateway) |
| Cuentas y Movimientos | [RetoTecnicoCuentasService](https://github.com/IsmaelBoada/RetoTecnicoTataCuentasService) |
| Clientes y Personas | [RetoTecnicoClienteService](https://github.com/IsmaelBoada/RetoTecnicoTataClienteService) |

## Entrega de la solución

La solución completa se entrega mediante un archivo ZIP que contiene los proyectos y los recursos necesarios para desplegar y probar la arquitectura.

El paquete incluye:

- Código fuente de los cuatro microservicios.
- Archivo `docker-compose.yml` para la orquestación de los servicios.
- Archivo `init.sql` para la creación inicial de las bases de datos.
- Colección de Postman para probar los endpoints de la API.
- Archivos de configuración necesarios para el despliegue.
- Documentación con las instrucciones de ejecución.

## Tecnologías utilizadas

- Java 21
- Spring Boot
- Spring Cloud Netflix Eureka
- Spring Cloud Gateway
- Spring Data JPA / Hibernate
- PostgreSQL
- RabbitMQ
- Docker
- Docker Compose
- Maven
- Postman

## Requisitos previos

Para ejecutar la solución se requiere:

- Docker Desktop o Docker Engine.
- Docker Compose.
- Conexión a internet para descargar las imágenes Docker necesarias.

No es necesario iniciar cada microservicio manualmente desde el IDE si se utiliza el despliegue mediante Docker Compose.

## Instrucciones de despliegue

### 1. Obtener la solución

Descargar y descomprimir el archivo ZIP llamado microservicios.

### 2. Configurar el entorno

Abrir una terminal en el directorio donde se encuentra el archivo `docker-compose.yml`.

Configurar las variables de entorno necesarias según los archivos incluidos en la solución, si corresponde.

### 3. Levantar los servicios

Ejecutar el siguiente comando:

```bash
docker compose up -d
```

Docker Compose iniciará los contenedores y gestionará las dependencias entre los servicios. La creación de las bases de datos se realiza mediante la configuración de inicialización incluida en el paquete, sin necesidad de ejecutar manualmente las instrucciones SQL.

### 4. Verificar el estado de los contenedores

```bash
docker compose ps
```

### 5. Consultar los registros de ejecución

```bash
docker compose logs -f
```

### 6. Detener los servicios

```bash
docker compose down
```

## Puertos de acceso

| Componente | Puerto |
|---|-------:|
| API Gateway |   8080 |
| Discovery Server |   8761 |
| Microservicio de Clientes |   9020 |
| Microservicio de Cuentas |    9021 |
| PostgreSQL |   5432 |
| RabbitMQ AMQP |   5672 |
| RabbitMQ Management |  15672 |

### Interfaces disponibles

- **API Gateway:** http://localhost:8080
- **Eureka Dashboard:** http://localhost:8761
- **RabbitMQ Management:** http://localhost:15672

El acceso a RabbitMQ Management requiere las credenciales definidas en la configuración del despliegue.

## Pruebas de la API con Postman

Se incluye una colección de Postman con solicitudes para probar los endpoints implementados en los microservicios.

### Cómo ejecutar las pruebas

1. Levantar la arquitectura mediante Docker Compose.
2. Abrir Postman.
3. Importar el archivo de la colección incluido en el ZIP.
4. Verificar que la URL base de las solicitudes corresponda al API Gateway.
5. Ejecutar las solicitudes y comprobar las respuestas de los endpoints.

La URL base del Gateway es:

```text
http://localhost:8080
```

## Consideraciones técnicas

- Separación de responsabilidades mediante microservicios.
- Registro y descubrimiento de servicios con Netflix Eureka.
- Enrutamiento centralizado mediante Spring Cloud Gateway.
- Persistencia de datos en PostgreSQL.
- Bases de datos independientes para los microservicios de clientes y cuentas.
- Infraestructura de mensajería con RabbitMQ.
- Automatización del despliegue mediante Docker Compose.
- Pruebas de endpoints mediante Postman.

## Autor

Desarrollado por **Ismael Boada** como parte de una prueba técnica de backend con Java y Spring Boot.
