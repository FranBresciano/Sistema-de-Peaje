# Sistema de Peaje - Proyecto Académico

Aplicación web desarrollada con Spring Boot para gestionar un sistema de peajes con dos perfiles de usuario (Administrador y Propietario), simulación de tránsitos y reglas de bonificación por puesto.

Este proyecto fue realizado como obligatorio académico y está orientado a demostrar diseño orientado a objetos, separación por capas y uso de patrones de diseño en Java.

## Objetivo

Modelar y exponer una solución de peaje que permita:

- Autenticar usuarios por rol.
- Consultar y administrar propietarios, estados y bonificaciones.
- Simular tránsitos de vehículos por distintos puestos.
- Visualizar información operativa en vistas web con actualización desde backend.

## Funcionalidades principales

### Administrador

- Login y logout.
- Consulta de propietarios por cédula.
- Cambio de estado de propietarios.
- Asignación de bonificaciones por puesto.
- Simulación de tránsito ingresando puesto, matrícula y fecha.

### Propietario

- Login y logout.
- Visualización de:
  - estado actual,
  - saldo,
  - vehículos,
  - bonificaciones activas,
  - historial de tránsitos,
  - notificaciones.
- Limpieza de notificaciones.

## Patrones y diseño

El proyecto aplica varios patrones de diseño clásicos:

- Facade: centraliza la lógica de acceso en la clase Fachada.
- Strategy: bonificaciones intercambiables (Exonerados, Frecuentes, Trabajadores).
- State: estados de propietario (Habilitado, Deshabilitado, Suspendido, Penalizado).
- Observer: notificaciones y actualización de vistas mediante observadores.

Además, utiliza DTOs para desacoplar la representación de datos enviada al frontend.

## Stack tecnológico

- Java 21
- Spring Boot 3.5.x
- Maven Wrapper
- HTML, CSS y JavaScript (frontend estático)
- Server-Sent Events (SSE) para actualización en tiempo real

## Cómo ejecutar en local (Windows)

### 1) Requisitos

- Tener instalado JDK 21.

Si no lo tenés:

```powershell
winget install -e --id EclipseAdoptium.Temurin.21.JDK --accept-source-agreements --accept-package-agreements
```

### 2) Configurar Java en la terminal actual (si java no se reconoce)

```powershell
$env:JAVA_HOME="C:\Program Files\Eclipse Adoptium\jdk-21.0.11.10-hotspot"
$env:Path="$env:JAVA_HOME\bin;$env:Path"
java -version
```

### 3) Ejecutar la aplicación

Desde la raíz del proyecto (donde está mvnw.cmd):

```powershell
cd "X:\CarpetaWindows\ORT\SEMESTRE 7\DA\Obligatorio\obligatorio"
.\mvnw.cmd spring-boot:run
```

### 4) Abrir en el navegador

- http://localhost:8080

## Usuarios de prueba precargados

Se cargan al iniciar la app.

### Administradores

- Cédula: 12345678 | Contraseña: 123
- Cédula: 01234567 | Contraseña: 123

### Propietarios

- Cédula: 23456789 | Contraseña: 123
- Cédula: 34567890 | Contraseña: 123
- Cédula: 45678901 | Contraseña: 123
- Cédula: 56789012 | Contraseña: 123

## Estructura del proyecto

```text
src/main/java/ort/da/obligatorio
├─ controladores/
├─ dominio/
│  ├─ Bonificaciones/
│  ├─ EstadosPropietario/
│  ├─ Personas/
│  ├─ Puestos/
│  └─ DTOs/
├─ observador/
├─ servicios/
└─ utils/

src/main/resources/static
├─ index.html
├─ loginAdmin.html
├─ loginPropietario.html
├─ menuAdministrador.html
└─ menuPropietario.html
```

## Endpoints principales

- POST /acceso/loginAdministrador
- POST /acceso/loginPropietario
- POST /acceso/logoutAdministrador
- POST /acceso/logoutPropietario
- GET /menuAdministrador/vistaConectadaAdministrador
- POST /menuAdministrador/emularTransito
- POST /menuAdministrador/cambiarEstadoPropietario
- POST /menuAdministrador/asignarBonificacion
- GET /menuPropietario/vistaConectadaPropietario
- POST /menuPropietario/borrarNotificacionesPropietario

## Nota

Los datos son de prueba y se cargan en memoria al iniciar (sin persistencia en base de datos en esta versión).

## Autor

Podés completar esta sección con tu nombre, LinkedIn y contacto para portfolio.
