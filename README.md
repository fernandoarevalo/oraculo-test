# 🔮 Oráculo — Lectura de Cartas con IA

App web para lectura personalizada de cartas (Tarot, Oráculo, Baraja Española) usando visión artificial de Claude.

---

## 📁 Estructura del proyecto

```
oraculo-netlify/
├── public/
│   └── index.html          ← La app completa
├── netlify/
│   └── functions/
│       └── claude.js       ← Función serverless (protege tu API key)
├── netlify.toml             ← Configuración de Netlify
└── README.md
```

---

## 🚀 Pasos para publicar en Netlify

### 1. Consigue tu API Key de Anthropic
- Ve a → https://console.anthropic.com
- Crea una cuenta o inicia sesión
- En el menú lateral: **API Keys** → **Create Key**
- Copia la key (empieza con `sk-ant-...`)
- ⚠️ Guárdala bien, solo se muestra una vez

### 2. Sube el proyecto a GitHub
- Ve a https://github.com y crea un repositorio nuevo (puede ser privado)
- Sube todos los archivos de esta carpeta al repositorio

### 3. Conecta GitHub con Netlify
- Ve a https://app.netlify.com
- Clic en **"Add new site"** → **"Import an existing project"**
- Elige **GitHub** y selecciona tu repositorio
- Configuración de build:
  - **Publish directory:** `public`
  - **Functions directory:** `netlify/functions`
- Clic en **Deploy site**

### 4. Agrega tu API Key como variable de entorno
- En el dashboard de Netlify, ve a tu sitio
- **Site configuration** → **Environment variables** → **Add variable**
- Name: `ANTHROPIC_API_KEY`
- Value: `sk-ant-TUKEY...` (la que copiaste)
- Clic en **Save**

### 5. Redespliega
- Ve a **Deploys** → **Trigger deploy** → **Deploy site**
- ¡Listo! Tu app estará en `https://tu-sitio.netlify.app`

---

## 🔒 Seguridad

Tu API key **nunca** es visible en el frontend. El flujo es:

```
Navegador → /api/claude (Netlify Function) → API de Anthropic
                ↑
         API key segura en
         variables de entorno
```

---

## 💡 Uso

1. Ingresa nombre y fecha de nacimiento
2. Escribe tu pregunta
3. Sube una foto de tus cartas
4. La IA identifica las cartas y genera tu interpretación personalizada

---

## ⚙️ Personalización

Para cambiar el modelo de IA, edita `netlify/functions/claude.js` y `public/index.html`:
```js
model: "claude-sonnet-4-5-20250929"  // puedes cambiarlo
```
