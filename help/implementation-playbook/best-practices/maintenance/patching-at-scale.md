---
title: Prácticas recomendadas para distribuir parches a escala
description: Descubra cómo la aplicación centralizada de parches para Adobe Commerce puede ayudarle a administrar proyectos empresariales.
role: Developer
feature: Best Practices
badge: label="Colaboró Tony Evers, arquitecto técnico senior, Adobe" type="Informative" url="https://www.linkedin.com/in/evers-tony/" tooltip="Colaboró Tony Evers"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: 2c9f827326315bc4ef77d511dddce81e059a1092
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Prácticas recomendadas para distribuir parches de Adobe Commerce a escala

Si administra varias instalaciones de Adobe Commerce, [aplicar parches](../../../upgrade/patches/apply.md) puede ser un proceso complejo. _Aplicar parches de forma centralizada_ es una práctica recomendada para las empresas. Le ayuda a aplicar los parches adecuados en todas las instalaciones de Adobe Commerce. En este tema se explica cómo lograr la distribución centralizada de parches para todos los tipos de [parches](../../../upgrade/patches/overview.md) de Adobe Commerce.

>[!NOTE]
>
>El siguiente contenido se publicó originalmente en la publicación [Distribución de parches de Adobe Commerce a escala](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) del blog técnico de Adobe. Se ha modificado para centrarse en los pasos y ejemplos de código para implementar una estrategia centralizada de aplicación de parches. Consulte la publicación original para obtener más detalles sobre los distintos tipos de parches que se describen aquí.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Estrategia

Dado que hay muchos tipos diferentes de parches y muchas maneras de aplicarlos, ¿cómo sabe qué parche se aplica primero? Cuantos más parches tenga, mayores serán las posibilidades de que se apliquen al mismo archivo o a la misma línea de código. Los parches se aplican en el siguiente orden:

