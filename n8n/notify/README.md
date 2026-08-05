# Acción Webhook Sender (Genérica)

Envía cualquier objeto JSON a cualquier endpoint de Webhook compatible. Aunque el nombre de la carpeta sugiere n8n, la acción es totalmente agnóstica respecto al destino.

## Inputs

| Nombre | Descripción | Requerido |
| :--- | :--- | :--- |
| `endpoint` | URL de destino del Webhook. | Sí |
| `json_body` | Cuerpo completo del mensaje JSON. | Sí |

## Ejemplo de uso

```yaml
- name: Enviar Webhook
  uses: Alexmm14/toolsActions/notify-n8n@master
  with:
    endpoint: ${{ secrets.WEBHOOK_URL }}
    json_body: |
      {
        "evento": "despliegue_completado",
        "proyecto": "mi-proyecto",
        "status": "OK"
      }
```
