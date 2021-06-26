---
title: Использование групповых политик для управления расширениями Microsoft Edge
ms.author: aspoddar
author: AndreaLBarr
manager: balajek
ms.date: 06/09/2021
audience: ITPro
ms.topic: conceptual
ms.prod: microsoft-edge
ms.localizationpriority: high
ms.collection: M365-modern-desktop
description: Использование групповых политик для управления расширениями Microsoft Edge на предприятии
ms.openlocfilehash: a633b036c1733716dfb257b4711bca57bd6721f0
ms.sourcegitcommit: 4192328ee585bc32a9be528766b8a5a98e046c8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "11618247"
---
# <a name="use-group-policies-to-manage-microsoft-edge-extensions"></a><span data-ttu-id="2b653-103">Использование групповых политик для управления расширениями Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2b653-103">Use group policies to manage Microsoft Edge extensions</span></span>

<span data-ttu-id="2b653-104">В этой статье описываются параметры и действия для управления расширениями с помощью групповых политик.</span><span class="sxs-lookup"><span data-stu-id="2b653-104">This article describes the options and steps for managing extensions by using group policies.</span></span> <span data-ttu-id="2b653-105">Эти параметры предполагают, что вы уже управляете браузером Microsoft Edge для своих пользователей.</span><span class="sxs-lookup"><span data-stu-id="2b653-105">These options  assume that you already have Microsoft Edge managed for your users.</span></span> <span data-ttu-id="2b653-106">Если вы еще не настроили управление Microsoft Edge для пользователей, перейдите по ссылке ниже, чтобы сделать это сейчас.</span><span class="sxs-lookup"><span data-stu-id="2b653-106">If you have not already set up Microsoft Edge to be managed for your users please follow the below link to do so now.</span></span>

- [<span data-ttu-id="2b653-107">Управление расширениями Microsoft Edge на предприятии</span><span class="sxs-lookup"><span data-stu-id="2b653-107">Manage Microsoft Edge extensions in the enterprise</span></span>](/deployedge/microsoft-edge-manage-extensions)

> [!NOTE]
> <span data-ttu-id="2b653-108">Эта статья относится к Microsoft Edge версии 77 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="2b653-108">This article applies to Microsoft Edge version 77 or later.</span></span>

## <a name="block-extensions-based-on-their-permissions"></a><span data-ttu-id="2b653-109">Блокировка расширений на основе их разрешений</span><span class="sxs-lookup"><span data-stu-id="2b653-109">Block extensions based on their permissions</span></span>

