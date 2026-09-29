# Proyecto Gimnasio — Práctica DDSI

Versión final de una práctica universitaria de **Diseño y Desarrollo de Sistemas de Información (DDSI)** desarrollada en **Java**.

La aplicación implementa la gestión de un gimnasio mediante una interfaz gráfica Swing, persistencia con Hibernate/JPA y una base de datos MariaDB, organizando el código con una separación clara entre modelo, vista y controladores.

## Contexto académico

Este repositorio corresponde a una práctica universitaria. Su objetivo principal es aplicar conceptos de persistencia, acceso a bases de datos, arquitectura por capas, interfaces gráficas y organización de una aplicación Java.

No se presenta como un producto comercial ni como una aplicación de producción.

## Funcionalidades

La aplicación permite gestionar distintas entidades del gimnasio:

- socios;
- monitores;
- actividades.

Incluye:

- conexión a base de datos mediante Hibernate;
- operaciones de consulta y persistencia mediante DAO;
- controladores específicos para cada área;
- vistas Swing para la interacción con el usuario;
- tablas para mostrar información de socios, monitores y actividades;
- formularios de alta y actualización;
- validación y mensajes de información o error;
- navegación entre distintas secciones desde una ventana principal.

## Arquitectura

El proyecto sigue una organización similar a **Modelo–Vista–Controlador (MVC)**.

### Modelo

Contiene las entidades y clases DAO:

```text
Modelo/
├── Actividad.java
├── ActividadDAO.java
├── Monitor.java
├── MonitorDAO.java
├── Socio.java
└── SocioDAO.java
```

Las entidades se gestionan mediante Hibernate/JPA.

### Vista

La interfaz está construida con **Java Swing**.

Incluye, entre otras:

- vista principal;
- vista de conexión;
- gestión de socios;
- gestión de monitores;
- gestión de actividades;
- formularios de creación y actualización;
- diálogos y mensajes.

Algunas vistas fueron diseñadas con el editor visual de NetBeans, por lo que el repositorio incluye también archivos `.form`.

### Controladores

Los controladores coordinan la interfaz con la capa de persistencia:

```text
Controlador/
├── ControladorActividad.java
├── ControladorConexion.java
├── ControladorMonitor.java
├── ControladorPrincipal.java
├── ControladorSocio.java
├── GestionTablasActividad.java
├── GestionTablasMonitor.java
└── GestionTablasSocio.java
```

## Tecnologías

- **Java 24**
- **Maven**
- **Hibernate ORM 7.1**
- **Jakarta Persistence 3.2**
- **MariaDB**
- **Java Swing**
- **JCalendar 1.4**
- **NetBeans**

## Estructura del proyecto

```text
ProyectoGimnasio/
├── pom.xml
├── nbactions.xml
└── src/
    └── main/
        ├── java/
        │   ├── Aplicacion/
        │   ├── Config/
        │   ├── Controlador/
        │   ├── Modelo/
        │   └── Vista/
        └── resources/
            └── hibernate.cfg.xml
```

## Punto de entrada

La aplicación se inicia desde:

```text
src/main/java/Aplicacion/Practica_Gimnasio.java
```

La clase principal crea el controlador de conexión desde el hilo de eventos de Swing:

```java
java.awt.EventQueue.invokeLater(() -> {
    new ControladorConexion();
});
```

## Configuración de la base de datos

El archivo:

```text
src/main/resources/hibernate.cfg.xml
```

incluye valores de ejemplo y debe configurarse antes de ejecutar la aplicación:

```xml
<property name="hibernate.connection.url">jdbc:mariadb://HOST:3306/DATABASE</property>
<property name="hibernate.connection.username">YOUR_USERNAME</property>
<property name="hibernate.connection.password">YOUR_PASSWORD</property>
```

Sustituye esos valores por los correspondientes a tu instalación local de MariaDB.

Las credenciales reales no deben subirse al repositorio.

## Instalación

Clona el repositorio:

```bash
git clone https://github.com/Nico3246/ProyectoGimnasio.git
cd ProyectoGimnasio
```

Comprueba que dispones de una versión de Java compatible con la configurada en Maven.

Instala las dependencias y compila:

```bash
mvn clean package
```

También puede abrirse directamente como proyecto Maven desde NetBeans.

## Ejecución

Antes de iniciar la aplicación:

1. configura MariaDB;
2. crea o utiliza la base de datos correspondiente;
3. actualiza `hibernate.cfg.xml`;
4. comprueba que las tablas y datos requeridos por la práctica estén disponibles.

Después puedes ejecutar la clase:

```text
Aplicacion.Practica_Gimnasio
```

desde el IDE.

## Dependencias principales

Las dependencias están definidas en `pom.xml`:

- `hibernate-core 7.1.0.Final`;
- `jakarta.persistence-api 3.2.0`;
- `mariadb-java-client 3.5.5`;
- `jcalendar 1.4`.


