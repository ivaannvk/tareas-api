# API de tareas: FastAPI + SQLite (sqlite3, sin ORM)

Parte 1 de los apuntes de acceso a bases de datos. API REST para gestionar
tareas, con el SQL escrito a mano usando el módulo `sqlite3` de Python.

## Estructura

- `main.py`: la API y sus endpoints
- `database.py`: conexión a SQLite y creación de la tabla
- `schemas.py`: esquemas Pydantic (datos de entrada y salida)

## Ejecutar

```
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```

Documentación interactiva: http://127.0.0.1:8000/docs

El archivo `tareas.db` se crea automáticamente al arrancar.

## Endpoints

| Método | Ruta | Descripción |
|---|---|---|
| POST | `/tareas` | Crear una tarea (201) |
| GET | `/tareas` | Listar tareas; filtro opcional `?completada=true` |
| GET | `/tareas/{tarea_id}` | Obtener una tarea (404 si no existe) |
| PUT | `/tareas/{tarea_id}/completar` | Marcar como completada (404 si no existe) |
| DELETE | `/tareas/{tarea_id}` | Borrar una tarea (204, 404 si no existe) |
