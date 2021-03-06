---
title: Устранение проблем, связанных с анализом кода | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1b21666094d2a13054be49980028afcc7a7e39a3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224020"
---
# <a name="troubleshooting-code-analysis-issues"></a>Устранение проблем, связанных с анализом кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе приводятся сведения об устранении указанных ниже неполадок, связанных с анализом кода в Visual Studio.  
  
-   [Изменения в наборе правил Visual Studio 2010 не отражаются в предыдущих версиях Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Изменения в наборе правил Visual Studio 2010 не отражаются в предыдущих версиях Visual Studio  
 При создании в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] набора правил, содержащего дочерний набор правил, изменения, внесенные в дочерний набор правил, могут не применяться при анализе кода на компьютерах, на которых используется предыдущая версия Visual Studio. Для устранения этой проблемы необходимо принудительно перезаписать родительский набор правил, то есть набор правил, содержащий дочерний набор.  
  
1.  Откройте родительский набор правил в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
2.  Внесите изменение, например добавьте или удалите правило, а затем сохраните набор правил.  
  
3.  Повторно откройте набор правил, отмените изменение, а затем сохраните набор правил повторно.  
  
## <a name="see-also"></a>См. также  
 [Анализ качества приложения](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)



