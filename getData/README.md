# Acción Get Data

Esta acción procesa información del commit actual y del repositorio para generar salidas (outputs) para tus flujos de trabajo.

## Inputs

| Nombre | Descripción | Requerido |
| :--- | :--- | :--- |
| `docker_digest` | Hash de la imagen generada. | No |

## Ejemplo de uso

```yaml
- name: Extraer Variables
  id: vars
  uses: Alexmm14/toolsActions/getData@master
  with:
    docker_digest: ${{ steps.docker_build.outputs.digest }}
```
