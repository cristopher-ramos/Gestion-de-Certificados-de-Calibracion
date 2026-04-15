## Plataforma de Gestión de Certificados de Calibración

## Contexto del problema

IPC Associates es una empresa especializada en servicio técnico 
y calibración de equipos de medición. Contaba con más de 5,000 
certificados históricos en PDF sin estructura digital, lo que 
hacía imposible responder preguntas básicas como:

- ¿Qué equipos de un cliente tienen calibración próxima a vencer?
- ¿Existe el certificado N° X emitido en el año Y?
- ¿Qué comercial es responsable de cada cliente?

El ingreso manual de datos tomaba semanas y generaba errores 
humanos constantes.

---

## Solución implementada

Diseñé e implementé un ecosistema completo de gestión documental 
que automatiza desde la extracción de datos hasta la validación 
pública para clientes externos.

---

## Arquitectura del sistema

PDFs históricos
↓
[RPA - Power Automate Desktop]
Extracción masiva con Regex
↓
[Excel maestro consolidado]
↓
[Flujo Power Automate Online]
Carga, organización y renombramiento
↓
[SharePoint — Dos repositorios]
├── Repositorio interno (área calibraciones)
└── Repositorio comercial (segmentado por cliente)
↓
[Power BI — Validación pública]
Embebido en web de la empresa
Clientes verifican autenticidad de sus certificados
↓
[Power Apps — Seguimiento comercial]
Indicadores de desempeño por comercial

---

## Módulos del sistema

### 1. RPA — Extracción masiva de PDFs

Bot desarrollado en Power Automate Desktop que procesa cada 
certificado PDF de forma automática.

**Campos extraídos por certificado:**
- Número de certificado
- Fecha de emisión
- Fecha de calibración
- Empresa cliente
- Tipo de equipo, marca y modelo
- Número de serie
- Número de acreditación INACAL

**Técnicas utilizadas:**
- Expresiones regulares (Regex) para extracción de fechas
- CropText con flags específicos por sección del documento
- Extracción de tablas de página 2 para datos INACAL
- Renombramiento automático: `NUMERO_CERTIFICADO_MARCA.pdf`

**Resultado:** Procesamiento de 5,000+ documentos con reducción 
del 95% en tiempo de digitación y eliminación de errores humanos.

---

### 2. Repositorio documental en SharePoint

Dos estructuras diferenciadas según el tipo de usuario:

**Repositorio interno** (área de calibraciones)
