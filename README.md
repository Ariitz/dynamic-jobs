# JobMatch — Tu radar de vacantes

App personal para gestionar tu búsqueda de empleo con análisis de IA (Gemini).

## Stack
- HTML/JS puro — sin frameworks, sin build
- Gemini 2.0 Flash — análisis de fit, generación de CV, simulador de entrevistas
- Firebase Firestore — persistencia en la nube
- Deploy: Vercel o GitHub Pages (gratis)

---

## Setup en 5 pasos

### 1. Obtén tu Gemini API Key (gratis)
1. Ve a https://aistudio.google.com/app/apikey
2. Crea una key
3. Cópiala — la pegas en la app en Configuración > Gemini API Key

### 2. Crea tu proyecto Firebase
1. Ve a https://console.firebase.google.com
2. "Crear proyecto" → dale un nombre (ej: jobmatch-tuapellido)
3. Desactiva Google Analytics (no lo necesitas)
4. Ve a **Firestore Database** → "Crear base de datos" → Modo producción
5. Ve a **Configuración del proyecto** (ícono de engranaje) → pestaña "General"
6. Baja hasta "Tus apps" → haz clic en el ícono `</>` (Web)
7. Registra la app → copia los valores de `firebaseConfig`:
   - `apiKey`
   - `authDomain`
   - `projectId`

### 3. Configura las reglas de Firestore
En Firebase Console → Firestore → Reglas, pega esto:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```
> ⚠️ Esto es para uso personal. Si compartes la app, agrega autenticación.

### 4. Deploy en Vercel (recomendado)
1. Sube la carpeta a un repo en GitHub
2. Ve a https://vercel.com → "New Project"
3. Importa el repo → deploy automático
4. Tu app queda en `https://tu-app.vercel.app`

**O con GitHub Pages:**
1. Repo en GitHub → Settings → Pages → Source: main branch
2. Tu app queda en `https://tuusuario.github.io/nombre-repo`

### 5. Abre la app y configura
1. Ve a **Configuración** en el menú lateral
2. Pega tu Gemini API Key
3. Pega los datos de Firebase (apiKey, authDomain, projectId)
4. Sube tu CV en **Mi CV** (formato .txt)
5. Completa tu **Perfil profesional**

---

## Cómo usar

### Analizar una vacante
1. Ve a "Analizar vacante"
2. Pega el JD completo
3. Haz clic en "Analizar con IA ✦"
4. Revisa el % de fit, skills que tienes/faltan, y consejos
5. Genera tu CV personalizado con un clic
6. Guarda la vacante para seguimiento

### Preparar una entrevista
1. Ve a "Entrevistas"
2. Selecciona una vacante guardada
3. Elige el tipo: técnica, conductual, preguntas difíciles, o simulacro libre
4. Practica con la IA como entrevistador

---

## Notas
- La Gemini API Key se guarda en localStorage del navegador (solo tú la ves)
- Firebase guarda las vacantes en la nube — accesibles desde cualquier dispositivo
- Sin Firebase, las vacantes se guardan en localStorage (solo en ese navegador)
