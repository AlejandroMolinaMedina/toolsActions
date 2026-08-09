# 🤖 geminiReadme Action

Una GitHub Action inteligente que mantiene tu `README.md` actualizado automáticamente utilizando el modelo Gemini de Google. Analiza tu código y estructura para generar documentación relevante, ahorrándote tiempo y manteniendo la consistencia de tu proyecto.

## 🚀 ¿Por qué usarla?

- **Actualización Automática:** Mantiene tu documentación al día con los cambios en tu código.
- **Basada en IA:** Utiliza el modelo Gemini para redactar contenido preciso y coherente.
- **Configurable:** Define tu propio prompt de sistema para personalizar el estilo de redacción.
- **Flujo integrado:** Crea ramas y Pull Requests automáticamente.

## ⚙️ Entradas (Inputs)

| Nombre | Descripción | Requerido | Default |
| :--- | :--- | :--- | :--- |
| `gemini_api_key` | Tu API Key de Google Gemini. | Sí | - |
| `gemini_model` | Modelo de Gemini a usar (ej: `gemini-1.5-flash`). | Sí | - |
| `prompt_url` | URL (raw) hacia el archivo `.md` del prompt de sistema. | Sí | - |
| `repo_slug` | Repositorio a analizar (owner/repo). | No | `${{ github.repository }}` |
| `target_branch` | Rama base para crear el Pull Request. | No | `main` |

## 📝 Requerimientos del Prompt

Para que la acción funcione correctamente, el prompt configurado en `prompt_url` **debe** devolver una respuesta estructurada en dos partes:

1.  **Primera línea (Decisión):** Debe contener exclusivamente la palabra `true` (si amerita actualización) o `false` (si no). Sin formato markdown, puntuación ni texto adicional.
2.  **Segunda línea en adelante:** El contenido (el nuevo README si es `true`, o el motivo si es `false`).

Puedes utilizar este prompt como referencia robusta que sigue exactamente esta lógica:
[Prompt de ejemplo para README](https://github.com/AlejandroMolinaMedina/prompts/blob/master/prompts/readme-prompt.md)

## 🛠️ Ejemplo de Uso

Añade este paso a tu archivo de workflow (`.github/workflows/update-readme.yml`):

```yaml
jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Gemini Update README
        uses: Alexmm14/toolsActions/geminiReadme@master
        with:
          gemini_api_key: ${{ secrets.GEMINI_API_KEY }}
          gemini_model: 'gemini-1.5-flash'
          prompt_url: 'https://raw.githubusercontent.com/tu-usuario/tu-repo/main/prompts/prompt.md'
```

> **Nota:** Esta acción requiere que `gh` (GitHub CLI) esté disponible en el entorno de ejecución del runner.

## 🛠️ Dependencias (Recomendación)

Se recomienda ejecutar esta acción dentro de un entorno que contenga las herramientas necesarias (como una imagen Docker preconfigurada):

```yaml
    container:
      image: ghcr.io/alejandromolinamedina/gemini-cli-docker:latest
      # ...
```
