#  Backend — Medical Rolling

Backend REST API del proyecto final **Medical Rolling**, una plataforma web de medicina prepaga desarrollada como proyecto integrador del **RollingCode Institute**.

---

##  Equipo

| Nombre | Rol |
|---|---|
| Federico Mansilla | Desarrollador Backend |
| Cristhian Rodrigo Sosa Zurita | Desarrollador Backend |
| Dario Ezequiel Cabrera | Desarrollador Backend |

---

##  Stack Tecnológico

| Tecnología | Uso |
|---|---|
| **Node.js** | Entorno de ejecución |
| **Express** | Framework HTTP |
| **MongoDB + Mongoose** | Base de datos |
| **JWT** | Autenticación |
| **Bcrypt** | Hash de contraseñas |
| **Nodemon** | Hot reload en desarrollo |
| **Morgan** | Logging HTTP |
| **Zod** | Validación de esquemas |
| **node-cron** | Tareas programadas |
| **moment-timezone** | Manejo de fechas y zonas horarias |
| **Vercel** | Deploy |

---

##  Referencia de API

Base URL producción: `https://backend-medical-rolling.vercel.app`  
Base URL local: `http://localhost:3001`

### Usuarios

| Método | Ruta | Descripción |
|--------|------|-------------|
| `POST` | `/api/createusers` | Registrar usuario |
| `POST` | `/api/loginusers` | Login de usuario |
| `POST` | `/api/verifyUser` | Verificar token de usuario |
| `GET` | `/api/gettingusers` | Obtener todos los usuarios |
| `GET` | `/api/getoneuser/:id` | Obtener usuario por ID |
| `GET` | `/api/getUserByDNI/:dni` | Obtener usuario por DNI |
| `GET` | `/api/checkDniUser/:dni` | Verificar disponibilidad de DNI |
| `GET` | `/api/checkEmailUser/:email` | Verificar disponibilidad de email |
| `PUT` | `/api/updateusers/:id` | Actualizar usuario |
| `DELETE` | `/api/deleteusers/:id` | Eliminar usuario |

### Doctores

| Método | Ruta | Descripción |
|--------|------|-------------|
| `POST` | `/api/createdoctor` | Registrar doctor |
| `POST` | `/api/logindoctor` | Login de doctor |
| `POST` | `/api/verifyDoctor` | Verificar token de doctor |
| `GET` | `/api/gettingdoctors` | Obtener todos los doctores |
| `GET` | `/api/getonedoctor/:id` | Obtener doctor por ID |
| `GET` | `/api/doctorsbyspecialty/:specialty` | Obtener doctores por especialidad |
| `GET` | `/api/checkDniDoctor/:dni` | Verificar disponibilidad de DNI |
| `GET` | `/api/checkEmailDoctor/:email` | Verificar disponibilidad de email |
| `PUT` | `/api/updatedoctors/:id` | Actualizar doctor |
| `DELETE` | `/api/deletedoctors/:id` | Eliminar doctor |

### Turnos

| Método | Ruta | Descripción |
|--------|------|-------------|
| `POST` | `/api/createappointment` | Crear turno |
| `GET` | `/api/gettingappointments` | Obtener todos los turnos |
| `GET` | `/api/getoneappointment/:id` | Obtener turno por ID |
| `GET` | `/api/getappointmentbyuser/:userId` | Turnos por usuario |
| `GET` | `/api/getappointmentbydoctor/:doctorId` | Turnos por doctor |
| `GET` | `/api/availableTimes` | Horarios disponibles |
| `PUT` | `/api/updateappointments/:id` | Actualizar turno |
| `DELETE` | `/api/deleteappointments/:id` | Eliminar turno |

---

##  Instalación y ejecución

### 1. Clonar el repositorio

```bash
git clone https://github.com/CristhianSZ/Backend-Medical_Rolling.git
cd Backend-Medical_Rolling
```

### 2. Instalar dependencias

```bash
npm install
```

### 3. Configurar variables de entorno

Crear un archivo `.env` en la raíz del proyecto (ver sección [Variables de Entorno](#-variables-de-entorno)).

### 4. Ejecutar en modo desarrollo

```bash
npm start
```

El servidor corre en **http://localhost:3001**

---

##  Variables de Entorno

Crear un archivo `.env` en la raíz con el siguiente contenido:

```env
MONGODB_URI=tu_cadena_de_conexion_mongodb
JWT_SECRET=tu_secreto_jwt
PORT=3001
```

| Variable | Descripción |
|---|---|
| `MONGODB_URI` | Cadena de conexión a MongoDB (Atlas o local). Ver sección [Configuración de MongoDB](#-configuración-de-mongodb). |
| `JWT_SECRET` | Clave secreta para firmar y verificar tokens JWT. Puede ser cualquier string largo y aleatorio. |
| `PORT` | Puerto en el que corre el servidor. Por defecto `3001`. |

> **Importante:** No subir el archivo `.env` al repositorio. Asegurarse de que esté incluido en `.gitignore`.

---

##  Configuración de MongoDB

Este proyecto utiliza **MongoDB** como base de datos. Podés conectarte usando **MongoDB Atlas** (recomendado, cloud gratuito) o una instancia **local**.

### Opción A — MongoDB Atlas (recomendado)

1. Crear una cuenta gratuita en [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
2. Crear un nuevo **Cluster** (el tier gratuito M0 es suficiente)
3. En **Database Access**, crear un usuario con permisos de lectura/escritura y anotá la contraseña
4. En **Network Access**, agregar tu IP (o `0.0.0.0/0` para permitir cualquier IP en desarrollo)
5. En el cluster, hacer clic en **Connect → Drivers** y copiar la URI de conexión

La URI tendrá este formato:

```
mongodb+srv://<usuario>:<contraseña>@<cluster>.mongodb.net/<nombre-db>?retryWrites=true&w=majority
```

Reemplazar:
- `<usuario>` y `<contraseña>` con las credenciales creadas en Database Access
- `<nombre-db>` con el nombre que quieras darle a la base de datos (ej: `medical_rolling`)

Ejemplo completo:

```env
MONGODB_URI=mongodb+srv://admin:miPassword123@cluster0.abc12.mongodb.net/medical_rolling?retryWrites=true&w=majority
```

### Opción B — MongoDB local

Si tenés MongoDB instalado localmente, la URI es simplemente:

```env
MONGODB_URI=mongodb://localhost:27017/medical_rolling
```

> Las colecciones (`users`, `doctors`, `appointments`) **se crean automáticamente** por Mongoose al ejecutar el servidor por primera vez. No es necesario crearlas manualmente.

---

##  Deploy

| Capa | Plataforma | URL |
|---|---|---|
| **Backend** | Vercel | *(URL del backend en Vercel)* |
| **Frontend** | Vercel | https://frontend-medical-rolling.vercel.app |

---

##  Licencia

ISC
