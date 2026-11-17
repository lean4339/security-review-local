# Security Review · Local & Marketplace

**Revisar cambios concretos, construir pruebas útiles y aprender de la evidencia.**

[English](README.md) · **Español**

Una copia de la skill local security-review, incluidos cambios ausentes del repositorio publicado. Las variantes de marketplace se conservan por separado porque difieren en contenido y condiciones de distribución.

## Qué cubre

| Área | Guía |
| --- | --- |
| Revisión de commits | Resolver la revisión solicitada y distinguir el código confirmado de los cambios del árbol de trabajo. |
| Desarrollo y pruebas | Relacionar límites de autorización, entradas no confiables y fallos con comprobaciones funcionales y de seguridad pertinentes. |
| Aprendizaje | Usar referencias OWASP y ejercicios para aplicaciones web, MCP, LLM y agentes. |

## Primeros pasos

Leé [SKILL.md](SKILL.md) y después las referencias pertinentes. Dale a un agente compatible acceso al paquete y a los archivos autorizados. Conservá las carpetas adyacentes a SKILL.md; copiar solamente ese archivo puede romper sus referencias.

### Requisitos

Un agente compatible y un proyecto autorizado para trabajar sobre código. El estudio puede comenzar sin repositorio. La skill pide verificar la edición OWASP aplicable al invocarla; el empaquetado no realizó esa investigación.

### Ejemplo de pedido

> Usá security-review sobre este commit. Resolvé el SHA completo, inspeccioná el límite de autorización y proponé una prueba de regresión que distinga el comportamiento vulnerable del corregido.

## Contenido del paquete

| Ruta | Función |
| --- | --- |
| [SKILL.md](SKILL.md) | Instrucciones del agente y flujo de trabajo |
| [references](references) | Módulos de apoyo y fuentes |
| [agents](agents) | Metadatos de presentación para el cliente |

### Índice de referencias

- [OWASP para MCP, LLM, agentes y skills](references/ai-security.md)
- [Autenticación antes del efecto protegido](references/auth-boundaries.md)
- [Estudio, ejercicios y cuestionarios](references/learning.md)
- [Fuentes y técnicas OWASP](references/owasp.md)
- [Tests de funcionamiento y de seguridad](references/security-tests.md)

## Ediciones conservadas

Elegí una edición completa, sin mezclar sus archivos. Se conservan los avisos originales y las diferencias.

| Edición | Documentación |
| --- | --- |
| multitienda | [English](variants/multitienda/README.md) · [Español](variants/multitienda/README.es.md) |
| agensi | [English](variants/agensi/README.md) · [Español](variants/agensi/README.es.md) |

## Alcance y límites

Es un paquete de instrucciones, no un escáner automático ni una certificación de seguridad. El seguimiento de commits dentro de una sesión no instala un observador permanente. La raíz incluye la referencia local auth-boundaries; las variantes anteriores conservan sus propios contenidos. Las suites externas de evaluación quedan fuera de este paquete.

El README está disponible en inglés y español, como la documentación de Huella. Los SKILL.md y las referencias conservan su idioma y redacción originales.

## Origen y condiciones

Preparado a partir de los archivos locales de skills de Leandro Ayala el 17/11/2026. Este README agrega documentación: no reemplaza las condiciones originales ni agrega una licencia.
