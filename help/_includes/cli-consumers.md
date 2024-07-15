---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---
# Opciones de CLI para consumidores de colas de mensajes

| Nombre | Descripción | Valor | Requerido |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Determina si los consumidores esperarán un mensaje de la cola. | 1 - Sí, 0 - No | No |

* `0`: los consumidores procesan los mensajes disponibles en la cola, cierran la conexión TCP y finalizan. Los consumidores no esperan mensajes adicionales para entrar en la cola, aunque el número de mensajes procesados sea menor que el valor `--max_messages` especificado durante el inicio de los consumidores.

* `1`: los consumidores continúan procesando mensajes de la cola de mensajes hasta alcanzar el número máximo de mensajes (el valor especificado para `--max_messages` en el comando `queue:consumers:start`) antes de cerrar la conexión TCP y finalizar el proceso de consumo. Si la cola se vacía antes de llegar a `--max_messages`, el consumidor espera a que lleguen más mensajes. Si usa trabajadores para ejecutar consumidores en lugar de usar un trabajo cron, establezca esta variable en `1`.

>[!WARNING]
>
>La opción `--consumers-wait-for-messages` es una opción global y no se puede configurar por separado para cada consumidor.
