---
title: Crear, editar o desbloquear una cuenta de administrador
description: Siga estos pasos para administrar la cuenta de administrador de la aplicación de administración de Adobe Commerce o Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Crear, editar o desbloquear una cuenta de administrador

Antes de utilizar este comando, debe hacer lo siguiente:

- [Creación de la configuración de implementación](deployment.md)
- [Habilitar como mínimo los módulos Magento_Authorization y Magento_User](manage-modules.md)
- Crear el esquema de la base de datos

>[!NOTE]
>
>La forma más sencilla de crear la base de datos es utilizar el comando `magento setup:upgrade`.

## Crear o editar un administrador

Utilice este comando para crear un administrador o editar un administrador existente.

>[!NOTE]
>
>Si está editando un administrador, solo el `first name`, `last name`y `password` se puede editar.

Uso de comandos:

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

Donde la tabla siguiente define parámetros y valores:

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--admin-firstname` | Nombre del usuario administrador. | Sí |
| `--admin-lastname` | Apellido del usuario administrador. | Sí |
| `--admin-email` | Dirección de correo electrónico del usuario administrador. | Sí |
| `--admin-user` | Nombre de usuario del administrador. | Sí |
| `--admin-password` | Contraseña de usuario administrador. La contraseña debe tener al menos 7 caracteres de longitud y debe incluir al menos un carácter alfabético y al menos un carácter numérico. <br><br>Recomendamos una contraseña más larga y compleja. Si la cadena de contraseña contiene caracteres especiales que requieren interpretación literal (como barras invertidas o espacios), escriba la contraseña entre comillas simples. | Sí |
| `--magento-init-params` | Agregar a cualquier comando para personalizar los parámetros de inicialización de la aplicación<br/><br/>Por ejemplo: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | No |

Ejemplo de uso:

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```terminal
Created Magento administrator user named j.doe
```

Si no especifica ninguno de los parámetros requeridos, la aplicación pregunta acerca de ellos en la CLI:

```bash
bin/magento admin:user:create
```

```terminal
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```terminal
Created Magento administrator user named John
```

El siguiente ejemplo actualiza `first name`, `last name`y `password` de `j.doe` usuario administrador:

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```terminal
Created Magento administrator user named j.doe
```

## Desbloquear una cuenta de administrador

Utilice este comando para desbloquear la cuenta de un administrador que estaba bloqueado, por lo general debido a varios intentos de inicio de sesión incorrectos.

```bash
bin/magento admin:user:unlock {username}
```

Debe especificar el nombre de usuario del administrador. Ejemplo:

```bash
bin/magento admin:user:unlock admin
```

```terminal
The user account "admin" has been unlocked
```

Si la cuenta no está bloqueada o si hay algún problema, se muestra el siguiente mensaje:

```terminal
The user account "admin" was not locked or could not be unlocked
```

Compruebe que el usuario es administrador, que el usuario está activo y que la cuenta está bloqueada. Para ver la lista de usuarios bloqueados en el Administrador, inicie sesión como administrador y haga clic en **Sistema** > **Permisos** > **Usuarios bloqueados**.

Si la cuenta no existe, se muestra el siguiente mensaje:

```terminal
Couldn't find the user account "bob"
```
