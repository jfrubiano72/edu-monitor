# 🎓 EDU Monitor — Análisis de Dominios .edu.co

> **Herramienta de inteligencia competitiva web para instituciones de educación superior colombianas.**  
> Desarrollada por [Javier Fernando Rubiano Espinosa](https://javierrubiano.com) · VISORIA Intelligence · Behavioral Intelligence Lab

[![Live Demo](https://img.shields.io/badge/🌐_Demo_En_Vivo-GitHub_Pages-137DC5?style=for-the-badge)](https://jfrubiano72.github.io/edu-monitor/)
[![Licencia](https://img.shields.io/badge/Uso-Académico_/_Institucional-C8963E?style=for-the-badge)](#licencia)
[![Fuente](https://img.shields.io/badge/Datos-Wayback_Machine_CDX_API-10b981?style=for-the-badge)](https://web.archive.org/cdx/search/)

---

## 📌 ¿Qué es EDU Monitor?

**EDU Monitor** es una aplicación web de una sola página (SPA) que permite monitorear y comparar la **frecuencia de actualización de sitios web** de universidades colombianas con dominio `.edu.co`, utilizando como fuente de datos la [Wayback Machine CDX API](https://github.com/internetarchive/wayback/tree/master/wayback-cdx-server) de Internet Archive.

El número de capturas históricas registradas por Internet Archive actúa como un **proxy objetivo y verificable** de la actividad digital de cada institución: a mayor frecuencia de actualización del sitio, más capturas registra el archivo automáticamente.

---

## 🏛️ Caso de uso principal

Desarrollado originalmente para apoyar la **Escuela de Negocios de la Universidad de La Salle** (`unisalle.edu.co`) en el monitoreo de su presencia digital frente a los principales competidores del ecosistema de educación superior en Bogotá y Colombia.

**Instituciones configuradas por defecto:**

| Institución | Dominio | Activo por defecto |
|---|---|:---:|
| Universidad de Los Andes | `uniandes.edu.co` | ✅ |
| Universidad del Rosario | `urosario.edu.co` | ✅ |
| Pontificia Universidad Javeriana | `javeriana.edu.co` | ✅ |
| Universidad Santo Tomás | `usantotomas.edu.co` | ✅ |
| Politécnico Grancolombiano | `poligran.edu.co` | ✅ |
| Universidad de La Sabana | `unisabana.edu.co` | ✅ |
| Corporación Universitaria Minuto de Dios | `uniminuto.edu.co` | ✅ |
| Universidad Externado de Colombia | `uexternado.edu.co` | ⬜ |
| Universidad EAN | `ean.edu.co` | ⬜ |
| Universidad Jorge Tadeo Lozano | `utadeo.edu.co` | ⬜ |
| Universidad El Bosque | `unbosque.edu.co` | ⬜ |
| Universidad ECCI | `ecci.edu.co` | ⬜ |

> Cualquier dominio `.edu.co` puede ser analizado como dominio principal.

---

## 📊 Funcionalidades

### 5 pestañas de análisis

| Pestaña | Contenido |
|---|---|
| ⚙️ **Configurar** | Selección de dominio principal, período y competidores |
| 📊 **Resumen** | KPIs principales · Evolución semanal · Actividad por día y hora · Hallazgos automáticos |
| 🏆 **Comparativa** | Ranking horizontal · Radar multidimensional · Línea de tiempo multi-dominio · Tabla detallada |
| 📈 **Estadísticas** | Estadística descriptiva completa · Histograma · Regresión lineal · Δ% semanal · Media móvil MA-4 |
| 📅 **Historial** | Últimas 30 capturas con fecha y hora UTC |

### Indicadores estadísticos calculados

- **Media y mediana** semanal de capturas
- **Desviación estándar** y **Coeficiente de Variación (CV%)**
- **Regresión lineal** con slope de tendencia
- **Media Móvil MA-4** (4 semanas)
- **Δ% semana a semana** (variación relativa)
- **Radar multidimensional** (Total · Prom/sem · Semanas activas · Máx/sem · Consistencia)
- **Posición relativa** vs. promedio de competidores

### Exportación
- **CSV completo** con todos los indicadores + desglose semanal con media móvil

---

## 🛠️ Stack tecnológico

```
HTML5 + CSS3 + JavaScript vanilla
Chart.js 4.4.0 (visualizaciones)
Wayback Machine CDX API (fuente de datos)
Google Fonts: DM Serif Display + Plus Jakarta Sans + DM Mono
Sin dependencias de servidor · Sin base de datos · Sin autenticación
```

**Arquitectura:** Single Page Application (SPA) — un único archivo `index.html` autocontenido.  
**Compatibilidad:** Chrome, Safari, Firefox, Edge · Desktop y móvil.

---

## 🚀 Uso local

1. Descarga `index.html`
2. Ábrelo directamente en tu navegador
3. Configura el dominio y los competidores
4. Presiona **Iniciar Análisis**

> ⚠️ **Nota CORS:** Para uso local o desde iframes embebidos, la app utiliza proxies CORS públicos como fallback automático. Para resultados óptimos, se recomienda acceder desde la URL de GitHub Pages.

---

## 🌐 Demo en línea

Accede a la versión publicada en:

**[https://jfrubiano72.github.io/edu-monitor/](https://jfrubiano72.github.io/edu-monitor/)**

---

## 📐 Metodología

### Fuente de datos
La **Wayback Machine CDX API** de Internet Archive es una API pública y gratuita que permite consultar el índice histórico de capturas de cualquier URL. Se consulta con los siguientes parámetros:

```
https://web.archive.org/cdx/search/cdx
  ?url={dominio}
  &output=json
  &fl=timestamp,statuscode
  &from={fecha_inicio}
  &to={fecha_fin}
  &limit=5000
  &filter=statuscode:200
```

Solo se contabilizan capturas con código HTTP 200 (exitosas).

### Interpretación
El robot de Internet Archive rastrea con mayor frecuencia los sitios que **cambian más seguido**. Por tanto:

- **Alta frecuencia de capturas** → sitio activo, con actualizaciones frecuentes de contenido
- **Baja frecuencia de capturas** → sitio estático o con pocas actualizaciones
- **Tendencia positiva (slope > 0)** → actividad web creciente en el período

> Esta métrica es **objetiva, histórica y verificable públicamente** para cualquier dominio en internet.

---

## 🎨 Diseño

Paleta de colores institucional VISORIA Intelligence:

| Color | Hex | Uso |
|---|---|---|
| Navy | `#0B2545` | Fondo principal |
| Teal | `#137DC5` | Acento primario · La Salle |
| Gold | `#C8963E` | Acento secundario · Énfasis |
| Success | `#10b981` | Indicadores positivos |

---

## 👤 Autor

**Javier Fernando Rubiano Espinosa**  
Consultor Senior en Neuromarketing · Docente Universitario · Empresario  
Director — [VISORIA Intelligence](https://javierrubiano.com)  
Behavioral Intelligence Lab

📧 Contacto: [javierrubiano.com](https://javierrubiano.com)  
🐙 GitHub: [@jfrubiano72](https://github.com/jfrubiano72)

---

## 📄 Licencia

Uso académico e institucional. Desarrollado en el marco de proyectos de inteligencia estratégica para la educación superior colombiana.

© 2025 Javier Fernando Rubiano Espinosa · VISORIA Intelligence

---

*Construido con datos de [Internet Archive](https://archive.org) · Wayback Machine CDX API*
