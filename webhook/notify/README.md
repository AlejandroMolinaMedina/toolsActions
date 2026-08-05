# Acción Webhook Sender (Genérica)

Envía cualquier objeto JSON a cualquier endpoint de Webhook compatible.

## Inputs

| Nombre | Descripción | Requerido |
| :--- | :--- | :--- |
| `endpoint` | URL de destino del Webhook. | Sí |
| `json_body` | Cuerpo completo del mensaje JSON. | Sí |

## Ejemplo de uso

```yaml
- name: Enviar Webhook
  uses: Alexmm14/toolsActions/webhook/notify@master
  with:
    endpoint: ${{ secrets.WEBHOOK_URL }}
    json_body: |
      {
        "evento": "despliegue_completado",
        "proyecto": "mi-proyecto",
        "status": "OK"
      }
```
