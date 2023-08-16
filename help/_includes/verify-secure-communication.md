---
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 1%

---
# Verifique que la comunicación sea segura

En esta sección se describen dos formas de comprobar que la autenticación HTTP Basic funciona:

* Uso de un `curl` para comprobar que debe escribir un nombre de usuario y una contraseña para obtener el estado del clúster
* Configuración de la autenticación HTTP Basic en el administrador

## Utilice un `curl` comando para comprobar el estado del clúster

Introduzca el siguiente comando:

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Por ejemplo, si introduce el comando en el servidor del motor de búsqueda y el proxy utiliza el puerto 8080:

```bash
curl -i http://localhost:8080/_cluster/health
```

Se muestra el siguiente mensaje para indicar que la autenticación ha fallado:

```terminal
HTTP/1.1 401 Unauthorized
Date: Tue, 23 Feb 2016 20:35:29 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
WWW-Authenticate: Basic realm="Restricted"
<html>
<head><title>401 Authorization Required</title></head>
<body bgcolor="white">
  <center><h1>401 Authorization Required</h1></center>
</body>
</html>
```

Ahora intente el siguiente comando:

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Por ejemplo:

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

Esta vez, el comando se ejecuta correctamente con un mensaje similar al siguiente:

```terminal
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## Configure la autenticación HTTP Basic en el administrador

Realice las mismas tareas que se describen en [Configuración del motor de búsqueda](../configuration/search/configure-search-engine.md) *excepto* click **[!UICONTROL Yes]** desde el **[!UICONTROL Enable HTTP Auth]** e introduzca su nombre de usuario y contraseña en los campos proporcionados.

Clic **[!UICONTROL Test Connection]** para asegurarse de que funciona y haga clic en **[!UICONTROL Save Config]**.

Debe vaciar la caché y reindexar antes de continuar.
