# Proceso de Traducción de Archivos

Este documento describe el flujo de trabajo para la traducción de archivos de idioma en nuestro sistema.

## Descripción General

El proceso de traducción sigue un flujo secuencial que involucra a diferentes actores y sistemas:
- Desarrolladores (A y B)
- GitHub como sistema de control de versiones
- Sistema de Gestión de Traducciones (TMS)
- Traductora

## Fases del Proceso

### 1. Fase de Desarrollo Inicial
- El Desarrollador A crea un Pull Request (PR) con los archivos fuente en español (es.yml)
- GitHub notifica al Desarrollador B sobre el nuevo PR
- El Desarrollador B revisa y aprueba el PR
- GitHub integra los cambios a la rama master

### 2. Fase de Traducción
- El Sistema de Gestión de Traducciones (TMS) obtiene los nuevos archivos fuente de GitHub
- TMS sincroniza los archivos fuente
- TMS notifica a la Traductora sobre las traducciones pendientes
- La Traductora realiza las traducciones a inglés y portugués [EN-PT]
- La Traductora completa el flujo de traducciones en el TMS
- TMS crea un PR con las nuevas traducciones [EN-PT]

### 3. Fase de Desarrollo Final
- GitHub notifica al Desarrollador A sobre el PR con las nuevas traducciones
- El Desarrollador A revisa y aprueba el PR
- GitHub integra las traducciones a la rama master

## Diagrama de Secuencia

[El diagrama de secuencia](/docs/assets/seq-diagram.es.png)  muestra el flujo completo del proceso de traducción, incluyendo todas las interacciones entre los diferentes actores y sistemas involucrados.

```mermaid
---
config:
  theme: mc
---
sequenceDiagram
  participant DA as Developer A
  participant DB as Developer B
  participant GH as GitHub
  participant H as TMS
  participant T as Traductora
  rect rgb(230, 240, 255)
    Note right of DA: Fase de Desarrollo
    DA ->> GH: Crear PR es.yml (source files)
    GH ->> DB: Notificar nuevo PR
    DB ->> GH: Revisar y Aprobar PR
    GH ->> GH: Integrar PR a master
  end
  rect rgb(255, 245, 245)
    Note right of H: Fase de Traducción
    H ->> GH: Obtener nuevos soruce files
    GH ->> H: Sync source files
    H ->> T: Notificar traducciones pendientes
    T ->> T: Realizar traducciones a [EN-PT]
    T ->> H: Completar flujo de traducciones
    H ->> GH: Crear PR nuevas traducciones [EN-PT]
  end
  rect rgb(230, 240, 255)
    Note right of DA: Fase de Desarrollo
    GH ->> DA: Notificar PR nuevas traducciones [EN-PT]
    DA ->> GH: Revisar y Aprobar PR
    GH ->> GH: Integrar PR a master
  end
  Note over DA, T: Proceso de Traducciones

```

## Notas Importantes
- Los archivos fuente siempre están en español (es.yml) o español variante país (es-mx.yml, es-cl.yml, etc.)
- Las traducciones se realizan a inglés y portugués [EN-PT]
- Cada fase está claramente delimitada y requiere aprobación antes de pasar a la siguiente
- El proceso está automatizado a través de GitHub y el Sistema de Gestión de Traducciones