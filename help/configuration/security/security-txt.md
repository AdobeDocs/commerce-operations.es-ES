---
title: Security.txt
description: Aprenda a proporcionar información para ayudar a los investigadores de seguridad a notificar vulnerabilidades.
badge: label="Contribución de Kalpesh Mehta de Corra" type="Informativo" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Archivo TXT de seguridad

Cuando los investigadores descubren vulnerabilidades de seguridad, a menudo no hay canales de informes adecuados. Como resultado, no se informa de algunas vulnerabilidades. El propósito de la `security.txt` [formato de archivo](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) El objetivo de este archivo es proporcionar a los investigadores de seguridad la información que pueden utilizar para informar sobre sus conclusiones.

Los comerciantes pueden introducir su información de contacto para [informe de problemas de seguridad](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) de Commerce _Administrador_. Para los desarrolladores, la variable `Magento_Securitytxt` Este módulo proporciona las siguientes funciones:

- Permite guardar las configuraciones de seguridad desde el _Administrador_.
- Contiene un enrutador para que coincida con la clase de acción de la aplicación para las solicitudes al `.well-known/security.txt` y `.well-known/security.txt.sig` archivos.
- Sirve el contenido del `.well-known/security.txt` y `.well-known/security.txt.sig` archivos.

Un válido `security.txt` el archivo puede tener el aspecto siguiente:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Para crear el `security.txt` firma (`security.txt.sig`) archivo:

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Para comprobar la firma:

```bash
gpg --verify security.txt.sig security.txt
```
