# JobMatch — Tu radar de vacantes

App personal para gestionar tu búsqueda de empleo con análisis de IA (Gemini / OpenRouter) y persistencia en la nube.

---

## 🚀 Credenciales de Tu Aplicación (Respaldo)

Si necesitas volver a configurar la aplicación en otro dispositivo, utiliza los siguientes datos en la pestaña **Configuración**:

### 🤖 Proveedor de IA Recomendado: OpenRouter
Si tu clave de Google Gemini falla por cuota o restricciones regionales, cambia el **Proveedor** a `OpenRouter` y genera una clave gratuita en:
* **Enlace para obtener la clave**: https://openrouter.ai/keys

### 🔥 Firebase Configuración
Pega estos valores en la tarjeta de **Firebase** dentro de la app para sincronizar tus vacantes en la nube:

* **API KEY**: `AIzaSyDE6n7xqFSClMOptuFORnlLUkIyzzee4_Y`
* **AUTH DOMAIN**: `jobmatch-app-37e19.firebaseapp.com`
* **PROJECT ID**: `jobmatch-app-37e19`

---

## 🛠️ Stack Tecnológico
- **Frontend**: HTML/JS puro con CSS nativo moderno (Outfit & Inter fonts).
- **Backend (Serverless)**: Consumo directo de APIs de IA (Google AI Studio / OpenRouter).
- **Base de Datos**: Firebase Firestore (persistido en tiempo real en la nube) con fallback a LocalStorage.
- **Deploy**: Vercel (despliegue automático continuo).

---

## 📋 Configuración de Firestore en Firebase Console

Para que tus datos se guarden correctamente, asegúrate de activar las siguientes reglas de lectura/escritura en tu consola de Firebase:

1. Ve a **Firestore Database** en la consola de Firebase.
2. Ve a la pestaña **Reglas** y pega lo siguiente:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```
*Nota: Esta regla está diseñada para uso personal rápido y simplificado. Si vas a compartir tu app con usuarios externos, te recomendamos implementar autenticación.*

---

## 💡 Cómo usar la Aplicación

1. **Completa tu Perfil**: En la pestaña **Mi Trayectoria**, ingresa tus datos básicos, tu historial laboral (trabajos anteriores) y tus habilidades principales.
2. **Analiza Vacantes**: Copia el Job Description (JD) de cualquier vacante en **Analizar vacante** para obtener:
   - Tu porcentaje de compatibilidad (fit).
   - Retroalimentación sobre fortalezas y brechas.
   - Autoevaluación interactiva de las habilidades que pide el puesto.
3. **Genera tu CV**: Con un solo clic, la IA creará un CV adaptado de forma óptima a esa oferta de trabajo específica.
4. **Practica Entrevistas**: Selecciona la vacante guardada en la pestaña **Entrevistas** y simula rondas de preguntas técnicas, conductuales, preguntas difíciles de justificación, o un simulacro libre de entrevista.
