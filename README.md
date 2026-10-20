# 🧊 Smart Fridge - Nevera Intel·ligent amb Firebase i IA

![Kotlin](https://img.shields.io/badge/Kotlin-2.2.10-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)
![Android SDK](https://img.shields.io/badge/Android%20SDK-30%2B-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-Auth%20%7C%20Firestore%20%7C%20AI-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)

Aplicación nativa para Android desarrollada en **Kotlin** como parte de la asignatura **A1 - Pràctica Backend al núvol** (*Institut Marianao*). 

La aplicación permite a cada usuario gestionar la despensa/nevera de su hogar de forma individual y generar **sugerencias de recetas personalizadas e inteligentes mediante IA** utilizando los ingredientes disponibles en tiempo real.

---

## 🚀 Características Principales

### 🔐 1. Autenticación de Usuarios (Firebase Authentication)
* **Inicio de Sesión y Registro:** Acceso seguro mediante correo electrónico y contraseña.
* **Validación de Formularios:** Comprobación de campos requeridos, formato de correo y coincidencia de contraseñas con gestión centralizada de errores.
* **Aislamiento de Datos:** Cada usuario accede únicamente a sus propios ingredientes y despensa.
* *(Ampliación)* Validación/Verificación del correo electrónico del usuario.

### 📦 2. Gestión de Inventario e Ingredientes (Cloud Firestore)
* **CRUD Completo:** Alta, lectura, edición y eliminación de ingredientes en Firestore.
* **Confirmación de Seguridad:** Diálogo de confirmación antes de eliminar cualquier elemento de la lista.
* **Carga/Edición Dinámica:** Al seleccionar un ingrediente de la lista, se cargan sus datos en el formulario para modificarlo.
* **Limpieza Rápida:** Botón *Clear* para resetear el formulario y añadir nuevos elementos rápidamente.
* **Categorización:** Clasificación de ingredientes por tipo (Fruit & Vegs, Meat & Fish, Dairy & Eggs, Bakery & Bread, Grains & Pasta, Sauces & Condiments, Drinks, Leftovers, Other).

### 🤖 3. Sugerencias de Recetas con IA (Firebase AI Logic)
* **Generación Automática:** Obtención de recetas personalizadas según los ingredientes en stock.
* **Formateo Markdown:** Procesamiento de respuesta formateada con encabezados, listas con viñetas y texto en negrita.
* **Visualización de Resultados:** Presentación de la receta en una nueva actividad dedicada mediante renderizado fluido con **Markwon**.
* **Feedback de Usuario:** Indicador visual (*Loading/Progress*) durante la llamada a la IA.

---

## 📊 Modelo de Datos (Cloud Firestore)

Estructura de la colección `ingredients` asociada a la cuenta del usuario autenticado (`users/{userId}/ingredients/{ingredientId}`):

| Campo | Tipo | Requerido | Descripción |
| :--- | :--- | :---: | :--- |
| `name` | `String` | **Sí** | Nombre del ingrediente (ej: *"Eggs"*). |
| `quantity` | `Int` | **Sí** | Cantidad disponible (ej: `6`). |
| `unit` | `String?` | No | Unidad de medida (`units`, `grams`, `kg`, `liters`, `ml`, `packs`...). |
| `category` | `String?` | No | Categoría (*Fruit & Vegs*, *Meat & Fish*, *Dairy & Eggs*, etc.). |
| `expiration` | `Date?` | No | Fecha de caducidad. |
| `addedAt` | `Date` | **Sí** | Fecha de creación/registro. |

---

## 📱 Pantallas de la Aplicación

1. **Pantalla de Login:** Formularios de acceso con validación de credenciales. Botón de navegación al registro.
2. **Pantalla de Registro:** Creación de cuenta con verificación de contraseña.
3. **Pantalla de Nevera / Despensa (Principal):**
   * Formulario superior para dar de alta/editar ingredientes.
   * `RecyclerView` con la lista en tiempo real de los ingredientes almacenados.
   * Botón para llamar a la IA (**Generar Sugerencia de Receta**).
   * Opción para cerrar sesión (*Logout*).
4. **Pantalla de Receta Sugerida:** Muestra la receta generada por la IA renderizando el texto Markdown mediante `Markwon`.

---

## 🛠️ Tecnologías y Librerías Utilizadas

* **Lenguaje:** [Kotlin](https://kotlinlang.org/)
* **Plataforma:** Android SDK (API 30+)
* **Arquitectura & UI:** Android Jetpack, `ViewBinding`, `ConstraintLayout`, `RecyclerView`.
* **Backend & Cloud:**
  * [Firebase Authentication](https://firebase.google.com/docs/auth)
  * [Cloud Firestore](https://firebase.google.com/docs/firestore)
  * [Firebase AI Logic / Vertex AI for Firebase](https://firebase.google.com/docs/vertex-ai)
* **Renderizado de Markdown:**
  * [Markwon](https://github.com/noties/Markwon) (`io.noties.markwon:core`)

---

## 🔧 Configuración e Instalación

### Requisitos Previos
* Android Studio (Ladybug o versión superior).
* Cuenta en [Firebase Console](https://console.firebase.google.com/).

### Pasos de Configuración

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/TU_USUARIO/smart-fridge-firebase-ai.git
   ```

2. **Configurar Firebase:**
   * Crea un proyecto en Firebase Console.
   * Habilita **Firebase Authentication** (proveedor Email/Password).
   * Habilita **Cloud Firestore** en modo de prueba o con reglas de seguridad por usuario.
   * Descarga el archivo `google-services.json` y colócalo dentro del directorio `app/`.

3. **Abrir y Ejecutar:**
   * Abre el proyecto en Android Studio.
   * Sincroniza las dependencias de Gradle (`Sync Project with Gradle Files`).
   * Ejecuta la aplicación en un emulador o dispositivo físico (Android 11+).

---

## 📄 Licencia

Este proyecto se distribuye bajo la licencia **MIT**. Consulta el archivo `LICENSE` para más información.

---

Developed for **Institut Marianao** - *A1 Pràctica Backend al núvol*.
