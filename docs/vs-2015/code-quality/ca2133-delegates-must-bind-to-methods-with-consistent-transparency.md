---
title: 'CA2133: делегаты должны быть привязаны к методам с единообразной прозрачностью | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 487047b7dd3096e65a6e287d79d91d3029f3dc5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608988"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: делегаты должны привязываться к методам с согласованной прозрачностью
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|делегатесмустбиндвисконсистенттранспаренци|
|CheckId|CA2133|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

> [!NOTE]
> Это предупреждение применяется только к коду, на котором работает CoreCLR (версия CLR, относящаяся к веб-приложениям Silverlight).

## <a name="cause"></a>Причина
 Это предупреждение срабатывает для метода, который привязывает делегат, помеченный <xref:System.Security.SecurityCriticalAttribute>, к методу, который является прозрачным или помеченным <xref:System.Security.SecuritySafeCriticalAttribute>. Предупреждение также запускает метод, который привязывает прозрачный или безопасный делегат к критическому методу.

## <a name="rule-description"></a>Описание правила
 Типы делегатов и методы, к которым они привязаны, должны иметь одинаковую прозрачность. Прозрачные и критические для безопасности делегаты могут быть привязаны только к другим прозрачным или безопасным методам. Аналогичным образом, критические делегаты могут быть привязаны только к критическим методам. Эти правила привязки гарантируют, что единственный код, который может вызвать метод через делегат, может также вызывать тот же метод напрямую. Например, правила привязки не позволяют прозрачному коду вызывать критический код непосредственно через прозрачный делегат.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого предупреждения, измените прозрачность делегата или метода, к которому он привязан, чтобы прозрачность этих двух эквивалентна.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]
