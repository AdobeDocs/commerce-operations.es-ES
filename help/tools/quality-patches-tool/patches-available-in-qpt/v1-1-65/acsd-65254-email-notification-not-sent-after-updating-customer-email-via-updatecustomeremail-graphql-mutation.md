---
title: 'ACSD-65254: notificación por correo electrónico no enviada después de actualizar el correo electrónico del cliente mediante updateCustomerEmail [!DNL GraphQL] mutation'
description: Aplique el parche ACSD-65254 para corregir el problema de Adobe Commerce por el que las notificaciones por correo electrónico no se enviaban a los clientes después de actualizar correctamente sus direcciones de correo electrónico en sus cuentas mediante la mutación updateCustomerEmail [!DNL GraphQL] mutation.
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: a97daceb-98f6-4bb8-9847-692af700c0fd
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-65254: notificación por correo electrónico no enviada después de actualizar el correo electrónico del cliente mediante la mutación `updateCustomerEmail` [!DNL GraphQL]

El parche ACSD-65254 corrige el problema por el que las notificaciones por correo electrónico no se enviaban a los clientes después de actualizar sus direcciones de correo electrónico en sus cuentas mediante la mutación `updateCustomerEmail` [!DNL GraphQL]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. El ID del parche es ACSD-65254. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se enviaron notificaciones por correo electrónico a los clientes después de actualizar sus direcciones de correo electrónico con la mutación `updateCustomerEmail` [!DNL GraphQL].

<u>Pasos a seguir</u>:

1. Crear usuario con la siguiente mutación:

   ```
   mutation {
   	    createCustomer(
   		    input: {
   			    firstname: "Test"
   			    lastname: "User"
   			    email: "test@test.com"
   			    password: "Admin@123"
   			    is_subscribed: true
   		    }
   	    ) {
   		    customer {
   			    created_at
   		    }
   	    }
   }
   ```

1. Genere un token para el usuario creado anteriormente y utilícelo como token de portador:

   ```
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
   	    token
   }
   }
   ```

1. Intente actualizar el correo electrónico del usuario creado anteriormente con el último token de portador creado:

   ```
   mutation {
   	    updateCustomerEmail(email: "test+updated@test.com", password: "Admin@123") {
   		    customer {
   			    email
   		    }
   	    }
   }
   ```

<u>Resultados esperados</u>:

Los clientes deben recibir notificaciones por correo electrónico después de actualizar las direcciones de correo electrónico en sus cuentas.

<u>Resultados reales</u>:

Solo se envía un correo electrónico de suscripción a la nueva dirección; no se envía el correo electrónico de confirmación del cambio de dirección de correo electrónico.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
