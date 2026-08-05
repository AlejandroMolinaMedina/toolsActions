# Tools Actions

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-Composite-blue)](https://docs.github.com/en/actions/creating-actions/creating-a-composite-action)

Este repositorio centraliza **GitHub Composite Actions** diseñadas para estandarizar, automatizar y optimizar los flujos de trabajo (CI/CD) en múltiples proyectos. Estas acciones reutilizables eliminan la redundancia y garantizan la consistencia en el despliegue y la gestión de repositorios.

## Características Principales

*   **Estandarización**: Unifica procesos comunes como la extracción de metadatos de Git y la notificación vía webhooks.
*   **Modularidad**: Acciones independientes y desacopladas que se pueden integrar selectivamente según las necesidades del workflow.
*   **Facilidad de Uso**: Configuración rápida mediante pasos simples en archivos de flujo de trabajo YAML.
*   **Extensibilidad**: Diseñado para escalar y añadir nuevas utilidades DevOps conforme evolucione el ecosistema del proyecto.

## Estructura del Proyecto

```text
.
├── getData/              # Acción para extraer contexto de Git
├── webhook/notify/       # Acción genérica para envío de webhooks JSON
├── geminiReadme/         # Acción para automatización de documentación
└── README.md             # Documentación principal del repositorio
```

## Guía de Inicio Rápido

Para utilizar cualquiera de estas acciones, es obligatorio realizar un `checkout` con profundidad completa para asegurar que el contexto del repositorio esté disponible.

### Ejemplo de implementación (`getData`):

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Extraer Datos
        uses: Alexmm14/toolsActions/getData@master
```

### Ejemplo de implementación (`webhook/notify`):

```yaml
      - name: Notificar vía Webhook
        uses: Alexmm14/toolsActions/webhook/notify@master
        with:
          url: ${{ secrets.WEBHOOK_URL }}
          payload: '{"status": "success", "message": "Pipeline ejecutado correctamente"}'
```

## Soporte y Documentación

Cada directorio de acción incluye su propio archivo `README.md` con detalles específicos sobre los parámetros de entrada (`inputs`), salidas (`outputs`) y configuraciones avanzadas. Si encuentras un error o deseas proponer una nueva acción, abre un **Issue** en este repositorio.

## Mantenimiento y Contribución

Este proyecto es mantenido por **Alexmm14**. Las contribuciones son bienvenidas mediante *Pull Requests*. Para cambios significativos, por favor abre primero un Issue para discutir los cambios propuestos. 

---
MIT License © 2026 Alexmm14