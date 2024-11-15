# Translation Files Structure
The [source files](https://github.com/bukhr/tms-docs/blob/main/docs/files/README.en.md#source-files) and [target files](https://github.com/bukhr/tms-docs/blob/main/docs/files/README.en.md#target-files) are located inside `packs/`, they can be at any level within `config/locales/`:

```
packs/*/config/locales/
├── en.yml                                # Level 1
├── foo/
│   └── en.yml                           # Level 2
├── foo/
│   └── bar/
│       └── en.yml                       # Level 3
├── foo/
│   └── bar/
│       └── baz/
│           └── en.yml                   # Level 4
└── foo/
    └── bar/
        └── baz/
            └── qux/
                └── en.yml               # Level 5
```

## Important
- Source and translation files can be at any depth level within the packs
- For more details about the file pattern, check the [Translation Files Structure Guide](https://github.com/bukhr/tms-docs/blob/main/docs/files/README.es.md)