<span data-ttu-id="2b653-110">Вы можете управлять тем, какие расширения пользователи могут устанавливать на основе разрешений, с помощью политики [ExtensionSettings](/deployedge/microsoft-edge-policies#extensionsettings).</span><span class="sxs-lookup"><span data-stu-id="2b653-110">You can control what extensions your users can install based on permissions using the [ExtensionSettings](/deployedge/microsoft-edge-policies#extensionsettings) policy.</span></span> <span data-ttu-id="2b653-111">Если установленному расширению требуется разрешение, которое заблокировано, оно просто не запустится.</span><span class="sxs-lookup"><span data-stu-id="2b653-111">If an installed extension needs a permission that’s blocked, it just won't run.</span></span> <span data-ttu-id="2b653-112">Расширение не удаляется, а просто отключается.</span><span class="sxs-lookup"><span data-stu-id="2b653-112">The extension isn't removed, just disabled.</span></span>

> [!NOTE]
> <span data-ttu-id="2b653-113">Параметр блокировки разрешений можно настроить только в политике параметров расширений.</span><span class="sxs-lookup"><span data-stu-id="2b653-113">The blocked permissions setting can only be set within the extension settings policy.</span></span>  

<span data-ttu-id="2b653-114">Используйте следующие действия в качестве руководства для блокировки расширения.</span><span class="sxs-lookup"><span data-stu-id="2b653-114">Use the following steps as a guide for blocking an extension.</span></span>

1. <span data-ttu-id="2b653-115">Откройте редактор управления групповыми политиками и выберите **Административные шаблоны > Microsoft Edge > Расширения**, а затем щелкните **Настройки управления расширениями**.</span><span class="sxs-lookup"><span data-stu-id="2b653-115">Open the group policy management editor and go to **Administrative Templates > Microsoft Edge > Extensions**  and then select **Configure extension management settings**.</span></span>
2. <span data-ttu-id="2b653-116">Включите политику, а затем введите разрешения, которые нужно разрешить или заблокировать, с помощью сжимаемой строки JSON.</span><span class="sxs-lookup"><span data-stu-id="2b653-116">Enable the policy, then enter the permissions that you want allowed or blocked, by using a JSON string that gets compressed.</span></span> <span data-ttu-id="2b653-117">На следующем снимке экрана показано, как заблокировать расширение, использующее разрешение "usb".</span><span class="sxs-lookup"><span data-stu-id="2b653-117">The next screenshot shows how to block an extension that uses the permission "usb".</span></span>

    :::image type="content" source="media/microsoft-edge-manage-extensions-policies/manage-extensions-gp-block-1.png" alt-text="Настройка групповой политики для блокировки расширения.":::

<span data-ttu-id="2b653-119">В следующем примере показан формат JSON для блокировки любого расширения, которое требует использования разрешения "usb", и соответствующая сжатая строка.</span><span class="sxs-lookup"><span data-stu-id="2b653-119">The following example shows the JSON to block any extension that needs the use of permission "usb" and its compressed string.</span></span>

### <a name="json-example"></a><span data-ttu-id="2b653-120">Пример JSON</span><span class="sxs-lookup"><span data-stu-id="2b653-120">JSON example</span></span>

   ```json
   { 
        "*": { 
             "blocked_permissions": ["usb"] 
        } 
   } 
   ```

   ```json
   {"*":{"blocked_permissions":["usb"]}} 
   ```

   > [!NOTE]
   > <span data-ttu-id="2b653-121">Чтобы заблокировать все расширения, использующие разрешение, примените звездочку для ИД расширения, как показано в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="2b653-121">To block all extensions that use the permission, use an asterisk for the extension ID, as shown in the previous example.</span></span> <span data-ttu-id="2b653-122">Если указать один ИД расширения, политика будет применяться только к этому расширению.</span><span class="sxs-lookup"><span data-stu-id="2b653-122">If you specify one extension ID, the policy will only apply to that extension.</span></span> <span data-ttu-id="2b653-123">Вы можете заблокировать несколько расширений, но они должны быть отдельными записями.</span><span class="sxs-lookup"><span data-stu-id="2b653-123">You can block more than one, but they need to be separate entries.</span></span>

## <a name="prevent-extensions-from-altering-web-pages"></a><span data-ttu-id="2b653-124">Запрет изменения веб-страниц расширениями</span><span class="sxs-lookup"><span data-stu-id="2b653-124">Prevent extensions from altering web pages</span></span>

<span data-ttu-id="2b653-125">Этот параметр не позволяет расширениям читать и изменять данные с конфиденциальных веб-сайтов и доменов.</span><span class="sxs-lookup"><span data-stu-id="2b653-125">This setting prevents extensions from reading and changing  data from sensitive websites and domains.</span></span> <span data-ttu-id="2b653-126">Запрет нежелательных действий выполняется путем блокировки действий, таких как внедрение сценария на веб-сайты, чтение файлов cookie или внесение изменений в веб-запросы.</span><span class="sxs-lookup"><span data-stu-id="2b653-126">Blocking unwanted actions is done by blocking actions such as script injection into your websites, reading the cookies, or making web-request modifications.</span></span> <span data-ttu-id="2b653-127">Этот параметр не запрещает установку или удаление расширений пользователями, а только предотвращает изменение указанных веб-сайтов расширениями.</span><span class="sxs-lookup"><span data-stu-id="2b653-127">This setting doesn’t prevent your users from installing or removing extensions, it only prevents extensions from altering the specified websites.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="2b653-128">Параметр разрешенных и заблокированных узлов среды выполнения можно настроить только в политике параметров расширений.</span><span class="sxs-lookup"><span data-stu-id="2b653-128">The Runtime allowed/blocked hosts setting can only be set within the extension settings policy.</span></span>  

<span data-ttu-id="2b653-129">Вы можете настроить следующие параметры политики ExtensionSettings, чтобы запретить (или разрешить) изменения веб-сайтов или доменов.</span><span class="sxs-lookup"><span data-stu-id="2b653-129">You can configure the following settings in the ExtensionSettings policy to prevent (or allow) alterations of websites or domains:</span></span>

- <span data-ttu-id="2b653-130">**Runtime_blocked_hosts**.</span><span class="sxs-lookup"><span data-stu-id="2b653-130">**Runtime_blocked_hosts**.</span></span> <span data-ttu-id="2b653-131">Этот параметр запрещает расширениям вносить изменения или читать данные с указанных вами веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="2b653-131">This setting blocks extensions from making changes or reading data from the websites you specify.</span></span>
- <span data-ttu-id="2b653-132">**Runtime_allowed_hosts**.</span><span class="sxs-lookup"><span data-stu-id="2b653-132">**Runtime_allowed_hosts**.</span></span> <span data-ttu-id="2b653-133">Этот параметр позволяет расширениям вносить изменения или читать данные с указанных вами веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="2b653-133">This setting allows extensions to make changes or read data from the websites you specify.</span></span> <span data-ttu-id="2b653-134">Следующий формат используется для указания сайтов в строке JSON в политике.</span><span class="sxs-lookup"><span data-stu-id="2b653-134">The following format is used for specifying your site(s) in the JSON string in the policy:</span></span>

  ```json
  [http|https|ftp|*]://[subdomain|*].[hostname|*].[eTLD|*] [http|https|ftp|*],
  ```

  > [!NOTE]
  > `[hostname|*], and [eTLD|*]` <span data-ttu-id="2b653-135">— обязательные разделы, а раздел `[subdomain|*]` — необязательный.</span><span class="sxs-lookup"><span data-stu-id="2b653-135">sections are required, but `[subdomain|*]` section is optional.</span></span>

<span data-ttu-id="2b653-136">В следующей таблице показаны примеры допустимых шаблонов узлов и шаблонов соответствий.</span><span class="sxs-lookup"><span data-stu-id="2b653-136">The following table shows examples of valid host patterns and matching patterns.</span></span>

|<span data-ttu-id="2b653-137">Допустимые шаблоны узлов</span><span class="sxs-lookup"><span data-stu-id="2b653-137">Valid host patterns</span></span>|<span data-ttu-id="2b653-138">Соответствуют</span><span class="sxs-lookup"><span data-stu-id="2b653-138">Matches</span></span>|<span data-ttu-id="2b653-139">Не соответствуют</span><span class="sxs-lookup"><span data-stu-id="2b653-139">Doesn't match</span></span>|
|--|--|--|
|  `*://*.example.*` | `http://example.com`<br>`https://test.example.co.uk`   | `https://example.microsoft.com`<br>`http://example.microsoft.co.uk`  |
| `http://example.*` | `http://example.com`<br>`http://example.ly` | `https://example.com`<br>`http://test.example.com`   |
| `http://example.com`   | `http://example.com` | `https://example.com`<br>`http://test.example.co.uk` |
| `*://*`   | <span data-ttu-id="2b653-140">Все URL-адреса</span><span class="sxs-lookup"><span data-stu-id="2b653-140">All URLs</span></span>  |   |

<span data-ttu-id="2b653-141">Чтобы заблокировать или разрешить расширениям доступ к веб-сайту или домену, используйте следующие действия в качестве руководства.</span><span class="sxs-lookup"><span data-stu-id="2b653-141">Use the following steps as a guide to block or allow extensions to access a website or domain.</span></span>

1. <span data-ttu-id="2b653-142">Откройте редактор управления групповыми политиками и перейдите в раздел **Административные шаблоны > Microsoft Edge > Расширения**, а затем выберите **Настройки управления расширениями**.</span><span class="sxs-lookup"><span data-stu-id="2b653-142">Open the group policy management editor and go to **Administrative Templates > Microsoft Edge > Extensions**, and then select **Configure extension management settings**.</span></span>  
2. <span data-ttu-id="2b653-143">Включите политику, а затем введите разрешения, которые нужно разрешить или заблокировать, сжав разрешения в одной строке JSON.</span><span class="sxs-lookup"><span data-stu-id="2b653-143">Enable the policy, then enter the permissions that you want allowed or blocked, compressing the permissions to a single JSON string.</span></span>

<span data-ttu-id="2b653-144">В следующих примерах показано, как блокировать расширения в имени узла и в одном домене.</span><span class="sxs-lookup"><span data-stu-id="2b653-144">The following examples show how to block extensions on a hostname and how to block extensions on the same domain.</span></span>

### <a name="json-example-to-block-hostname"></a><span data-ttu-id="2b653-145">Пример JSON для блокировки имени узла</span><span class="sxs-lookup"><span data-stu-id="2b653-145">JSON example to block hostname</span></span>

<span data-ttu-id="2b653-146">В этом примере показан формат JSON и сжатая строка JSON с целью заблокировать любому расширению доступ к имени узла `www.microsoft.com`.</span><span class="sxs-lookup"><span data-stu-id="2b653-146">This example shows the JSON and compressed JSON string to block any extension from accessing the `www.microsoft.com` hostname.</span></span>

```json
{ 
    "*":{ 
            "runtime_blocked_hosts":["www.microsoft.com"] 
    } 
} 
```

```json
{"*":{"runtime_blocked_hosts":["www.microsoft.com"]}} 
```

> [!NOTE]
> <span data-ttu-id="2b653-147">Чтобы заблокировать доступ к веб-странице для всех расширений, используйте звездочку для ИД расширения, как показано в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="2b653-147">To block all extensions from accessing a webpage, use an asterisk for the extension ID, as shown in the previous example.</span></span>  <span data-ttu-id="2b653-148">Если вместо звездочки указать один ИД расширения, политика будет применяться только к этому расширению.</span><span class="sxs-lookup"><span data-stu-id="2b653-148">If you specify one extension ID instead of an asterisk, the policy will only apply to that extension.</span></span> <span data-ttu-id="2b653-149">Вы можете заблокировать несколько расширений, но они должны быть отдельными записями.</span><span class="sxs-lookup"><span data-stu-id="2b653-149">You can block more than one extension, but they need to be separate entries.</span></span>

### <a name="json-example-to-block-extensions-on-same-domain"></a><span data-ttu-id="2b653-150">Пример JSON для блокировки расширений в одном домене</span><span class="sxs-lookup"><span data-stu-id="2b653-150">JSON example to block extensions on same domain</span></span>

<span data-ttu-id="2b653-151">В этом примере показан формат JSON и сжатая строка JSON с целью заблокировать запуск определенных расширений в одном домене "importantwebsite".</span><span class="sxs-lookup"><span data-stu-id="2b653-151">This example shows the JSON and compressed JSON string to block specific extensions from running on the same domain, "importantwebsite".</span></span>

```json
{ 
    "aapbdbdomjkkjkaonfhkkikfgjllcleb": { 
        "runtime_blocked_hosts": ["*://*.importantwebsite"] 
    }, 
    "bfbmjmiodbnnpllbbbfblcplfjjepjdn": { 
        "runtime_blocked_hosts": ["*://*.importantwebsite"] 
    } 
} 
```

```json
{"aapbdbdomjkkjkaonfhkkikfgjllcleb": {"runtime_blocked_hosts": ["*://,*.importantwebsite"]},"bfbmjmiodbnnpllbbbfblcplfjjepjdn": {"runtime_blocked_hosts": ["*://*.importantwebsite"]}} 
```

## <a name="allow-or-block-extensions-in-group-policy"></a><span data-ttu-id="2b653-152">Разрешение или блокировка расширений в групповой политике</span><span class="sxs-lookup"><span data-stu-id="2b653-152">Allow or block extensions in group policy</span></span>

<span data-ttu-id="2b653-153">Вы можете использовать политики [ExtensionInstallBlocklist](/DeployEdge/microsoft-edge-policies#extensioninstallblocklist) и [ExtensionInstallAllowlist](/DeployEdge/microsoft-edge-policies#extensioninstallallowlist), чтобы управлять тем, какие расширения заблокированы или разрешены.</span><span class="sxs-lookup"><span data-stu-id="2b653-153">You can use the [ExtensionInstallBlocklist](/DeployEdge/microsoft-edge-policies#extensioninstallblocklist) and [ExtensionInstallAllowlist](/DeployEdge/microsoft-edge-policies#extensioninstallallowlist) policies to control which extensions are blocked or allowed.</span></span> <span data-ttu-id="2b653-154">Используйте следующие действия в качестве руководства, чтобы разрешить все расширения, за исключением тех, которые необходимо заблокировать.</span><span class="sxs-lookup"><span data-stu-id="2b653-154">Use the following steps as a guide to allow all extensions except those you want to block.</span></span>

1. <span data-ttu-id="2b653-155">Откройте редактор управления групповыми политиками и перейдите в раздел **Административные шаблоны > Microsoft Edge > Расширения**, а затем выберите **Управление расширениями, которые нельзя устанавливать**.</span><span class="sxs-lookup"><span data-stu-id="2b653-155">Open the group policy management editor and go to **Administrative Templates > Microsoft Edge > Extensions >** and then select **Control which extensions cannot be installed**.</span></span>
2. <span data-ttu-id="2b653-156">Выберите **Включено**.</span><span class="sxs-lookup"><span data-stu-id="2b653-156">Select **Enabled**.</span></span>
3. <span data-ttu-id="2b653-157">Щелкните **Показать**.</span><span class="sxs-lookup"><span data-stu-id="2b653-157">Click **Show**.</span></span>
4. <span data-ttu-id="2b653-158">Введите идентификатор приложения для расширений, которые необходимо заблокировать.</span><span class="sxs-lookup"><span data-stu-id="2b653-158">Enter the app ID of the extensions that you want to block.</span></span> <span data-ttu-id="2b653-159">При добавлении нескольких идентификаторов приложений используйте отдельную строку для каждого идентификатора.</span><span class="sxs-lookup"><span data-stu-id="2b653-159">When adding multiple app ID’s use a separate row for each ID.</span></span>
5. <span data-ttu-id="2b653-160">Чтобы заблокировать все расширения, введите **\*** в политику, чтобы запретить установку любых расширений.</span><span class="sxs-lookup"><span data-stu-id="2b653-160">To block all extensions, type **\*** into the policy to prevent any extensions from being installed.</span></span> <span data-ttu-id="2b653-161">Вы можете использовать это в сочетании с политикой "Разрешить установку определенных расширений", чтобы разрешить установку только определенных расширений.</span><span class="sxs-lookup"><span data-stu-id="2b653-161">You can use this in conjunction with the "Allow specific extensions to be installed" policy to only allow certain extensions to be installed.</span></span> <span data-ttu-id="2b653-162">На следующем снимке экрана показано расширение, которое будет заблокировано на основе указанного идентификатора приложения.</span><span class="sxs-lookup"><span data-stu-id="2b653-162">The next screenshot shows an extension that will be blocked based on the app ID that's provided.</span></span>

   :::image type="content" source="media/microsoft-edge-manage-extensions-policies/manage-extensions-gp-block-2.png" alt-text="Чтобы заблокировать расширение, используйте идентификатор приложения.":::

   > [!TIP]
   > <span data-ttu-id="2b653-164">Если вы не можете найти идентификатор приложения для расширения, посмотрите на расширение на веб-сайте надстроек Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="2b653-164">If you can’t find the app ID of an extension, look at the extension in the Microsoft Edge Add-ons website.</span></span> <span data-ttu-id="2b653-165">Найдите определенное расширение, и вы увидите идентификатор приложения в конце URL-адреса в омнибоксе.</span><span class="sxs-lookup"><span data-stu-id="2b653-165">Find the specific extension and you will see the app ID at the end of the URL in the omnibox.</span></span>

> [!NOTE]
> <span data-ttu-id="2b653-166">Вы можете добавить расширение в список заблокированных, который уже установлен на компьютере пользователя.</span><span class="sxs-lookup"><span data-stu-id="2b653-166">You can add an extension to the blocklist that’s already installed on a user’s computer.</span></span> <span data-ttu-id="2b653-167">Это отключит расширение и запретит пользователю повторно включить его.</span><span class="sxs-lookup"><span data-stu-id="2b653-167">This will disable the extension and prevent the user from re-enabling it.</span></span> <span data-ttu-id="2b653-168">Оно не будет удалено, а просто будет отключено.</span><span class="sxs-lookup"><span data-stu-id="2b653-168">It won't be uninstalled, just disabled.</span></span>

## <a name="force-install-an-extension"></a><span data-ttu-id="2b653-169">Принудительная установка расширения</span><span class="sxs-lookup"><span data-stu-id="2b653-169">Force-install an extension</span></span>

<span data-ttu-id="2b653-170">Чтобы управлять блокировкой и разрешением расширений, используйте политику [ExtensionInstallForcelist](/DeployEdge/microsoft-edge-policies#extensioninstallforcelist).</span><span class="sxs-lookup"><span data-stu-id="2b653-170">Use the [ExtensionInstallForcelist](/DeployEdge/microsoft-edge-policies#extensioninstallforcelist) policy to control which extensions are blocked or allowed.</span></span> <span data-ttu-id="2b653-171">Используйте следующие действия в качестве руководства для принудительной установки расширения.</span><span class="sxs-lookup"><span data-stu-id="2b653-171">Use the following steps as a guide to force-install an extension.</span></span>

1. <span data-ttu-id="2b653-172">В редакторе групповых политик перейдите в раздел **Административные шаблоны > Microsoft Edge > Расширения**, а затем выберите **Определение автоматически устанавливаемых расширений**.</span><span class="sxs-lookup"><span data-stu-id="2b653-172">In the Group Policy Editor, go to **Administrative Templates> Microsoft Edge >  Extensions >** and then select **Control which extensions are installed silently**.</span></span>
2. <span data-ttu-id="2b653-173">Выберите **Включено**.</span><span class="sxs-lookup"><span data-stu-id="2b653-173">Select **Enabled**.</span></span>  
3. <span data-ttu-id="2b653-174">Щелкните **Показать**.</span><span class="sxs-lookup"><span data-stu-id="2b653-174">Click **Show**.</span></span>
4. <span data-ttu-id="2b653-175">Введите идентификатор приложения или идентификаторы для расширения или расширений, которые необходимо установить принудительно.</span><span class="sxs-lookup"><span data-stu-id="2b653-175">Enter the app ID or IDs of the extension or extensions you want to force-install.</span></span>  

<span data-ttu-id="2b653-176">Расширение будет установлено автоматически без необходимости взаимодействия с пользователем.</span><span class="sxs-lookup"><span data-stu-id="2b653-176">The extension will be installed silently with no need for user interaction.</span></span> <span data-ttu-id="2b653-177">Пользователь также не сможет удалить или отключить расширение.</span><span class="sxs-lookup"><span data-stu-id="2b653-177">The user also won’t be able to uninstall or disable the extension.</span></span> <span data-ttu-id="2b653-178">Этот параметр переопределяет любую включенную политику списка блокировки.</span><span class="sxs-lookup"><span data-stu-id="2b653-178">This setting will overwrite over any blocklist policy that’s enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="2b653-179">Для расширений из интернет-магазина Chrome используйте строку `pckdojakecnhhplcgfflhndiffaohfah;https://clients2.google.com/service/update2/crx`.</span><span class="sxs-lookup"><span data-stu-id="2b653-179">For extensions hosted in the Chrome web store use a string such as: `pckdojakecnhhplcgfflhndiffaohfah;https://clients2.google.com/service/update2/crx`.</span></span>

## <a name="block-extensions-from-a-specific-store-or-update-url"></a><span data-ttu-id="2b653-180">Блокировка расширений из определенного магазина или URL-адреса обновления</span><span class="sxs-lookup"><span data-stu-id="2b653-180">Block extensions from a specific store or update URL</span></span>

<span data-ttu-id="2b653-181">Чтобы заблокировать расширения из определенного магазина или URL-адреса, необходимо заблокировать *update_url* для этого магазина с помощью политики [ExtensionSettings](/deployedge/microsoft-edge-policies#extensionsettings).</span><span class="sxs-lookup"><span data-stu-id="2b653-181">To block extensions from a particular store or URL, you only need to block the *update_url* for that store using the [ExtensionSettings](/deployedge/microsoft-edge-policies#extensionsettings) policy.</span></span>

<span data-ttu-id="2b653-182">Используйте следующие действия в качестве руководства для блокировки расширений из определенного магазина или URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="2b653-182">Use the following steps as a guide to block extensions from an particular store or URL.</span></span>

1. <span data-ttu-id="2b653-183">Откройте редактор управления групповыми политиками и перейдите в раздел **Административные шаблоны > Microsoft Edge > Расширения**, а затем выберите **Настройки управления расширениями**.</span><span class="sxs-lookup"><span data-stu-id="2b653-183">Open the group policy management editor and go to **Administrative Templates > Microsoft Edge > Extensions >** and then select **Configure extension management settings**.</span></span>  
2. <span data-ttu-id="2b653-184">Включите политику, а затем введите разрешения, которые нужно разрешить или заблокировать, сжав их в одной строке JSON.</span><span class="sxs-lookup"><span data-stu-id="2b653-184">Enable the policy, then enter the permissions that you want allowed or blocked, compressing it to a single JSON string.</span></span>

<span data-ttu-id="2b653-185">В следующем примере показан формат JSON и сжатая строка JSON для блокировки из интернет-магазина Chrome с помощью URL-адреса обновления (`https://clients2.google.com/service/update2/crx`).</span><span class="sxs-lookup"><span data-stu-id="2b653-185">The next example shows the JSON and compressed JSON string to block from the Chrome Web Store using its update URL (`https://clients2.google.com/service/update2/crx`).</span></span>

### <a name="json-example-for-blocking-on-update-url"></a><span data-ttu-id="2b653-186">Пример JSON для блокировки по URL-адресу обновления</span><span class="sxs-lookup"><span data-stu-id="2b653-186">JSON example for blocking on update URL</span></span>

```json
{ 
"update_url:https://clients2.google.com/service/update2/crx":{ 
                                                             " installation_mode":"blocked" 
                                                             } 
} 
```

```json
{"update_url:https://clients2.google.com/service/update2/crx":{"installation_mode":"blocked"}} 
```

> [!NOTE]
> <span data-ttu-id="2b653-187">Вы по-прежнему можете использовать **ExtensionInstallForceList** и **ExtensionInstallAllowList**, чтобы разрешить или принудить установить определенные расширения, даже если магазин заблокирован с помощью формата JSON в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="2b653-187">You can still use **ExtensionInstallForceList** and **ExtensionInstallAllowList** to allow/force install specific extensions even if the store is blocked using the JSON in the previous example.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b653-188">См. также</span><span class="sxs-lookup"><span data-stu-id="2b653-188">See also</span></span>

- [<span data-ttu-id="2b653-189">Управление расширениями Microsoft Edge на предприятии</span><span class="sxs-lookup"><span data-stu-id="2b653-189">Manage Microsoft Edge extensions in the enterprise</span></span>](microsoft-edge-manage-extensions.md)
- [<span data-ttu-id="2b653-190">Создание интернет-магазина для размещения расширений Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2b653-190">Create a web store to host Microsoft Edge extensions</span></span>](microsoft-edge-manage-extensions-webstore.md)
- [<span data-ttu-id="2b653-191">Справочное руководство по политике ExtensionSettings</span><span class="sxs-lookup"><span data-stu-id="2b653-191">Reference guide for the ExtensionSettings policy</span></span>](microsoft-edge-manage-extensions-ref-guide.md)
- [<span data-ttu-id="2b653-192">Вопросы и ответы по расширениям Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2b653-192">FAQ for Microsoft Edge Extensions</span></span>](microsoft-edge-manage-extensions-faq.md)
- [<span data-ttu-id="2b653-193">Целевая страница Microsoft Edge Enterprise</span><span class="sxs-lookup"><span data-stu-id="2b653-193">Microsoft Edge Enterprise landing page</span></span>](https://aka.ms/EdgeEnterprise)
