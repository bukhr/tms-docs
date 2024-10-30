# Fase de Incorporación de Traducciones

Este documento describe el proceso de gestión de traducciones desde el sistema TMS hasta su integración en la rama principal del repositorio.

## Descripción General

El flujo de trabajo involucra múltiples actores y sistemas:
- Traductora
- Sistema TMS (Translation Management System)
- GitHub
- Desarrolladores
- Ambiente Local

## Fases del Proceso

### 1. Fase de Traducción

1. La traductora completa el flujo de traducciones en el sistema TMS.

### 2. Fase de Desarrollo Final - Revisión Pull Request

1. El sistema TMS crea automáticamente un Pull Request (PR) en GitHub con las traducciones [EN-PT].
2. GitHub notifica al desarrollador asignado sobre el nuevo PR.
3. El desarrollador descarga el PR en su ambiente local.

### 3. Proceso de Revisión Local

El desarrollador debe ejecutar un script supervisado (`script.rb`) que realiza las siguientes acciones:

#### Acciones Automatizadas:
- Rebase y squash de los commits del PR
- Ejecución del linter en archivos .yml

#### Acciones Manuales:
- Resolución de conflictos del rebase
- Reescritura de archivos `pt-br.yml` a `pt.yml`
- Verificación visual final

#### Conflictos Comunes:
1. Keys duplicadas
2. Problemas de indentación en archivos YML

#### Validaciones del Linter:
1. Sintaxis YML válida
2. Ausencia de espacios extras
3. Encoding UTF-8 correcto

### 4. Criterios de Aceptación

Para aprobar el PR, se deben cumplir los siguientes criterios:
1. El linter pasa sin errores
2. No existen conflictos
3. Las traducciones están completas

### 5. Flujos de Resolución

#### PR Aprobado:
1. El desarrollador aprueba y confirma el PR en GitHub
2. Las traducciones se integran en la rama master
3. Los archivos `EN.yml` y `PT.yml` quedan integrados en la rama principal

#### PR Requiere Cambios:
1. El desarrollador rechaza el PR en GitHub
2. Se notifica a la traductora sobre los cambios requeridos
3. El proceso vuelve a la Fase de Traducción

#### Razones Comunes de Rechazo:
1. Traducciones incompletas
2. Errores de formato
3. PR sin cambios

## Diagrama de Secuencia

El diagrama de secuencia muestra el flujo en su última fase dónde se realiza la revisión de un nuevo Pull Request de Traducciones.

```mermaid
---
config:
theme: mc
---
sequenceDiagram
    participant TD as Traductora
    participant TMS as Sistema TMS
    participant GH as GitHub
    participant M as Master Branch
    participant DA as Desarrollador A
    participant L as Localhost
    Note over TD,TMS: ... Fase de Traducción
    TD->>+TMS: Completa flujo de traducciones
    Note over TMS,L: Fase Final - Incorporación de Traducciones a Buk
    TMS->>-GH: Crea PR con traducciones [EN-PT]
    GH->>DA: Notifica nuevo PR con traducciones
    Note over DA: Recibe notificación<br/>del nuevo PR<br/>
    DA->>L: Descarga nuevo PR
    rect rgb(255, 245, 245)
        Note over L: Ejecución supervisada del script.rb
        L->>L: Rebase and squash de los commits del PR [Auto]
        Note over L: Conflictos comunes:<br/>1. Keys duplicadas<br/>2. Indentación YML
        L->>L: Resolver conflictos del rebase [Manual]
        L->>L: Linter a los archivos .yml [Auto]
        Note over L: Validaciones:<br/>1. Sintaxis YML válida<br/>2. No hay espacios extras<br/>3. Encoding UTF-8
        L->>L: Reescribir archivos pt-br.yml > pt.yml [Manual]
        L->>L: Chequear que todo se ve bien [Manual]
    end
    alt PR Aprobado
        Note over L: Criterios de aceptación:<br/>1. Linter pasa sin errores<br/>2. No hay conflictos<br/>3. Traducciones completas
        L->>GH: Aprueba y confirma PR
        GH->>M: Integra traducciones
        Note over M: Archivos EN.yml y PT.yml<br/>integrados en master
    else PR Requiere Cambios
        Note over L: Razones comunes de rechazo:<br/>1. Traducciones incompletas<br/>2. Errores de formato<br/>3. PR sin cambios
        L->>GH: Rechaza PR
        GH->>TD: Notifica cambios requeridos
        Note over TMS: Vuelve a<br/>Fase de Traducción<br/>
    end
```

## Notas Importantes

- Es crucial mantener la consistencia en el formato de los archivos YML (source files y target files)
- La verificación manual es necesaria para garantizar la calidad de las traducciones
- El proceso está diseñado para mantener la integridad de las traducciones en todo momento
