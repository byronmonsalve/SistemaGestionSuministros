# Sistema de Gestión de Suministros -    

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

## Microservicios implementados

### api.suministros

Microservicio encargado de administrar el inventario de componentes tecnológicos.

**Funciones principales:**

- Registrar suministros.
- Consultar suministros.
- Actualizar información de suministros.
- Eliminar suministros (cuando las reglas de negocio lo permiten).
- Verificar el stock disponible.
- Consultar información del microservicio de proveedores cuando el stock es menor a 3 unidades.

### api.proveedores

Microservicio encargado de administrar la información de proveedores e importaciones.

**Funciones principales:**

- Registrar proveedores.
- Consultar proveedores.
- Actualizar información de proveedores.
- Eliminar proveedores.
- Verificar órdenes de compra o cargamentos en tránsito.

## Rutas principales (Endpoints)

### api.suministros
 
| Método | Endpoint | Descripción |
|---------|----------|-------------|


| GET | /api/suministros | Obtiene todos los suministros |
| GET | /api/suministros/{id} | Obtiene un suministro por ID |
| POST | /api/suministros | Registra un suministro |
| PUT | /api/suministros/{id} | Actualiza un suministro |
| DELETE | /api/suministros/{id} | Elimina un suministro |
| GET | /api/suministros/verificar/{idFabricante} | Verifica el stock y consulta al microservicio de proveedores |

### api.proveedores

| Método | Endpoint | Descripción |


|---------|----------|-------------|
| GET | /api/proveedores | Obtiene todos los proveedores |
| GET | /api/proveedores/{id} | Obtiene un proveedor por ID |
| POST | /api/proveedores | Registra un proveedor |
| PUT | /api/proveedores/{id} | Actualiza un proveedor |
| DELETE | /api/proveedores/{id} | Elimina un proveedor |
| GET | /api/proveedores/verificar/{idFabricante} | Consulta importaciones u órdenes de compra en tránsito |

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

1. Clonar el repositorio.

```bash
git clone https://github.com/usuario/repositorio.git
```

2. Crear las bases de datos correspondientes para ambos microservicios.

3. Configurar el archivo `application.properties` de cada proyecto con los datos de conexión a la base de datos.

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
