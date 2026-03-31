# Revisores eBird Colombia

Formulario de registro para la construcción de una red nacional voluntaria de revisores de registros en eBird Colombia.

🔗 **[Ver formulario en vivo](https://setase24.github.io/revisores-ebird-colombia/)**  
📊 **[Ver registros en tiempo real](https://docs.google.com/spreadsheets/d/1ilPIeY_WfYw4aMCD441CbBDmWEA71anyD3vTojly_kI/edit)**

---

## ¿Qué es esto?

eBird Colombia tiene un potencial enorme para documentar la distribución de las aves en el país, pero aprovecharlo bien depende de contar con datos revisados y de alta calidad. Este proyecto busca identificar y conectar a personas interesadas en revisar registros inusuales en sus regiones de experiencia.

Es una **iniciativa independiente**, no oficial de eBird o el Cornell Lab of Ornithology.

---

## ¿Qué hace el formulario?

El formulario recopila información de personas interesadas en ser revisores, organizada en 6 secciones:

1. **Datos personales** — nombre, correo, país, afiliación y perfil eBird
2. **Experiencia ornitológica** — años de experiencia, motivaciones, grupos taxonómicos y familiaridad con eBird
3. **Zona geográfica** — selector interactivo con mapa de Colombia por departamentos y zonas biogeográficas Olson 2017
4. **Curso eBird Essentials** — verificación de diploma del curso oficial
5. **Disponibilidad y motivación** — horas disponibles por semana y motivación principal
6. **Evidencia de calidad** — enlace opcional a un registro raro documentado o publicación científica como coautor

---

## Características técnicas

- **Verificación automática de eBird** — al pegar la URL del perfil, consulta un proxy en Google Apps Script y muestra en tiempo real el nombre del usuario, listas subidas y listas completas en Colombia
- **Mapa interactivo D3.js** — dos vistas: departamentos de Colombia y zonas biogeográficas Olson 2017, con selección por prioridades
- **Diploma en base64** — el archivo se convierte a base64 en el cliente y se envía al servidor para guardarse en Google Drive
- **Barra de progreso** — refleja el avance del formulario en tiempo real
- **Diseño responsivo** — funciona en móvil y escritorio

---

## Arquitectura

```
Formulario (GitHub Pages)
    │
    ├── Proxy eBird (Google Apps Script)
    │     └── Consulta ebird.org y devuelve nombre + estadísticas de listas
    │
    └── Bot formulario (Google Apps Script)
          ├── Guarda datos en Google Sheets (hoja Pública + hoja Privada)
          └── Guarda diploma en Google Drive
```

### Google Apps Scripts

| Nombre | Función |
|--------|---------|
| `bot_ebird_revisores` | Recibe el POST del formulario → guarda en Sheets y Drive |
| `ebird-proxy-prueba` | Proxy para consultar estadísticas de eBird sin CORS |

### Google Sheets

- **Hoja Pública** — todos los campos excepto correo electrónico (visible para cualquiera)
- **Hoja Privada** — todos los campos incluyendo correo

---

## Datos recopilados

| Campo | Privado |
|-------|---------|
| Nombre y apellido | No |
| Correo electrónico | ✅ Sí |
| País de residencia | No |
| Afiliación | No |
| Perfil eBird | No |
| Experiencia y motivaciones | No |
| Zonas geográficas de interés | No |
| Diploma eBird Essentials | Drive privado |
| Disponibilidad y motivación | No |
| Registro raro / publicación | No |

---

## Créditos

Desarrollado por **Sebastián Tabares Segovia**  
Biólogo y estudiante de Estadística · Universidad Nacional de Colombia

Foto del héroe: *Poecilotriccus palmeri* © Sebastián Tabares Segovia

---

## Nota

Este formulario **no es una convocatoria oficial** de eBird ni del Cornell Lab. Es un registro de interesados como paso previo para organizar y visibilizar la comunidad ornitológica colombiana con capacidad de revisar registros inusuales.
