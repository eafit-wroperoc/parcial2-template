# Examen: Arquitectura de Software - API de Gestión de Notas

NOTA: Evaluare los commits que haga y que siga las reglas del curso

## Descripción del Proyecto

Este examen consiste en desarrollar una API RESTful para la gestión de notas (To-Do List) utilizando Flask o FastAPI. **El objetivo principal es evaluar los conocimientos sobre servicios y microservicios**, arquitectura de software, diseño de APIs y buenas prácticas de desarrollo.

## Requisitos Funcionales

### API Endpoints
La API debe implementar los siguientes endpoints:

#### Gestión de Notas
- `GET /api/notes` - Obtener todas las notas
- `GET /api/notes/{id}` - Obtener una nota específica por ID
- `POST /api/notes` - Crear una nueva nota
- `PUT /api/notes/{id}` - Actualizar una nota existente
- `DELETE /api/notes/{id}` - Eliminar una nota

### Integración con API Externa
- `GET /api/external/users` - Obtener usuarios desde jsonplaceholder.typicode.com
- `GET /api/external/posts` - Obtener posts desde jsonplaceholder.typicode.com
- `GET /api/external/posts/{id}` - Obtener post específico desde jsonplaceholder.typicode.com

#### Modelo de Datos
Cada nota debe contener:
- `id`: Identificador único (UUID o auto-incremental)
- `title`: Título de la nota (string, requerido)
- `content`: Contenido/descripción de la nota (string, opcional)
- `completed`: Estado de completado (boolean, default: false)
- `created_at`: Fecha de creación (timestamp)
- `updated_at`: Fecha de última actualización (timestamp)

#### Validaciones
- El título es obligatorio y debe tener entre 1 y 200 caracteres
- El contenido no debe exceder 1000 caracteres
- El ID debe ser válido para las operaciones de actualización y eliminación

## Requisitos Técnicos

### Framework
- **Opción 1**: Flask con Flask-RESTful
- **Opción 2**: FastAPI

### Base de Datos
- SQLite para desarrollo (almacenamiento local)
- SQLAlchemy como ORM

### Estructura del Proyecto (puede cambiar de acuerdo a lo que ud elija)
```
todo-api/
├── app/
│   ├── __init__.py
│   ├── models.py          # Modelos de base de datos (SOLID: Single Responsibility)
│   ├── routes.py          # Endpoints de la API (Controladores)
│   ├── services.py        # Lógica de negocio (Service Layer)
│   ├── repositories.py    # Acceso a datos (Repository Pattern)
│   ├── database.py        # Configuración de la base de datos
│   ├── external_api.py    # Cliente para API externa
│   └── utils.py           # Utilidades y validaciones
├── tests/
│   ├── test_models.py     # Pruebas de modelos
│   ├── test_routes.py     # Pruebas de endpoints
│   ├── test_services.py   # Pruebas de lógica de negocio
│   └── test_external.py   # Pruebas de API externa
├── requirements.txt       # Dependencias de Python
├── Dockerfile            # Configuración de Docker
├── docker-compose.yml    # Configuración de Docker Compose
├── .env.example          # Variables de entorno ejemplo
└── README.md             # Documentación del proyecto
```

### Docker
Crear un `Dockerfile` que:
- Use una imagen base de Python 3.11+
- Instale las dependencias desde requirements.txt
- Exponga el puerto 5000
- Configure el comando para ejecutar la aplicación

## Rúbrica de Evaluación

### 🏗️ Arquitectura y Diseño (30%)
**Excelente (30%):**
- Aplicación completa de principios SOLID
- **Arquitectura de microservicios bien implementada y justificada**
- Código modular y mantenible
- Patrones de diseño aplicados correctamente
- **Servicios desacoplados y comunicados correctamente**

**Bueno (25%):**
- Aplicación parcial de principios SOLID
- Arquitectura básica implementada
- Código organizado con mínima deuda técnica
- **Estructura de servicios básica**

**Regular (15%):**
- Poca aplicación de principios SOLID
- Arquitectura confusa o incompleta
- Código desorganizado
- **Servicios mal diseñados**

