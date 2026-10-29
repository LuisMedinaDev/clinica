# Clínica San Jorge — Sistema de Historia Clínica Digital

**Next.js 14 · TypeScript · Tailwind CSS**

Portal institucional y sistema de historia clínica digital para el Hospital de Clínicas San Jorge, Temblador, Estado Monagas, Venezuela.

---

## Rutas de la aplicación

| Ruta | Descripción |
|------|-------------|
| `/` | Portal institucional: servicios, directorio médico, solicitud de citas |
| `/historias` | Sistema de historia clínica digital (formulario + expedientes) |
| `/portal` | Alias del portal institucional |

---

## Cómo iniciar

```bash
# Instalar dependencias
npm install

# Modo desarrollo (hot-reload)
npm run dev

# Build de producción
npm run build

# Servidor de producción
npm start
```

El servidor de desarrollo arranca en `http://localhost:3000`.

---

## Estructura del proyecto

```
clinica-san-jorge/
├── app/
│   ├── globals.css          ← Estilos globales + Tailwind + print A4
│   ├── layout.tsx           ← Root layout (HTML shell)
│   ├── page.tsx             ← Portal institucional (ruta /)
│   ├── portal/
│   │   └── page.tsx         ← Alias /portal
│   └── historias/
│       └── page.tsx         ← Sistema de historia clínica (ruta /historias)
├── next.config.mjs
├── tailwind.config.js
├── postcss.config.js
├── tsconfig.json
├── package.json
├── LEEME.md                 ← Documentación clínica y de uso
├── ejemplo-transcripcion.json
├── index.html               ← Versión anterior (standalone HTML, conservada)
└── portal.html              ← Versión anterior del portal (standalone HTML, conservada)
```

---

## Funcionalidades del sistema clínico (`/historias`)

- **Formulario de historia clínica** con 7 secciones (I–VII):
  - Datos generales · Antecedentes patológicos y hábitos
  - Antecedentes familiares · Antecedentes ocupacionales
  - Signos vitales (tabla dinámica) · Evolución/notas médicas · Reporte de enfermería
- **Alertas fisiológicas automáticas** bajo signos vitales: crisis hipertensiva, taquicardia, fiebre, hipoxemia
- **Autoguardado** en borrador (localStorage) mientras se escribe
- **Barra lateral de pacientes**: lista agrupada por paciente con buscador (nombre/expediente)
- **Historial por paciente**: múltiples consultas en un expediente
- **Adjuntos** (PDF/JPG/PNG, máx. 15 MB) guardados en IndexedDB del navegador
- **Imprimir/PDF** en formato A4: oculta controles, agrega pie de página con fecha
- **Exportar a Word** (.doc): genera documento completo con tablas y firmas
- **Atajos**: `Ctrl+S` guardar · `Ctrl+P` imprimir

> ⚠️ Los datos viven exclusivamente en el navegador del equipo (localStorage + IndexedDB). El único respaldo digital son los archivos Word/PDF que se exporten. **No subir a GitHub ni a hosting público** — el sistema maneja expedientes clínicos reales.

---

## Siguiente paso técnico (referencia)

1. **Base de datos**: migrar de localStorage a Supabase / Firebase
2. **Login por rol**: médico, enfermería, recepción
3. **Búsqueda avanzada** por edad, fecha, diagnóstico
4. **Plantillas** de evolución y recetas
# clinica
# clinica2
