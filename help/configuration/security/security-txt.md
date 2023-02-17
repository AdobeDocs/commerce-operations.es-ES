---
title: Security.txt
description: Aprenda a proporcionar información para ayudar a los investigadores de seguridad a informar sobre vulnerabilidades.
badge: label="Contribuido por Kalpesh Mehta de Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
source-git-commit: bcb995ea417423b0cbc59c035ba5fdedbce3310e
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# Archivo TXT de seguridad

Cuando los investigadores descubren vulnerabilidades de seguridad, a menudo faltan canales adecuados de informes. Como resultado, no se notifican algunas vulnerabilidades. El propósito del `security.txt` [formato de archivo](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) es proporcionar a los investigadores de seguridad la información que pueden utilizar para informar de sus hallazgos.

Los comerciantes pueden introducir su información de contacto para [informes de problemas de seguridad](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) del comercio _Administrador_. Para los desarrolladores, la variable `Magento_Securitytxt` proporciona la siguiente funcionalidad:

- Permite guardar las configuraciones de seguridad de la variable _Administrador_.
- Contiene un router para que coincida con la clase de acción de la aplicación para las solicitudes de `.well-known/security.txt` y `.well-known/security.txt.sig` archivos.
- Sirve el contenido del `.well-known/security.txt` y `.well-known/security.txt.sig` archivos.

Un `security.txt` puede tener el siguiente aspecto:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Para crear la variable `security.txt` signature (`security.txt.sig`) archivo:

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Para verificar la firma:

```bash
gpg --verify security.txt.sig security.txt
```
