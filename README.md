# Gestor de Tareas Académicas

Este proyecto es una aplicación web front-end desarrollada con React para ayudar a los estudiantes a gestionar sus tareas académicas. Permite a los usuarios registrarse, iniciar sesión y realizar operaciones CRUD (Crear, Leer, Actualizar, Eliminar) sobre sus tareas. La aplicación utiliza `json-server` como backend simulado para la persistencia de datos y `localStorage` para gestionar la sesión del usuario.

## Características Principales

* **Autenticación de Usuarios:**
    * Registro de nuevos usuarios.
    * Inicio de sesión con correo y contraseña.
    * Protección de rutas para el dashboard.
    * Cierre de sesión.
* **Gestión de Tareas:**
    * Crear nuevas tareas (título, materia, fecha límite, estado).
    * Listar tareas existentes en formato de tarjetas.
    * Editar la información de tareas existentes.
    * Marcar tareas como "completada" o "pendiente".
    * Eliminar tareas (con confirmación).
* **Funcionalidades Adicionales:**
    * Buscar tareas por título o materia.
    * Filtrar tareas por materia o estado.
    * Resumen visual con la cantidad total de tareas, tareas pendientes y tareas completadas.
    * Interfaz de usuario clara y responsiva utilizando Bootstrap.
    * Notificaciones y confirmaciones con SweetAlert2.

## Tecnologías Utilizadas

* **React (v18.2.0):** Biblioteca principal para la construcción de la interfaz de usuario.
    * Hooks de React (`useState`, `useEffect`, `useCallback`, `useMemo`).
* **React Router DOM (v6.23.1):** Para la gestión de rutas en la aplicación.
* **json-server (v0.17.4 / 1.0.0-beta):** Para simular una API RESTful y persistir datos localmente en un archivo `db.json`.
* **Bootstrap (v5.3.x):** Framework CSS para el diseño y la maquetación responsiva.
* **SweetAlert2 (v11.x.x):** Para mostrar alertas y modales de confirmación atractivos.
* **Vite:** Herramienta de desarrollo front-end para un entorno de desarrollo rápido y eficiente.
* **JavaScript (ES6+):** Lenguaje de programación principal.
* **HTML5 y CSS3:** Para la estructura y estilos base.

## Estructura del Proyecto


vite-prueba/
├── public/                 # Archivos estáticos públicos
├── src/
│   ├── components/         # Componentes reutilizables de React
│   │   ├── ProtectedRoute.jsx # Componente para proteger rutas
│   │   ├── TaskCard.jsx       # Componente para mostrar una tarea individual
│   │   └── TaskForm.jsx       # Componente para el formulario de crear/editar tarea
│   ├── pages/              # Componentes que representan páginas completas
│   │   ├── Dashboard.jsx
│   │   ├── Login.jsx
│   │   └── Register.jsx
│   ├── App.css             # Estilos globales o específicos de App
│   ├── App.jsx             # Componente principal de la aplicación y configuración de rutas
│   ├── index.css           # Estilos globales principales
│   └── main.jsx            # Punto de entrada de la aplicación React
├── .eslintrc.cjs           # Configuración de ESLint (puede variar el nombre)
├── .gitignore              # Archivos y carpetas ignorados por Git
├── db.json                 # Base de datos simulada para json-server
├── index.html              # Plantilla HTML principal
├── package-lock.json
├── package.json            # Dependencias y scripts del proyecto
└── vite.config.js          # Configuración de Vite


## Instalación y Puesta en Marcha

Sigue estos pasos para configurar y ejecutar el proyecto en tu entorno local:

1.  **Clonar el Repositorio (si aplica):**
    ```bash
    git clone <URL_DEL_REPOSITORIO>
    cd vite-prueba
    ```

2.  **Instalar Dependencias:**
    Asegúrate de tener Node.js y npm (o yarn) instalados.
    ```bash
    npm install
    ```
    o
    ```bash
    yarn install
    ```

3.  **Configurar `db.json`:**
    El archivo `db.json` en la raíz del proyecto actúa como una base de datos simulada. Puedes modificarlo para añadir usuarios o tareas iniciales. Un ejemplo de estructura es:
    ```json
    {
      "users": [
        {
          "id": "1", // json-server puede generar IDs numéricos si no se proveen al crear
          "name": "Tu Nombre",
          "email": "tu@correo.com",
          "password": "tucontraseña"
        }
      ],
      "tareas": [
        {
          "id": "t1", // json-server puede generar IDs si no se proveen
          "userId": "1", // Debe coincidir con el id de un usuario
          "titulo": "Mi Primera Tarea",
          "materia": "General",
          "fechaLimite": "YYYY-MM-DD",
          "estado": "pendiente"
        }
      ]
    }
    ```

4.  **Iniciar la API Simulada (json-server):**
    Abre una terminal y ejecuta:
    ```bash
    npm run api
    ```
    Esto iniciará `json-server` (generalmente en `http://localhost:3001`). Mantén esta terminal abierta.

5.  **Iniciar la Aplicación React (Vite):**
    Abre otra terminal y ejecuta:
    ```bash
    npm run dev
    ```
    Esto iniciará el servidor de desarrollo de Vite (generalmente en `http://localhost:5173` o un puerto similar). La aplicación se abrirá automáticamente en tu navegador.

¡Y listo! Ahora deberías poder interactuar con la aplicación de gestión de tareas.

## Scripts Disponibles

En el archivo `package.json`, encontrarás los siguientes scripts:

* `npm run dev`: Inicia el servidor de desarrollo de Vite.
* `npm run build`: Compila la aplicación para producción.
* `npm run api`: Inicia `json-server` para simular el backend.
* `npm run lint`: Ejecuta ESLint para analizar el código.
* `npm run preview`: Previsualiza la build de producción localmente.

## Despliegue

Para desplegar esta aplicación, necesitarías:

1.  **Un backend real:** `json-server` es solo para desarrollo. Deberías construir una API real (con Node.js/Express, Python/Django, etc.) y desplegarla.
2.  **Actualizar las URLs de la API:** En el código React, cambiar las URLs `http://localhost:3001/...` por las URLs de tu API desplegada.
3.  **Compilar el proyecto React:**
    ```bash
    npm run build
    ```
    Esto generará una carpeta `dist/` con los archivos estáticos optimizados.
4.  **Desplegar los archivos estáticos:** Puedes desplegar el contenido de la carpeta `dist/` en plataformas como:
    * Vercel
    * Netlify
    * GitHub Pages
    * AWS S3, Google Cloud Storage, etc.

    Estas plataformas suelen ofrecer integración continua y despliegue automático desde repositorios Git.
