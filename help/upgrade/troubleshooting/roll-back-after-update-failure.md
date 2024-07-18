---
title: Revertir tras un error de actualización del módulo
description: Solucione los problemas de la actualización de Adobe Commerce después de encontrar un error de actualización de módulo.
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Revertir tras un error de actualización del módulo

Si la actualización del módulo falla, se muestran mensajes similares a los siguientes en el registro de la consola:

```
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

En el ejemplo anterior, no hay ninguna versión de componente a la que se pueda revertir. Póngase en contacto con el proveedor del componente o intente resolver el problema usted mismo.

Mientras tanto, puede revertir a una versión anterior haciendo clic en **Reversión**, que recupera los datos aunque no haya realizado una copia de seguridad anteriormente.
