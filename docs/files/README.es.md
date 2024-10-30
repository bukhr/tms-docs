# Guía de Estructura de Archivos de Traducción
Esta guía describe la organización interna y nomenclatura de los archivos de traducción utilizados en el proyecto. No debe confundirse con la estructura de directorios del proyecto en sí.

## Source Files
Son los archivos fuente gestionados por los desarrolladores (creación, edición, movimiento o eliminación de estos).

### Archivo Base

El archivo principal por defecto es `es.yml` (Español estándar). 

Ejemplo:
```yml
---
es:
  activerecord:
    models:
      postulante:
        one: Postulante
        other: Postulantes
    attributes:
      postulante:
        first_name: Nombre
        last_name: Primer Apellido
        segundo_apellido: Segundo Apellido
        date_of_birth: Fecha de Nacimiento
        email: Email
        telefono: Teléfono
        picture_url: Foto
        direccion: Dirección
```

### Archivos Fuente por País
Cuando los requisitos del negocio varían por país, utilizamos los siguientes archivos fuente con traducciones adaptadas al contexto local:

```
es-br.yml  (Español - Brasil)
es-cl.yml  (Español - Chile)
es-co.yml  (Español - Colombia)
es-mx.yml  (Español - México)
es-pe.yml  (Español - Perú)
```

Por ejemplo, `es-mx.yml` (Español - México):
```yml
---
es-mx:
  activerecord:
    models:
      postulante: Postulante
    attributes:
      postulante:
        last_name: Apellido Paterno        # Diferente al estándar
        segundo_apellido: Apellido Materno # Diferente al estándar
        region: Estado                     # Diferente al estándar
        comuna: Municipio                  # Diferente al estándar
        location: Estado-Municipio         # Diferente al estándar
        recomendador_rut: Recomendador RFC # Específico de México
```

Y `es-pe.yml` (Español - Perú):
```yml
---
es-pe:
  activerecord:
    models:
      postulante: Postulante
    attributes:
      postulante:
        region: Departamento              # Diferente al estándar
        comuna: Distrito                  # Diferente al estándar
        location: Distrito                # Diferente al estándar
        recomendador_rut: Recomendador DNI # Específico de Perú
```

## Target Files
Contiene los archivos generados por el Sistema de Gestión de Traducciones (TMS) para cada idioma objetivo.

### Traducciones al Inglés
El inglés mantiene la misma estructura que los archivos fuente, adaptando las traducciones tanto para la versión estándar como para las variantes por país:


```
en.yml      (Inglés estándar)
en-br.yml   (Inglés - Brasil)
en-cl.yml   (Inglés - Chile)
en-co.yml   (Inglés - Colombia)
en-mx.yml   (Inglés - México)
en-pe.yml   (Inglés - Perú)
```

Ejemplo inglés estándar (`en.yml`):
```yml
---
en:
  activerecord:
    models:
      postulante:
        one: Applicant
        other: Applicants
    attributes:
      postulante:
        first_name: Name
        last_name: First Surname
        segundo_apellido: Second Surname
        date_of_birth: Date of Birth
        email: Email
        region: Region
        comuna: Commune
        location: Commune
```

Para la variante de Perú (`en-pe.yml`):
```yml
---
en-pe:
  activerecord:
    models:
      postulante: Applicant
    attributes:
      postulante:
        first_name: Name
        last_name: First Surname
        segundo_apellido: Second Surname
        date_of_birth: Date of Birth
        email: Email
        region: Department
        comuna: District
        location: District
```

### Traducciones al Portugués
El portugués sigue el mismo patrón de traducción, adaptando términos y estructura según el uso local del idioma:


```
pt.yml      (Portugués estándar)
pt-br.yml   (Portugués - Brasil)
pt-cl.yml   (Portugués - Chile)
pt-co.yml   (Portugués - Colombia)
pt-mx.yml   (Portugués - México)
pt-pe.yml   (Portugués - Perú)
```

Ejemplo portugués estándar (`pt.yml`):
```yml
---
pt:
  activerecord:
    models:
      postulante:
        one: Candidato
        other: Candidatos
    attributes:
      postulante:
        first_name: Nome
        last_name: Primeiro Sobrenome
        segundo_apellido: Segundo Sobrenome
        date_of_birth: Data de Nascimento
        email: E-mail
        region: Região
        comuna: Comuna
        location: Comuna
```

Ejemplo variante de México (`pt-mx.yml`):
```yml
---
pt-mx:
  activerecord:
    models:
      postulante: Candidato
    attributes:
      postulante:
        first_name: Nome
        last_name: Sobrenome Paterno
        segundo_apellido: Sobrenome Materno
        date_of_birth: Data de Nascimento
        email: E-mail
        region: Estado
        comuna: Município
        location: Estado-Município
```

**Nota:** Cada archivo destino corresponde a una versión traducida de su archivo fuente, manteniendo las mismas variantes específicas por país pero en diferentes idiomas.
