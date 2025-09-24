# peopleflow
Challenge Backend - Gestión de Empleados

Tecnologías y versiones
- Python: 3.13
- Django: 5.2.6
- Django REST Framework: última versión compatible
- MongoEngine: para manejar MongoDB desde Django
- MongoDB: 7.x (o la versión que tengas instalada)

Instalación y configuración

Clonar el repositorio:

git clone <url-del-repo>
cd peopleflow


Crear y activar un entorno virtual:

python -m venv venv
# Windows
venv\Scripts\activate
# Linux/macOS
source venv/bin/activate


Instalar dependencias:
pip install django==5.2.6 djangorestframework mongoengine


Levantar MongoDB:
Asegurarse de que MongoDB está corriendo en localhost:27017.

En Windows, si usas la app de MongoDB, iniciar el servicio o el servidor desde MongoDB Compass/terminal.

En Linux/macOS:

mongod --dbpath /ruta/a/tu/db


Configurar Django:

La configuración de la base de datos MongoDB está en peopleflow/settings.py:

connect(
    db='peopleflow_db',
    host='localhost',
    port=27017
)
Modificar si tu host, puerto o nombre de DB es distinto.


Levantar la API
python manage.py runserver

La API estará disponible en: http://127.0.0.1:8000/api/


# Endpoints

1. Listar empleados (con filtro y paginación)
GET /api/employees/?puesto=Developer&page=1&page_size=10

2. Crear empleado
POST /api/employees/
Content-Type: application/json

{
    "nombre": "Juan",
    "apellido": "Pérez",
    "email": "juan.perez@mail.com",
    "puesto": "Developer",
    "salario": "45000.00",
    "fecha_ingreso": "2025-09-01"
}

3. Obtener detalle de empleado
GET /api/employees/<uuid:id>/

4. Actualizar empleado
PUT /api/employees/<uuid:id>/
Content-Type: application/json

{
    "nombre": "Juan",
    "apellido": "Pérez",
    "email": "juan.perez@mail.com",
    "puesto": "Senior Developer",
    "salario": "50000.00",
    "fecha_ingreso": "2025-09-01"
}

5. Borrar empleado
DELETE /api/employees/<uuid:id>/

Notas importantes
Los emails de los empleados deben ser únicos. Intentar insertar un email duplicado lanzará un error.

Para filtrar empleados por puesto y paginar, usar parámetros en la URL:

GET /api/employees/?puesto=Developer&page=2&page_size=5


## Ideas de mejora y expansión del proyecto

- Roles y jerarquía: indicar si un empleado es jefe, definir manager y subordinados.
- Datos adicionales: teléfono, dirección, departamento, historial salarial y laboral.
- Filtros y estadísticas: búsqueda avanzada, orden por salario, departamento o fecha de ingreso, estadísticas de empleados.
- Autenticación y permisos: roles (admin, manager, empleado) y control de acciones por rol.
- Auditoría y notificaciones: registro de cambios, recordatorios y alertas por correo.
- Frontend y visualización: dashboard interactivo, organigramas y reportes exportables.
- Escalabilidad y arquitectura: índices en MongoDB, microservicios, integración con sistemas externos.
