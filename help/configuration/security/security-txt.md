---
title: Security.txt
description: Aprenda a proporcionar información para ayudar a los investigadores de seguridad a notificar vulnerabilidades.
feature: Configuration, Security
badge: label="Colaboró Kalpesh Mehta de Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# Archivo TXT de seguridad

Cuando los investigadores descubren vulnerabilidades de seguridad, a menudo no hay canales de informes adecuados. Como resultado, no se informa de algunas vulnerabilidades. El propósito del archivo `security.txt` [formato de archivo](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) es proporcionar a los investigadores de seguridad la información que pueden utilizar para informar sobre sus hallazgos.

Los comerciantes pueden escribir su información de contacto para [informar sobre problemas de seguridad](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-issue-reporting) desde el _administrador_ de Commerce. Para los desarrolladores, el módulo `Magento_Securitytxt` proporciona la siguiente funcionalidad:

- Permite guardar las configuraciones de seguridad desde _Admin_.
- Contiene un enrutador para que coincida con la clase de acción de la aplicación para las solicitudes de los archivos `.well-known/security.txt` y `.well-known/security.txt.sig`.
- Sirve el contenido de los archivos `.well-known/security.txt` y `.well-known/security.txt.sig`.

Un archivo `security.txt` válido puede tener el siguiente aspecto:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Para crear el archivo de firma `security.txt` (`security.txt.sig`):

```shell
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Para comprobar la firma:

```shell
gpg --verify security.txt.sig security.txt
```
