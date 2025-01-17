---
title: Parámetros de propiedad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369584"
---
# <a name="property-parameters"></a>Parámetros de propiedad

En la tabla siguiente se enumeran los nombres recomendados y la funcionalidad de los parámetros de propiedad.

|Parámetro|Funcionalidad|
|---|---|
|**Contabiliza**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario pueda especificar el número de objetos que se van a procesar.|
|**Descripción**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar una descripción de un recurso.|
|**De**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el objeto de referencia del que se va a obtener información.|
|**Sesión**<br>Tipo de datos: dependiente del recurso|Implemente este parámetro para que el usuario pueda especificar el identificador de un recurso.|
|**Entradas**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar la especificación del archivo de entrada.|
|**Ubicación**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar la ubicación del recurso.|
|**LogName**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el nombre del archivo de registro que se va a procesar o usar.|
|**Name**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el nombre del recurso.|
|**Genere**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el archivo de salida.|
|**Propietario**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el nombre del propietario del recurso.|
|**Propiedad**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el nombre o los nombres de las propiedades que se van a utilizar.|
|**Debido**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar por qué se invoca este cmdlet.|
|**Regular**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que se usen expresiones regulares cuando se especifique el parámetro. Cuando se especifica este parámetro, no se resuelven los caracteres comodín.|
|**Rápidas**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario pueda especificar la velocidad en baudios. El usuario establece este parámetro en la velocidad del recurso.|
|**State**<br>Tipo de datos: palabra clave array|Implemente este parámetro para que el usuario pueda especificar los nombres de los Estados, como KEYDOWN.|
|**Valor**<br>Tipo de datos: objeto|Implemente este parámetro para que el usuario pueda especificar un valor para proporcionar al cmdlet.|
|**Versión**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar la versión de la propiedad.|

## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
