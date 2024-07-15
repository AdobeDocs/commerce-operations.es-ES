---
title: Seguridad de instalación local
description: Obtenga información acerca de las formas de mejorar la postura de seguridad de la instalación local de Adobe Commerce.
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Seguridad de instalación local

[Security Enhanced Linux (SELinux)](https://selinuxproject.org/page/Main_Page) permite a los administradores de CentOS y Ubuntu un mayor control de acceso sobre sus servidores. Si está usando SELinux *y* Apache debe iniciar una conexión con otro host, debe ejecutar los comandos mencionados en esta sección.

>[!NOTE]
>
>Adobe no recomienda el uso de SELinux; puede utilizarlo para mejorar la seguridad si lo desea. Si utiliza SELinux, debe configurarlo correctamente o el Adobe Commerce puede funcionar de forma impredecible. Si decide usar SELinux, consulte un recurso como la wiki de [CentOS](https://wiki.centos.org/HowTos/SELinux) para configurar reglas que permitan la comunicación.

## Sugerencia para instalar con Apache

Si decide habilitar SELinux, es posible que tenga problemas al ejecutar el instalador a menos que cambie el *contexto de seguridad* de algunos directorios de la siguiente manera:

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

Los comandos anteriores solo funcionan con el servidor web Apache. Debido a la variedad de configuraciones y requisitos de seguridad, no garantizamos que estos comandos funcionen en todas las situaciones. Para obtener más información, consulte:

* [página de comando man](https://linux.die.net/man/8/httpd_selinux)
* [Laboratorio de servidores](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Habilitar la comunicación entre servidores

Si Apache y el servidor de la base de datos están en el mismo host, utilice el siguiente comando si planea utilizar integraciones que utilicen `curl` (por ejemplo, PayPal y USPS).
Para permitir que Apache inicie una conexión con otro host con SELinux habilitado:

1. Para determinar si SELinux está habilitado, utilice el siguiente comando:

   ```bash
   getenforce
   ```

   `Enforcing` se muestra para confirmar que SELinux se está ejecutando.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## Apertura de puertos en el cortafuegos

Según sus requisitos de seguridad, es posible que necesite abrir el puerto 80 y otros puertos en el cortafuegos. Debido a la naturaleza delicada de la seguridad de la red, Adobe recomienda encarecidamente que consulte con su departamento de TI antes de continuar. A continuación se sugieren algunas referencias:

* Ubuntu: [página de documentación de Ubuntu](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [Procedimientos de CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).
