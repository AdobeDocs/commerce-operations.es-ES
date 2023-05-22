---
title: Hashing de contraseñas
description: Obtenga información sobre las estrategias y la implementación de hash de contraseña.
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Hashing de contraseñas

Actualmente, Commerce utiliza su propia estrategia para el hashing de contraseñas, basada en diferentes algoritmos nativos de hashing de PHP. Commerce admite varios algoritmos como `MD5`, `SHA256`, o `Argon 2ID13`. Si la extensión Sodium está instalada (instalada de forma predeterminada en PHP 7.3), entonces `Argon 2ID13` se elige como algoritmo hash predeterminado. De lo contrario, `SHA256` es el valor predeterminado. Commerce puede usar el PHP nativo `password_hash` función compatible con algoritmo Argon 2i.

Para evitar poner en peligro las contraseñas antiguas con algoritmos obsoletos, como `MD5`, la implementación actual proporciona un método para actualizar el hash sin cambiar la contraseña original. En general, el hash de contraseña tiene el siguiente formato:

```text
password_hash:salt:version<n>:version<n>
```

Donde `version<n>`...`version<n>` representa todas las versiones de algoritmos hash utilizadas en la contraseña. Además, la sal siempre se almacena junto con el hash de la contraseña, por lo que podemos restaurar toda la cadena de algoritmos. Un ejemplo tiene este aspecto:

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

La primera parte representa el hash de la contraseña. El segundo, `8qnyO4H1OYIfGCUb` es la sal. Los dos últimos son los diferentes algoritmos hash: 1 es `SHA256` y 2 es `Argon 2ID13`. Esto significa que la contraseña del cliente se cifró originalmente con `SHA256` y después, el algoritmo se actualizó con `Argon 2ID13` y el hachís fue refrito con Argón.

## Actualizar estrategia hash

Considere el aspecto del mecanismo de actualización del hash. Supongamos que originalmente se aplicó un cifrado hash a una contraseña con `MD5` y luego el algoritmo fue actualizado varias veces con Argon 2ID13. El diagrama siguiente muestra el flujo de actualización hash.

![Flujo de trabajo de actualización de hash](../../assets/configuration/hash-upgrade-algorithm.png)

Cada algoritmo hash utiliza el hash de contraseña anterior para generar un nuevo hash. Commerce no almacena la contraseña original sin procesar.

![Estrategia de actualización de hash](../../assets/configuration/hash-upgrade-strategy.png)

Como se ha mencionado anteriormente, el hash de contraseña puede tener varias versiones hash aplicadas a la contraseña original.
Así es como funciona el mecanismo de verificación de contraseña durante la autenticación de un cliente.

```php
def verify(password, hash):
    restored = password

    hash_map = extract(hash)
    # iterate through all versions specified in the received hash [md5, sha256, argon2id13]
    for version in hash_map.get_versions():
        # generate new hash based on password/previous hash, salt and version
        restored = hash_func(salt . restored, version)

    # extract only password hash from the hash:salt:version chain
    hash = hash_map.get_hash()

    return compare(restored, hash)
```

Dado que Commerce almacena todas las versiones de hash de contraseña utilizadas junto con el hash de contraseña, podemos restaurar toda la cadena de hash durante la verificación de la contraseña. El mecanismo de verificación de hash es similar a la estrategia de actualización de hash: en función de las versiones almacenadas junto con el hash de contraseña, el algoritmo genera hash a partir de la contraseña proporcionada y devuelve el resultado de comparación entre la contraseña con hash y el hash almacenado en la base de datos.

## Implementación

El `\Magento\Framework\Encryption\Encryptor` La clase es responsable de la generación y verificación del hash de la contraseña. El [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) El comando actualiza un hash de contraseña de cliente al algoritmo hash más reciente.
