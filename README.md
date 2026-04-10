# 📊 Guía de Exportación e Importación en Oracle SQL Developer

[cite_start]Este repositorio contiene la **Guía Práctica** para el manejo de respaldos y restauración de bases de datos utilizando Oracle SQL Developer[cite: 3]. [cite_start]El objetivo es enseñar a los estudiantes cómo empaquetar una base de datos completa y cargarla en un nuevo espacio de trabajo[cite: 4].

## 🚀 Contenido del Proyecto
* [cite_start]**Fase 1:** Proceso de exportación (Rol Docente)[cite: 5, 6].
* [cite_start]**Fase 2:** Proceso de importación (Rol Estudiante)[cite: 478, 479].
* [cite_start]**Scripts de ejemplo:** Configuración de usuarios y permisos[cite: 486, 489].

---

## 🛠️ Fase 1: Cómo Exportar (Docente)
[cite_start]Este proceso genera el archivo `.sql` que se compartirá con la clase[cite: 6].

1. [cite_start]**Abrir el Asistente:** Ve a `Tools` > `Database Export`[cite: 43, 53].
2. [cite_start]**Configuración de Código:** * Marcar `Export DDL` y `Export Data`[cite: 124, 128, 139].
    * [cite_start]**IMPORTANTE:** Desmarcar `Show Schema` para evitar errores de permisos[cite: 140].
    * [cite_start]Marcar `Drops` para permitir la sobrescritura limpia[cite: 141].
3. [cite_start]**Selección de Objetos:** En la pestaña `Specify Objects`, usa `Lookup` para elegir solo las tablas necesarias (ej. `AULA`, `ESTUDIANTE`, `MATERIA`)[cite: 232, 293, 294].
4. [cite_start]**Guardar:** Exportar como un archivo único (ej. `Laboratorio.sql`)[cite: 170, 425].

---

## 📥 Fase 2: Cómo Importar (Estudiante)
[cite_start]Carga los datos del docente en tu base de datos local[cite: 479].

### 1. Preparar el Usuario
[cite_start]Antes de importar, debes crear un usuario de prueba (ej. `BD_TEST`) desde una cuenta con privilegios (ej. `SYSTEM`)[cite: 480, 481, 483]:

```sql
-- Cambiar al contenedor correcto
ALTER SESSION SET CONTAINER = XEPDB1; [cite: 486]

-- Crear usuario y asignar permisos
CREATE USER BD_TEST IDENTIFIED BY admin123; [cite: 488]
GRANT CONNECT, RESOURCE TO BD_TEST; [cite: 489]
ALTER USER BD_TEST QUOTA UNLIMITED ON USERS; [cite: 490]