1. **Los parches de seguridad** forman parte de la base de código estático de una versión de Adobe Commerce.
1. **Revisiones del compositor** a través de `composer install` y `composer update` complementos como [cweagans/composer-patch](https://packagist.org/packages/cweagans/composer-patches).
1. **Todos los parches necesarios** están incluidos en el paquete [Parches de nube para Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html?lang=es).
1. **parches de calidad** seleccionados incluidos en [[!DNL [Quality Patches Tool]]](../../../tools/quality-patches-tool/usage.md).
1. **Parches personalizados** y parches de soporte de Adobe Commerce en el directorio `/m2-hotfixes` en orden alfabético por nombre de parche.

   >[!IMPORTANT]
   >
   >Cuantos más parches aplique, más complejo se volverá su código. El código complejo puede dificultar la actualización a una nueva versión de comercio de Adobe y aumentar el coste total de propiedad.

Si es responsable de mantener varias instalaciones de Adobe Commerce, garantizar que todas las instancias tengan el mismo conjunto de parches instalados puede ser complicado. Cada instalación tiene su propio repositorio de Git, directorio `/m2-hotfixes` y archivo `composer.json`. La única garantía que tiene es que los **parches de seguridad** y los **parches necesarios** para los usuarios de la nube están instalados como parte de su versión principal de Adobe Commerce.

En la actualidad, no existe una solución centralizada para este problema, pero Composer ofrece una forma de salvar la brecha. El paquete [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) le permite [aplicar parches de dependencias](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Puede crear un paquete Composer que instale todos sus parches y luego requerir ese paquete en todos sus proyectos.

Eso cubre **parches de seguridad**, **parches necesarios** y **parches del Compositor**, pero ¿qué pasa con los parches de calidad y el contenido del directorio `/m2-hotfixes`?

## Aplicar parches y revisiones de calidad

Puede instalar parches de calidad tanto en la infraestructura en la nube como en las instalaciones locales mediante el comando `vendor/bin/magento-patches apply`. Debe asegurarse de que el comando `vendor/bin/magento-patches apply` se ejecute después de `composer install` operaciones.

>[!NOTE]
>
>En la infraestructura en la nube, también puede instalar parches de calidad enumerándolos en el archivo `.magento.env.yaml` de su proyecto. El ejemplo descrito aquí requiere el uso del comando `vendor/bin/magento-patches apply`.

Puede especificar las revisiones que se aplicarán en el archivo `composer.json` de un paquete de componentes Composer personalizado y, a continuación, crear un paquete de complementos que ejecute el comando después de `composer install` operaciones.

En resumen, este ejemplo de aplicación centralizada de parches requiere la creación de dos paquetes personalizados de Composer:

- **Paquete de componentes:** `centralized-patcher`

   - Define la lista de parches de calidad y `m2-hotfixes` para instalar
   - Requiere el paquete `centralized-patcher-composer-plugin`, que ejecuta el comando `vendor/bin/magento-patches apply` después de `composer install` operaciones

- **Paquete de complemento:** `centralized-patcher-composer-plugin`

   - Define una clase PHP `CentralizedPatcher` que lee la lista de parches de calidad del paquete `centralized-patcher`
   - Ejecuta el comando `vendor/bin/magento-patches apply` para instalar la lista de parches de calidad después de `composer install` operaciones

### `centralized-patcher`

Puede crear un paquete de componentes del Compositor (`centralized-patcher`) para administrar de forma centralizada todos los parches de calidad y `/m2-hotfixes` en todas las instalaciones de Adobe Commerce.

El paquete de componentes debe:

- Copie el contenido del directorio `/m2-hotfixes` en todas las instalaciones durante la implementación.
- Defina la lista de parches de calidad que desea instalar.
- Ejecute el comando `vendor/bin/magento-patches` para instalar la misma lista de parches de calidad en todas las instalaciones (utilizando el paquete de complemento [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) como dependencia).

Para crear el paquete de componentes `centralized-patcher`:

1. Crear un archivo de `composer.json` con el siguiente contenido:

   >[!NOTE]
   >
   >El atributo `require` del ejemplo siguiente muestra una dependencia `require` en el [paquete de complemento](#centralized-patcher-composer-plugin) que debe crear más adelante en este ejemplo.

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. Cree un directorio `/m2-hotfixes` dentro del paquete y agréguelo al atributo `map` en el archivo `composer.json`. El atributo `map` contiene archivos para copiar de este paquete en la raíz del proyecto de destino al que desea aplicar el parche.

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >El paquete `centralized-patcher` copia el contenido del directorio `/m2-hotfixes` en el directorio m2-hotfixes del proyecto de destino en `composer install`.  Dado que los scripts de implementación en la nube aplican revisiones m2 después de `composer install`, el mecanismo de implementación instala todas las revisiones.

1. Defina los parches de calidad que desea instalar en el atributo `quality-patches`.

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


El atributo `quality-patches` del ejemplo de código anterior contiene dos parches de la [lista completa de parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) como ejemplo.  Estas revisiones de calidad se instalan en todos los proyectos que requieren el paquete `centralized-patcher` mediante el comando `vendor/bin/magento-patches apply`.

Para realizar pruebas, puede crear un parche de ejemplo (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>Debe colocar sus propios parches en el directorio `m2-hotfixes` junto con los parches que reciba directamente del Soporte técnico de Adobe Commerce.

Un ejemplo de archivo de revisión (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

Dado que este ejemplo utiliza el método local para instalar parches de calidad, debe asegurarse de que el comando `vendor/bin/magento-patches apply` se ejecute después de `composer install` operaciones. Este complemento se activa después de `composer install` operaciones, lo que ejecuta el comando `vendor/bin/magento-patches apply`.

Para crear el paquete de componentes `centralized-patcher-compose-plugin`:

1. Crear un archivo de `composer.json` con el siguiente contenido:

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. Cree un archivo PHP y defina una clase `CentralizedPatcher` para leer la lista de parches de calidad del paquete de componentes [`centralized-patcher`](#centralized-patcher) e instálelos inmediatamente después de cada operación de `composer install`.

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>Consulte los [ejemplos de código](#code-examples) para ver los dos paquetes que se describen en este ejemplo en acción.


## Qué hacer con los parches específicos del proyecto

Es posible que tenga un escenario en el que solo se requiera el 95% de los parches en todos los proyectos, mientras que algunos parches se aplican solo a una instancia específica. La forma habitual de aplicar parches sigue funcionando. Puede mantener parches específicos del proyecto en el directorio `/m2-hotfixes` e instalar parches de calidad por proyecto.

Si usa este método, **no** confirme ningún parche en el directorio `/m2-hotfixes` que el paquete de componentes `centralized-patcher` haya copiado en el proyecto. Puede evitar confirmaciones accidentales agregando `/m2-hotfixes` al archivo `.gitignore`. Después de actualizar el archivo `.gitignore`, recuerde que debe agregarse cualquier `/m2-hotfixes` específico del proyecto mediante el comando `git add –force`.

## Ejecución de diferentes versiones de Adobe Commerce

Asegúrese de establecer la dependencia correcta en el paquete de componentes `centralized-patcher`. Por ejemplo, puede que necesite Adobe Commerce 2.4.5-p2 para una versión específica del paquete, que solo proporciona parches compatibles con Adobe Commerce 2.4.5-p2. Puede tener otra versión de este paquete compatible con Adobe Commerce 2.4.4.

## Comprensión del resultado

Al igual que con Adobe Commerce en la infraestructura en la nube, este artículo supone que el proceso de implementación utiliza el comando `composer install` y no `composer update` o `git pull` para implementar código nuevo en los servidores. El flujo de instalación centralizada de parches tendrá el siguiente aspecto:

1. Instalación del Compositor

   - Instala Adobe Commerce, incluidos los parches funcionales y de seguridad -p1 o -p2
   - Combina `/m2-hotfixes` centralizados y parches de soporte con `/m2-hotfixes` específicos del proyecto y parches de soporte
   - Aplica las revisiones instaladas con el paquete Compositor `cweagans/composer-patches`

1. Después de `composer install`

   - El complemento Composer instala parches de calidad centralizados

1. Implementación

   - Los parches necesarios y los parches de calidad específicos del proyecto se instalan en función del archivo `.magento.env.yaml` (solo Adobe Commerce en proyectos de infraestructura en la nube).
   - Los parches personalizados y los parches de soporte del directorio `/m2-hotfixes` se instalan en orden alfabético por nombre de parche.

De este modo, puede gestionar de forma centralizada todos sus parches para todas sus instalaciones y garantizar mejor la seguridad y estabilidad de sus tiendas Adobe Commerce. Utilice los siguientes métodos para comprobar el estado del parche:

- [Proyectos de infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es#view-available-patches-and-status)
- [Proyectos locales](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Ejemplos de código

- [Parches centralizados en el Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Parches centralizados en Adobe Commerce en la infraestructura en la nube](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Complemento de composición de parches centralizado](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Componente de revisión centralizado](https://github.com/AntonEvers/centralized-patcher)
