---
title: 'Идебугаппликатионнодивентс:: onattach | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAttach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAttach
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e45af6b931dad28a41f8f4453db9fab96405df3b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574692"
---
# <a name="idebugapplicationnodeeventsonattach"></a>IDebugApplicationNodeEvents::onAttach
Обрабатывает событие, которое означает, что объект узла приложения отладки был присоединен к родительскому узлу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `prddpParent`  
 окне Узел приложения отладки, являющийся родительским для данного узла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод обрабатывает событие, которое означает, что объект узла приложения отладки был присоединен к родительскому узлу.  
  
 Разработчики `IDebugApplicationNode`ного интерфейса вызывают это событие.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебугаппликатионнодивентс](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 @No__t_1 [идебугаппликатионнодивентс:: Ondetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)  
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)