**Insuficiente (0%):**
- No aplica principios SOLID
- Sin arquitectura definida
- Código inmantenible
- **Sin estructura de servicios**

### ⚙️ Funcionalidad (25%)
**Excelente (25%):**
- Todos los endpoints funcionan perfectamente
- **Servicios de notas bien implementados**
- Integración con API externa robusta
- Manejo de errores completo
- Validaciones exhaustivas

**Bueno (20%):**
- Endpoints principales funcionan
- **Servicios básicos funcionales**
- API externa básica implementada
- Manejo de errores básico
- Validaciones mínimas

**Regular (10%):**
- Algunos endpoints fallan
- **Servicios con errores**
- API externa con errores
- Manejo de errores deficiente
- Validaciones incompletas

**Insuficiente (0%):**
- Endpoints no funcionan
- **Servicios no implementados**
- Sin integración con API externa
- Sin manejo de errores
- Sin validaciones

### 💻 Calidad del Código (20%)
**Excelente (20%):**
- Código completamente documentado
- **Servicios bien estructurados y documentados**
- Nombres descriptivos y consistentes
- Manejo de excepciones robusto
- 100% PEP8 compliant

**Bueno (15%):**
- Código bien documentado
- **Servicios con documentación básica**
- Nombres adecuados
- Manejo básico de excepciones
- Mayormente PEP8 compliant

**Regular (10%):**
- Documentación mínima
- **Servicios pobremente documentados**
- Nombres poco descriptivos
- Manejo limitado de excepciones
- Algunas violaciones PEP8

**Insuficiente (0%):**
- Sin documentación
- **Servicios sin documentar**
- Nombres confusos
- Sin manejo de excepciones
- Múltiples violaciones PEP8

### 🐳 Docker y Despliegue (15%)
**Excelente (15%):**
- Dockerfile optimizado y funcional
- **Servicios correctamente desplegados en contenedores**
- docker-compose.yml completo
- Documentación clara de despliegue
- Aplicación funciona perfectamente en Docker

**Bueno (10%):**
- Dockerfile funcional básico
- **Servicios básicos en contenedores**
- Configuración básica de Docker
- Documentación mínima
- Aplicación funciona con problemas menores

**Regular (5%):**
- Dockerfile con errores
- **Servicios mal configurados en Docker**
- Configuración incompleta
- Poca documentación
- Aplicación no funciona correctamente

**Insuficiente (0%):**
- Dockerfile no funcional
- **Servicios no desplegables**
- Sin configuración Docker
- Sin documentación
- Aplicación no se despliega

### 🧪 Testing (10%)
**Excelente (10%):**
- Pruebas completas para todos los endpoints
- **Pruebas de servicios individuales funcionales**
- Pruebas de integración funcionales
- Cobertura >= 70%
- Todas las pruebas pasan

**Bueno (5%):**
- Pruebas para endpoints principales
- **Pruebas básicas de servicios**
- Pruebas básicas de integración
- Cobertura 50-69%
- La mayoría de pruebas pasan

**Regular (2%):**
- Pruebas limitadas
- **Pruebas de servicios incompletas**
- Sin pruebas de integración
- Cobertura < 50%
- Algunas pruebas fallan

**Insuficiente (0%):**
- Sin pruebas o pruebas no funcionan
- **Sin pruebas de servicios**
- Sin cobertura
- Todas las pruebas fallan

---

### 📊 Escala de Calificación Final
- **90-100%:** Sobresaliente (A)
- **80-89%:** Notable (B)
- **70-79%:** Aprobado (C)
- **60-69%:** Suficiente (D)
- **< 60%:** Reprobado (F)

### ⚠️ Penalizaciones
- **Uso de IA detectado:** -50% de la calificación total
- **Código copiado:** Calificación mínima (0-30%)
- **Entrega tardía:** -10% por día de retraso
- **Pruebas no funcionales:** -5% del total

## Entrega

### Formato de Entrega
1. Repositorio en GitHub Classroom
2. README.md con documentación completa
3. Código fuente funcional
4. Dockerfile y docker-compose.yml
5. Pruebas unitarias

