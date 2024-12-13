# Estructura de Directorios para Archivos de Idiomas

Los [archivos fuente](/docs/files/README.es.md#source-files) y [archivos de traducción](/docs/files/README.es.md#target-files) se encuentran dentro de `packs/`, pueden estar en cualquier nivel dentro de `config/locales/`:

```
packs/*/config/locales/
├── es.yml                                # Nivel 1
├── foo/
│   └── es.yml                           # Nivel 2
├── foo/
│   └── bar/
│       └── es.yml                       # Nivel 3
├── foo/
│   └── bar/
│       └── baz/
│           └── es.yml                   # Nivel 4
└── foo/
    └── bar/
        └── baz/
            └── qux/
                └── es.yml               # Nivel 5
```

## Importante
- Las fuentes y traducciones pueden estar en cualquier nivel de profundidad dentro de los packs
- Para más detalles sobre el patrón de los archivos consulta [Guía de Estructura de Archivos de Traducción](/docs/files/README.es.md)
