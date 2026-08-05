# Tools Actions

Este repositorio centraliza **GitHub Composite Actions** utilizadas para estandarizar flujos de trabajo en múltiples proyectos.

## Estructura del Repositorio

* `getData`: Extrae información del contexto de Git y del repositorio.
* `webhook/notify`: Una acción genérica para enviar webhooks JSON dinámicos.

## Uso General

Para utilizar cualquiera de estas acciones, es necesario incluir el paso de checkout con `fetch-depth: 0`:

```yaml
steps:
  - name: Checkout
    uses: actions/checkout@v4
    with:
      fetch-depth: 0

  - name: Extraer Datos
    uses: Alexmm14/toolsActions/getData@master
```

---
MIT License © 2026 Alexmm14