### Instrucciones de Entrega
- Fork del repositorio proporcionado en GitHub Classroom
- Desarrollar la solución en la rama `main`
- Crear un tag `v1.0.0` para la versión final
- Incluir un video demostrativo (opcional, puntos extra)

## Restricciones Importantes

### ⚠️ PROHIBICIÓN DE USO DE IA
- **ESTRICTAMENTE PROHIBIDO** el uso de herramientas de Inteligencia Artificial (ChatGPT, Copilot, Claude, etc.) para generar código
- **NO SE PERMITE el uso de Asistentes de Código o Autocompletado IA**
- **CÓDIGO QUE SEA EXACTAMENTE IGUAL EN SIMILITUD O GENERADO TOTALMENTE POR IA SERÁ PENALIZADO**
- El código debe ser 100% original del estudiante
- Cualquier evidencia de uso de IA resultará en calificación mínima
- Se realizarán revisiones de originalidad del código
- **El estudiante debe investigar y aprender a usar la API externa por sí mismo**

### Otras Restricciones
- No se permite el uso de frameworks de frontend (solo backend)
- No se permiten librerías externas que no estén en requirements.txt
- El código debe funcionar sin configuración adicional

## Documentación Requerida

### README.md debe incluir:
1. Descripción del proyecto
2. Instrucciones de instalación y ejecución
3. Documentación de endpoints (ejemplos de uso)
4. Requisitos del sistema
5. Estructura del proyecto

### Documentación de API:
- Ejemplos de requests/responses para cada endpoint
- Códigos de estado HTTP utilizados
- Formato de errores
- **Documentación de endpoints de API externa**

## Ejemplos de Uso

### Crear una nota
```bash
curl -X POST http://localhost:5000/api/notes \
  -H "Content-Type: application/json" \
  -d '{"title": "Estudiar para examen", "content": "Repasar arquitectura de software"}'
```

### Obtener todas las notas
```bash
curl http://localhost:5000/api/notes
```

### Actualizar una nota
```bash
curl -X PUT http://localhost:5000/api/notes/1 \
  -H "Content-Type: application/json" \
  -d '{"title": "Estudiar para examen", "completed": true}'
```

### Consumir API externa
```bash
# Obtener usuarios desde jsonplaceholder
curl http://localhost:5000/api/external/users

# Obtener posts desde jsonplaceholder
curl http://localhost:5000/api/external/posts

# Obtener post específico
curl http://localhost:5000/api/external/posts/1
```

## Preguntas Frecuentes

### ¿Puedo usar otro framework?
No, solo se permite Flask o FastAPI como se especifica.

### ¿Necesito implementar autenticación?
No, para este examen no se requiere autenticación.

### ¿Puedo usar otra base de datos?
Se recomienda SQLite, pero puede usar PostgreSQL si lo prefiere.

### ¿Qué pasa si mi código no funciona con Docker?
La aplicación debe funcionar tanto localmente como en Docker.

### ¿Cómo investigo la API externa?
Debes investigar por tu cuenta cómo funciona https://jsonplaceholder.typicode.com/ y cómo consumirla desde Python usando requests o httpx.

### ¿Qué arquitectura debo elegir?
Debes implementar una arquitectura específica vista en clase:
  - **Hexagonal/Clean Architecture**
  - **Microservicios (simplificado)**

### ¿Por qué microservicios es recomendado?
Este examen se centra en evaluar conocimientos sobre **servicios y microservicios**. La arquitectura de microservicios te permite:
- Diseñar servicios desacoplados
- Implementar comunicación entre servicios
- Aplicar principios de diseño de servicios
- Demostrar comprensión de arquitectura distribuida

---

**Nota Importante**: Este examen evalúa tu capacidad para diseñar y construir software de forma independiente. La honestidad académica es fundamental. Cualquier intento de usar herramientas de IA, asistentes de código o copiar código de fuentes externas será considerado plagio y resultará en las consecuencias académicas correspondientes. **Código con similitud exacta o generado por IA será penalizado severamente. La investigación de la API externa debe ser realizada completamente por el estudiante.**
