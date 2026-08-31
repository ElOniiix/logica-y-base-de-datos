# Modelado y Normalización de Bases de Datos Relacionales

Este repositorio contiene la documentación y estructura lógica para el diseño eficiente de bases de datos relacionales, aplicando los principios de normalización hasta **Tercera Forma Normal (3NF)** para garantizar la integridad de los datos y eliminar redundancias.

---

## 📌 Caso de Estudio: Sistema de Ventas de Asistencias y Servicios

### 🎯 Objetivo
Estructurar la base de datos de una entidad comercial encargada de la venta de servicios y asistencias, independizando los registros de clientes, productos y asesores para permitir un control de transacciones escalable y sin inconsistencias.

---

## 🛠️ Proceso de Normalización

### 1. Diagnóstico de Anomalías (Tabla Plana)
Inicialmente, la información se almacenaba en un único registro plano, lo que provocaba:
* **Redundancia:** Repetición de nombres de clientes y datos de agentes en cada transacción.
* **Riesgo de inconsistencia:** Dificultad para actualizar precios o comisiones sin modificar el historial completo.
* **Anomalías de eliminación:** Al borrar una venta, se corría el riesgo de perder la información del cliente o del agente.

### 2. Solución Aplicada (Esquema en 3NF)
Se dividió el dominio en **4 entidades relacionales con dependencias funcionales completas**:

* **`Clientes`**: Catálogo maestro con la información de los compradores.
* **`Asistencias`**: Catálogo de servicios ofertados y sus precios base.
* **`Agentes`**: Registro de asesores comerciales y su esquema de comisiones.
* **`Ventas`**: Tabla transaccional central vinculada mediante llaves foráneas.

---

## 📐 Estructura de Tablas (Diccionario de Datos)

### 1. Tabla `Clientes`
| Campo | Tipo de Dato | Descripción | Clave |
| :--- | :--- | :--- | :--- |
| `ID_Cliente` | VARCHAR(20) / INT | Identificador único del cliente | **PK** |
| `Nombre` | VARCHAR(100) | Nombre completo | |
| `Telefono` | VARCHAR(20) | Teléfono de contacto | |

### 2. Tabla `Asistencias`
| Campo | Tipo de Dato | Descripción | Clave |
| :--- | :--- | :--- | :--- |
| `ID_Asistencia` | VARCHAR(20) / INT | Identificador del servicio | **PK** |
| `Nombre_Asistencia` | VARCHAR(100) | Tipo de asistencia comercial | |
| `Precio` | DECIMAL(10,2) | Valor del servicio | |

### 3. Tabla `Agentes`
| Campo | Tipo de Dato | Descripción | Clave |
| :--- | :--- | :--- | :--- |
| `ID_Agente` | VARCHAR(20) / INT | Identificador del asesor | **PK** |
| `Nombre_Agente` | VARCHAR(100) | Nombre del vendedor | |
| `Porcentaje_Comision` | DECIMAL(5,2) | Porcentaje de comisión asignado | |

### 4. Tabla `Ventas`
| Campo | Tipo de Dato | Descripción | Clave |
| :--- | :--- | :--- | :--- |
| `ID_Venta` | INT | ID autoincremental de la transacción | **PK** |
| `ID_Cliente` | VARCHAR(20) / INT | Referencia al cliente comprador | **FK** |
| `ID_Asistencia` | VARCHAR(20) / INT | Referencia al servicio vendido | **FK** |
| `ID_Agente` | VARCHAR(20) / INT | Referencia al asesor responsable | **FK** |
| `Fecha` | DATETIME / DATE | Fecha y hora del registro | |

---

## 🚀 Tecnologías y Conceptos Aplicados
* **Modelo Relacional:** Normalización (1NF, 2NF, 3NF).
* **Diseño SQL:** Llaves Primarias (PK), Llaves Foráneas (FK) e Integridad Referencial.
* **Documentación Técnica:** Maquetación estructurada en Markdown.

---

## 👤 Autor
**Nixon López Peña**  
*Estudiante de Ingeniería de Sistemas*
