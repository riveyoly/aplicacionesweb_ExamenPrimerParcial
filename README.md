# Sistema de Gestión de Proyectos

Aplicación web en **ASP.NET Core MVC (.NET 10)** con **Entity Framework Core (Code First)** y
**PostgreSQL** para gestionar proyectos, empleados y las asignaciones de empleados a proyectos.

## Base de datos

```
proyectos    (proyecto_id PK, nombre UNIQUE, descripcion, fecha_inicio, fecha_fin)
empleados    (empleado_id PK, nombre, apellido, email UNIQUE, posicion)
asignaciones (asignacion_id PK, proyecto_id FK, empleado_id FK, rol, fecha_asignacion)
             UNIQUE (proyecto_id, empleado_id) · ON DELETE CASCADE
```

Las clases de `src/GestionProyectos/Models` definen las tablas y `Data/AppDbContext.cs` las mapea
a esos nombres. Los scripts para reconstruir la base están en `Database/`:

| Script                    | Contenido                                         |
|---------------------------|---------------------------------------------------|
| `00_crear_base_datos.sql` | Crea la base `gestion_proyectos`                  |
| `01_crear_tablas.sql`     | Tablas, claves, índices y restricciones           |
| `02_datos_prueba.sql`     | Datos de ejemplo (opcional)                       |

## Ejecutar

Requisitos: SDK de .NET 10 y PostgreSQL.

```bash
copy .env.example .env      # y escribir la contraseña de PostgreSQL
dotnet run --project src/GestionProyectos
```

Abrir http://localhost:5117. Los pasos completos están en `INSTRUCCIONES_DESPLIEGUE.txt`.
