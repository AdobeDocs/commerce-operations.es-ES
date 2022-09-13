---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# Comprobar que la comunicación es segura

En esta sección se tratan dos formas de verificar que la autenticación básica de HTTP funciona:

* Uso de un `curl` para verificar que debe introducir un nombre de usuario y una contraseña para obtener el estado del clúster
* Configuración de la autenticación HTTP Basic en el Administrador

## Utilice un `curl` comando para verificar el estado del clúster

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

Ahora pruebe el siguiente comando:

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

## Configurar la autenticación HTTP Basic en el Administrador

Realice las mismas tareas que se describen en [Configuración del motor de búsqueda](../configuration/search/configure-search-engine.md) *except* click **[!UICONTROL Yes]** de la variable **[!UICONTROL Enable Elasticsearch HTTP Auth]** e introduzca su nombre de usuario y contraseña en los campos proporcionados.

Haga clic en **[!UICONTROL Test Connection]** para asegurarse de que funciona y, a continuación, haga clic en **[!UICONTROL Save Config]**.

Debe vaciar la caché del Magento y reindexar antes de continuar.
