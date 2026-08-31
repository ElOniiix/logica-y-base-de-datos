# Mis Fundamentos de Bases de Datos

## Ejercicio de Normalización (Modelo de Ventas de Asistencias y Servicios)

### Esquema Final en 3NF (Tercera Forma Normal)

1. **Clientes:** `ID_Cliente (PK)`, Nombre, Telefono
2. **Asistencias:** `ID_Asistencia (PK)`, Nombre_Asistencia, Precio
3. **Agentes:** `ID_Agente (PK)`, Nombre_Agente, Porcentaje_Comision
4. **Ventas:** `ID_Venta (PK)`, `ID_Cliente (FK)`, `ID_Asistencia (FK)`, `ID_Agente (FK)`, Fecha
