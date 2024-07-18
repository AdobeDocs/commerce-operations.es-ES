---
title: Crear, editar o desbloquear una cuenta de administrador
description: Siga estos pasos para administrar la cuenta de administrador de la aplicación de administración de Adobe Commerce.
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Crear, editar o desbloquear una cuenta de administrador

Para poder utilizar este comando, debe hacer lo siguiente:

- [Creación de la configuración de implementación](deployment.md)
- [Habilite como mínimo los módulos Magento_Authorization y Magento_User](manage-modules.md)
- Creación del esquema de base de datos

>[!NOTE]
>
>La forma más sencilla de crear la base de datos es usar el comando `magento setup:upgrade`.

## Creación o edición de un administrador

Utilice este comando para crear un administrador o para editar uno existente.

>[!NOTE]
>
>Si está editando un administrador, solamente se podrán editar `first name`, `last name` y `password`.

Uso de comandos:

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

Donde la siguiente tabla define parámetros y valores:

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--admin-firstname` | Nombre del usuario administrador. | Sí |
| `--admin-lastname` | Apellido del usuario administrador. | Sí |
| `--admin-email` | Dirección de correo electrónico del usuario administrador. | Sí |
| `--admin-user` | Nombre de usuario del administrador. | Sí |
| `--admin-password` | Contraseña de usuario del administrador. La contraseña debe tener al menos 7 caracteres de longitud e incluir al menos un carácter alfabético y al menos un carácter numérico. <br><br>Recomendamos una contraseña más larga y compleja. Si la cadena de contraseña contiene caracteres especiales que requieren interpretación literal (como barras invertidas o espacios), escriba la contraseña entre comillas simples. | Sí |
| `--magento-init-params` | Agregue a cualquier comando para personalizar los parámetros de inicialización de la aplicación<br/><br/>Por ejemplo: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | No |

Ejemplo de uso:

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```
Created Magento administrator user named j.doe
```

Si no especifica ninguno de los parámetros requeridos, la aplicación pregunta sobre ellos en la CLI:

```bash
bin/magento admin:user:create
```

```
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```
Created Magento administrator user named John
```

El siguiente ejemplo actualiza `first name`, `last name` y `password` de `j.doe` usuario administrador:

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```
Created Magento administrator user named j.doe
```

## Desbloquear una cuenta de administrador

Utilice este comando para desbloquear la cuenta de un administrador que estaba bloqueada, normalmente debido a varios intentos de inicio de sesión incorrectos.

```bash
bin/magento admin:user:unlock {username}
```

Debe especificar el nombre de usuario del administrador. Ejemplo:

```bash
bin/magento admin:user:unlock admin
```

```
The user account "admin" has been unlocked
```

Si la cuenta no está desbloqueada o si se ha producido un problema, se muestra el siguiente mensaje:

```
The user account "admin" was not locked or could not be unlocked
```

Compruebe que el usuario es un administrador, que está activo y que la cuenta está bloqueada. Para ver la lista de usuarios bloqueados en el Admin, inicie sesión como administrador y haga clic en **Sistema** > **Permisos** > **Usuarios bloqueados**.

Si la cuenta no existe, aparece el siguiente mensaje:

```
Couldn't find the user account "bob"
```
