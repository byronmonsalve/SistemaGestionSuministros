# Sistema de Gestión de Suministros - DESARROLLO FULLSTACK I_006V

## Descripción del contexto

Este proyecto fue desarrollado para la asignatura Desarrollo FullStack I y simula el sistema de control de suministros tecnológicos de la empresa ficticia **CloudTech**, encargada de administrar múltiples centros de datos.

La solución implementa una arquitectura basada en microservicios para gestionar el inventario de componentes físicos utilizados en la reparación y mantenimiento de servidores. El sistema permite registrar, consultar, actualizar y controlar el stock de los suministros, aplicando reglas de negocio que garantizan la integridad de los datos y el cumplimiento de las restricciones establecidas.

Como parte del proceso, cuando un componente crítico posee menos de tres unidades disponibles, el microservicio de suministros realiza una consulta al microservicio de proveedores para verificar si existen órdenes de compra en tránsito, entregando esta información junto con la respuesta al usuario.

Además, el sistema incorpora validaciones de datos, manejo de excepciones, registro de movimientos de inventario (logs de auditoría), documentación mediante Swagger OpenAPI y pruebas unitarias, siguiendo una arquitectura en capas (Controller, Service y Repository) y buenas prácticas de desarrollo de software.

---

## Integrantes

- Byron Monsalve
- Danilo Núñez
- Juan Opazo

---

# Microservicios

## api.suministros

Microservicio encargado de administrar el inventario de componentes tecnológicos.

### Funcionalidades

- Registrar suministros.
- Consultar todos los suministros.
- Buscar suministros por fabricante.
- Actualizar suministros.
- Eliminar suministros según las reglas de negocio.
- Consultar al microservicio de proveedores cuando el stock es crítico.

---

## api.proveedores

Microservicio encargado de administrar las órdenes de compra en tránsito de los fabricantes.

### Funcionalidades

- Consultar órdenes de compra por fabricante.
- Entregar información al microservicio api.suministros mediante comunicación REST.

---

# Endpoints

### api.suministros

| Método | Endpoint | Descripción |
|---------|----------|-------------|
| GET | /api/v1/suministros | Obtiene la lista de todos los suministros registrados. |
| GET | /api/v1/suministros/fabricante/{idFabricante} | Consulta un suministro utilizando el identificador del fabricante. |
| POST | /api/v1/suministros | Registra un nuevo suministro en el inventario. |
| PUT | /api/v1/suministros/{id} | Actualiza la información de un suministro existente. |
| DELETE | /api/v1/suministros/{id} | Elimina un suministro del inventario, siempre que las reglas de negocio lo permitan. |

### api.proveedores

| Método | Endpoint | Descripción |
|---------|----------|-------------|
| GET | /api/v1/ordenes/{idFabricante} | Consulta las órdenes de compra en tránsito asociadas a un fabricante específico. Si existen órdenes registradas, devuelve la información correspondiente; en caso contrario, responde con un estado HTTP 404 (Not Found). |

---

## Documentación Swagger

### api.suministros

...

### api.proveedores

...

---

## Ejecución local

### Requisitos

- Java JDK 21
- Maven
- Oracle /  SQL Developer
- IntelliJ IDEA
- Git

### Pasos para ejecutar

1. Clonar el repositorio. (El enlace en las carpetas de su respectiva API)

2. Crear las bases de datos correspondientes para ambos microservicios.

3. Configurar el archivo application.properties de cada microservicio.

Modificar:

- URL de conexión
- Usuario
- Contraseña
- Puerto del servidor

4. Ejecutar primero el microservicio **api.proveedores**.

5. Ejecutar posteriormente el microservicio **api.suministros**.

6. Acceder a la documentación Swagger desde el navegador utilizando los enlaces indicados anteriormente.

---

## Tecnologías utilizadas

- Java 21
- Spring Boot
- Spring Data JPA
- Hibernate
- Maven
- MySQL
- Swagger OpenAPI
- Git
- GitHub
- IntelliJ IDEA

---

## Arquitectura

El proyecto utiliza una arquitectura basada en microservicios y el patrón **Controller – Service – Repository (CSR)**, separando las responsabilidades de presentación, lógica de negocio y acceso a datos para facilitar el mantenimiento y escalabilidad de la aplicación.
