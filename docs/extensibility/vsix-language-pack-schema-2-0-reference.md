---
title: Справочник по схеме 2.0 VSIX языкового пакета | Документация Майкрософт
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: dagriffe
author: dgriffen
manager: douge
ms.workload:
- dagriffe
ms.openlocfilehash: 94d785ce55b57e35b0880537e099cbc3e03d20ab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855822"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Справочник по схеме 2.0 VSIX языкового пакета

Схема языкового пакета VSIX предоставляет локализованные сведения об установке пакетов VSIX. Версии 2.0 этой схемы поддерживает локализацию дополнительные элементы.

## <a name="language-pack-schema"></a>Схема языкового пакета

Корневой элемент файла пакета языка — `<PackageLanguagePackManifest>`, с атрибутом `Version`, которая является версией языковой формат пакета. В этой статье описывается версия 2.0 пакета языковой формат, который указывается в манифесте, задав `Version` значение атрибута `Version="2.0.0"`. Корневой элемент содержит только одну дочернюю `<Metadata>` элемент.

### <a name="packagelangaugepackmanifest-element"></a>Элемент PackageLangaugePackManifest

В рамках `<PackageLanguagePackManifest>` элемент, должен существовать следующий элемент:

|Заголовок|Описание|
|-----------|-----------------|
|`<Metadata>`| Элемент-контейнер для всех метаданных локализованного пакета

### <a name="metadata-element"></a>Элемент метаданных

В рамках `<Metadata>` элемент может иметь следующие элементы:

|Заголовок|Описание|
|-----------|-----------------|
|`<DisplayName>`|Локализованное имя модуля для установки|
|`<Description>`|Локализованное описание устанавливаемое расширение|
|`<License>`| Путь к локализованной версии лицензию на расширение|
|`<MoreInfo>`| Ссылка на локализованные сведения о расширении|
|`<ReleaseNotes>`| Путь или ссылку на локализованной версии заметок о выпуске|
|`<Icon>`| Путь к локализованной версии значок расширения|

### <a name="sample-manifest"></a>Пример манифеста

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)|Показан способ предоставления поддержки локализованной установки для пакета VSIX.|
|[Справочник по схеме 2.0 расширения VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)|Манифест VSIX описывает содержимое *.vsix* файл развертывания. Файл развертывания позволяет установить это расширение Visual Studio с помощью **расширения и обновления** диалоговое окно.|
|[Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Демонстрируется использование **расширения и обновления** диалоговое окно, чтобы установить, удалить, активации и деактивации расширений.|