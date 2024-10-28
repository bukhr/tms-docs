# Guía de Estructura de Archivos de Traducción

## Directorio de Archivos Fuente (Source Files)
Este directorio contiene los archivos originales gestionados por los desarrolladores (creación, edición, movimiento o eliminación).

### Archivo Fuente Base
- Archivo principal por defecto: `es.yml` (Español estándar)

### Variantes por País
Cuando los requisitos del negocio varían por país, creamos variantes específicas:
```
es-br.yml  (Español - Brasil)
es-cl.yml  (Español - Chile)
es-co.yml  (Español - Colombia)
es-mx.yml  (Español - México)
es-pe.yml  (Español - Perú)
```

## Directorio de Archivos Destino (Target Files)
Contiene los archivos generados por el Sistema de Gestión de Traducciones (TMS) para cada idioma objetivo.

### Traducciones al Inglés
```
en.yml      (Inglés estándar)
en-br.yml   (Inglés - Brasil)
en-cl.yml   (Inglés - Chile)
en-co.yml   (Inglés - Colombia)
en-mx.yml   (Inglés - México)
en-pe.yml   (Inglés - Perú)
```

### Traducciones al Portugués
```
pt.yml      (Portugués estándar)
pt-br.yml   (Portugués - Brasil)
pt-cl.yml   (Portugués - Chile)
pt-co.yml   (Portugués - Colombia)
pt-mx.yml   (Portugués - México)
pt-pe.yml   (Portugués - Perú)
```

**Nota:** Cada archivo destino corresponde a una versión traducida de su archivo fuente, manteniendo las mismas variantes específicas por país pero en diferentes idiomas.