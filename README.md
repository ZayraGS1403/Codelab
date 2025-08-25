# H2 Database - Codelab de Persistencia en Memoria

## 📋 Descripción

Este proyecto es un codelab que demuestra cómo integrar y configurar la base de datos H2 con Spring Boot. H2 es una base de datos en memoria liviana y rápida, ideal para desarrollo, testing y prototipado.

## 🚀 Características

- **Base de datos en memoria H2** con persistencia en archivo
- **Spring Boot 3.5.5** con Java 21
- **Spring Data JPA** para operaciones de base de datos
- **Consola web H2** habilitada para administración
- **Inicialización automática** de datos de prueba

## 🛠️ Tecnologías Utilizadas

- Java 21
- Spring Boot 3.5.5
- Spring Data JPA
- H2 Database Engine
- Maven

## 📁 Estructura del Proyecto

```
src/
├── main/
│   ├── java/
│   │   └── com/codelab/h2/database/
│   │       └── Application.java
│   └── resources/
│       ├── application.yaml
│       └── data.sql
└── test/
    └── java/
        └── com/codelab/h2/database/
            └── ApplicationTests.java
```

## ⚙️ Configuración

### Base de Datos
La configuración de H2 se encuentra en `application.yaml`:

```yaml
spring:
  h2:
    console:
      enabled: true
      path: /h2-console
  datasource:
    url: jdbc:h2:file:/data/demo
    username: sa
    password: password
    driverClassName: org.h2.Driver
  jpa:
    database-platform: org.hibernate.dialect.H2Dialect
    defer-datasource-initialization: true
```

### Características de la Configuración:
- **Persistencia en archivo**: Los datos se guardan en `/data/demo`
- **Consola web habilitada**: Accesible en `/h2-console`
- **Inicialización diferida**: Los datos se cargan después de crear el esquema

## 🔧 Instalación y Ejecución

### Prerrequisitos
- Java 21+
- Maven 3.6+

### Pasos para ejecutar:

1. **Clonar el repositorio**
```bash
git clone <https://github.com/ZayraGS1403/Codelab.git>
cd h2.database
```

2. **Compilar el proyecto**
```bash
mvn clean compile
```

3. **Ejecutar la aplicación**
```bash
mvn spring-boot:run
```

4. **Acceder a la consola H2**
   - URL: http://localhost:8080/h2-console
   - JDBC URL: `jdbc:h2:file:/data/demo`
   - Username: `sa`
   - Password: `password`

## 📊 Datos de Prueba

El archivo `data.sql` inicializa la base de datos con datos de países:

| ID | País   |
|----|--------|
| 1  | USA    |
| 2  | France |
| 3  | Brazil |
| 4  | Italy  |
| 5  | Canada |

## 🖥️ Uso de la Consola H2

1. Inicia la aplicación
2. Navega a http://localhost:8080/h2-console
3. Usa las credenciales configuradas:
   - **JDBC URL**: `jdbc:h2:file:/data/demo`
   - **Username**: `sa`
   - **Password**: `password`
4. Ejecuta consultas SQL directamente en la interfaz web

### Consulta de ejemplo:
```sql
SELECT * FROM countries;
```


## 📚 Conceptos Clave Aprendidos

- **Configuración de H2 con Spring Boot**
- **Persistencia en memoria vs. archivo**
- **Inicialización de datos con SQL scripts**
- **Uso de la consola web de H2**
- **Configuración de JPA con H2**


## 📝 Notas Importantes

- La base de datos se crea automáticamente al iniciar la aplicación
- Los datos persisten entre reinicios gracias a la configuración de archivo
- La consola H2 solo debe usarse en desarrollo, no en producción
- El script `data.sql` se ejecuta automáticamente al iniciar

