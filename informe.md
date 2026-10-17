# Informe de Laboratorio: Protección y Privacidad de Datos en PostgreSQL

## 1. ¿De qué trata este laboratorio?
El objetivo principal de este lab fue aplicar técnicas reales de seguridad y privacidad para proteger información de identificación personal. Vimos cómo restringir accesos con el principio de privilegio mínimo, enmascarar datos para roles específicos, separar datos sensibles mediante seudonimización, aplicar anonimización con k-anonimato y definir políticas de retención.

---

## 2. Lo que se hizo en cada actividad

### Actividad 1: Clasificación de Datos
- **¿Qué se hizo?:** Revisamos la tabla de clientes para identificar qué datos son altamente sensibles (nombre, correo, teléfono, RFC) y cuáles son datos operativos o estadísticos.
- **Archivos:** Script en `sql/01-clasificacion.sql` y reporte con capturas en `evidencias/01-clasificacion.pdf`.

### Actividad 2: Enmascaramiento y Control de Acceso (RBAC)
- **¿Qué se hizo?:** Creamos el rol `soporte` con la opción `NOLOGIN` para evitar conexiones directas. Le revocamos el acceso a la tabla original de `clientes` y en su lugar creamos la vista `v_clientes_soporte` para que solo pueda ver datos parcialmente ocultos.
- **Archivos:** Script en `sql/02-enmascaramiento.sql` y reporte en `evidencias/02-ernmascaramiento.pdf`.

### Actividad 3: Seudonimización
- **¿Qué se hizo?:** Separamos la base de datos en dos esquemas: `pii`  y un esquema analítico. Reemplazamos los datos de identidad por tokens para que el área de analítica trabaje sin saber a quién pertenece cada registro.
- **Archivos:** Script en `sql/03-seudonimizacion.sql` y reporte en `evidencias/03-seudonimizacion.pdf`.

### Actividad 4: Anonimización y $k$-anonimato
- **¿Qué se hizo?:** Agrupamos datos para que no se pueda reidentificar a nadie, cambiamos las edades exactas por rangos y los códigos postales por zonas. Además, usamos `HAVING COUNT(*)` para asegurar que ningún grupo tenga tan poquita gente que termine delatando a alguien.
- **Archivos:** Script en `sql/04-anonimizacion.sql` y reporte en `evidencias/04-anonimizacion.pdf`.

### Actividad 5: Políticas de Retención de Datos
- **¿Qué se hizo?:** Diseñamos la regla para depurar datos con más de 5 años de antigüedad mediante un `SELECT` de prueba.
- **Archivos:** Script en `sql/05-retencion.sql` y reporte en `evidencias/05-retencion.pdf`.

