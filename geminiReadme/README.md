# Gemini Auto Update README

Esta acción de GitHub permite actualizar automáticamente el archivo `README.md` de tu repositorio utilizando el modelo Gemini de Google. Analiza los cambios recientes en tu código y la estructura de tu proyecto para mantener la documentación actualizada.

## Funcionalidad

1.  Genera contexto basado en los cambios del último commit y la estructura del proyecto.
2.  Descarga un prompt personalizado desde una URL proporcionada.
3.  Utiliza Gemini AI para generar un nuevo `README.md` basado en el contexto y el prompt.
4.  Crea una nueva rama, commitea los cambios y abre automáticamente un Pull Request.

## Entradas (Inputs)

| Nombre | Descripción | Requerido | Default |
| :--- | :--- | :--- | :--- |
| `gemini_api_key` | API Key de Google Gemini | Sí | - |
| `gemini_model` | Modelo de Gemini a utilizar (ej. `gemini-1.5-flash`) | Sí | - |
| `prompt_url` | URL raw hacia un archivo `.md` que contiene el prompt de sistema | Sí | - |
| `repo_slug` | Repositorio objetivo (owner/repo) | No | `${{ github.repository }}` |
| `target_branch` | Rama base para el Pull Request | No | `master` |

## Ejemplo de uso

```yaml
- name: Auto Update README
  uses: Alexmm14/toolsActions/gemini-readme@master
  with:
    gemini_api_key: ${{ secrets.GEMINI_API_KEY }}
    gemini_model: 'gemini-1.5-flash'
    prompt_url: 'https://raw.githubusercontent.com/usuario/repo/main/prompts/readme-updater.md'
```

---
*Esta herramienta requiere que la GitHub CLI (`gh`) esté instalada en el runner o sea accesible en el entorno.*

## Dependencias (Recomendación)

Para garantizar un entorno compatible, se recomienda ejecutar esta acción dentro de un contenedor Docker que incluya las herramientas necesarias:

```yaml
jobs:
  update-readme:
    runs-on: ubuntu-latest
    container:
      image: ghcr.io/alejandromolinamedina/gemini-cli-docker:latest
      credentials:
        username: ${{ github.actor }}
        password: ${{ secrets.GITHUB_TOKEN }}
    # ...
```
