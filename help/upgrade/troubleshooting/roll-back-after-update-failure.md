---
title: Reversión después del error de actualización del módulo
description: Solucione los problemas de la actualización de Adobe Commerce o Magento Open Source después de encontrar un error de actualización de módulo.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# Reversión después del error de actualización del módulo

Si falla la actualización del módulo, en el registro de la consola aparecen mensajes similares a los siguientes:

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

En el ejemplo anterior, no hay ninguna versión de componente a la que revertir. Póngase en contacto con el proveedor de componentes o intente resolver el problema usted mismo.

Mientras tanto, puede volver a una versión anterior haciendo clic en **Reversión**, que recupera los datos aunque no haya realizado una copia de seguridad anteriormente.
