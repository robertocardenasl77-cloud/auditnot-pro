# AuditNot Pro — Contexto del Proyecto

## Descripción
Sistema de gestión de documentos notariales (notarías) con autenticación Google y base de datos en Firebase Firestore.

## Stack
- **Frontend**: HTML5 + JavaScript vanilla (sin framework, sin npm)
- **Backend**: Firebase Firestore + Firebase Auth (Google OAuth)
- **Hosting**: Firebase Hosting
- **Admin**: roberto.cardenasl77@gmail.com

## Firebase
- **Project ID**: `auditnot-pro`
- **Default URL**: `https://auditnot-pro.web.app`
- **Dominio personalizado**: `https://www.notar-ia.com.mx`
- **DNS**: GoDaddy — CNAME `www` → `auditnot-pro.web.app`

## Estructura del proyecto
```
auditnot-pro/
├── index.html        ← toda la app (HTML + CSS + JS en un solo archivo)
├── firebase.json     ← config de Firebase Hosting (SPA rewrite, no-cache)
├── .firebaserc       ← apunta al proyecto auditnot-pro
└── functions/        ← Firebase Cloud Functions (si aplica)
```

## Ramas importantes
| Rama | Descripción |
|---|---|
| `main` | Base inicial (marzo 2026) — NO usar para deploy |
| `claude/notary-account-linking-4gjFz` | Versión activa con sidebar + vinculación notario-notaría |
| `claude/connect-notaria-domain-p88Hs` | Solo agrega firebase.json y .firebaserc |

## Versión correcta
- La versión correcta es la de la rama `claude/notary-account-linking-4gjFz`
- Tiene sidebar con navegación a la izquierda
- Tamaño aproximado: ~87KB (comprimido desde Firebase)
- Fue restaurada el 20 de abril 2026 desde el historial de Firebase Hosting

## Flujo de deploy
```bash
# Siempre trabajar desde esta rama
git checkout claude/notary-account-linking-4gjFz

# Desplegar a Firebase (ambos dominios se actualizan)
firebase deploy --only hosting
```

## Dominios autorizados en Firebase Auth
Ambos dominios están autorizados para Google Sign-In:
- `auditnot-pro.web.app`
- `notar-ia.com.mx`
- `www.notar-ia.com.mx`

## Roles de usuario
- `admin`: acceso total, puede aprobar usuarios y asignar notarías
- `notaria`: ve solo su notaría asignada, sin formulario de nueva notaría

## Advertencias
- NO hacer deploy desde la rama `main` — tiene versión antigua sin sidebar
- NO subir `index.html` directamente a GitHub sin verificar que es la versión correcta
- Siempre verificar en `auditnot-pro.web.app` antes de confirmar que el deploy fue exitoso
- Si algo sale mal, usar Firebase Console → Hosting → Historial de versiones para hacer rollback
