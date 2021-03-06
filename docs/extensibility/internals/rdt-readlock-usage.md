---
title: Использование RDT_ReadLock | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fda2fbb4a4b03dff9d677d9c7581a4138d9fcf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131685"
---
# <a name="rdtreadlock-usage"></a>Использование RDT_ReadLock

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> представляет собой флаг, который предоставляет логику для блокировки документа на в под управлением документа таблицы (RDT), который приводится список все документы, открытые в настоящий момент в Интегрированной среде разработки Visual Studio. Этот флаг определяет, при открытии документов и является ли документ видимым в пользовательском интерфейсе или принудительное незаметно в памяти.

Как правило, используется <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> когда верно одно из следующих:

- При необходимости незаметно открыть документ и доступными только для чтения, но она еще не установлено, что <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> должен принадлежать его.

- При необходимости пользователю будет предложено сохранить документ, который был открыт незаметно, прежде чем пользователь он отображается в пользовательском Интерфейсе и затем была предпринята попытка закрыть его.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Управление видимым и невидимым документов

Когда пользователь открывает документ в пользовательском Интерфейсе <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> владелец документа должно быть установлено и <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> должен быть установлен флаг. Если не <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> владелец может быть установлено, то не сохранятся при щелчке **сохранить все** или закрывает интегрированной среды разработки. Это означает, что если документ открыт незаметно там, где они были изменены в памяти, и пользователю будет предложено сохранить документ при завершении работы или при сохранении Если **сохранить все** выбрано, то `RDT_ReadLock` не может использоваться. Вместо этого необходимо использовать `RDT_EditLock` и зарегистрируйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> при <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> флаг.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock и изменение документа

Флаг предыдущих упомянутые указывает, что даст невидимой Открытие документа его `RDT_EditLock` при открытии документа пользователем в видимое **DocumentWindow**. В этом случае пользователю предоставляется **Сохранить** приглашение по видимых **DocumentWindow** закрыт. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` реализации, использующие <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> служба изначально работать, только если `RDT_ReadLock` извлекается (т. е. когда документ будет открыт незаметно для синтаксического анализа данных). Позже, если требуется изменить документ, затем блокировки будет обновлена до слабым **RDT_EditLock**. Если пользователь затем открывает документ в видимое **DocumentWindow**, `CodeModel`слабое `RDT_EditLock` освобождается.

Если пользователь закрывает **DocumentWindow** и выбирает **нет** при запросе на сохранение открытых документов, то `CodeModel` реализация удаляет все сведения в документе и открытия документ с диска незаметно при очередном Дополнительные сведения не требуются для документа. Особенность такое поведение является экземпляром, когда пользователь открывает **DocumentWindow** невидимой открытого документа, его изменение, закрывает его и затем выбирает **нет** при запросе на сохранение документа. В этом случае, если документ имеет `RDT_ReadLock`, документ фактически не закрывается и измененный документ остается открытым незаметно в памяти, несмотря на то, что пользователь не был сохранен в документе.

Если невидимой Открытие документа использует слабым `RDT_EditLock`, а затем он возвращает его блокировки, когда пользователь открывает документ, видимое и нет других блокировки удерживаются. Когда пользователь закрывает **DocumentWindow** и выбирает **нет** при запросе на сохранение документа, затем документ должен быть закрыт из памяти. Это означает, что невидимой клиент должен прослушивать события RDT для отслеживания возникновения. При очередном документа является обязательным, его нужно открыть заново.