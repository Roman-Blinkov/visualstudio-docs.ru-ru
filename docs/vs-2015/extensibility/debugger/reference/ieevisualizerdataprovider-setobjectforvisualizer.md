---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d20164e31f8c42b7099f99ff34ac120319a2def1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540283"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод изменяет объект, представляющий визуализатор.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pNewObject`  
 [in] Задаваемый объект.  
  
 `error`  
 [out] Если произошла ошибка при установке объекта, эта строка содержит сообщение об ошибке.  
  
 `pException`  
 [out] Если произошла ошибка, этот объект содержит сведения об исключении.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Это зависит от разработчика, чтобы определить, каким образом возвращаются сведения об ошибке. Тем не менее существует возможность, что некоторые вызывающим объектам может только внешний вид, чтобы узнать, был ли объект исключения возвращены знать, существует ошибка, поэтому этот метод всегда должен возвращать объект исключения, если произошла ошибка. Строка ошибки также должен быть предоставлен, в случае, если вызывающий объект хочет, чтобы его использовать.  
  
## <a name="see-also"></a>См. также  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
