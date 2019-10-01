---
title: <mailSettings> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: fb4c8844ed3eb13af483c214d659090c0c563c33
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698081"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="ae34a-102">@no__t – element > 0mailSettings (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="ae34a-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="ae34a-103">Nakonfiguruje možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="ae34a-103">Configures mail sending options.</span></span>  

[<span data-ttu-id="ae34a-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="ae34a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ae34a-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ae34a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="ae34a-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<mailSettings >**</span><span class="sxs-lookup"><span data-stu-id="ae34a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae34a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae34a-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae34a-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ae34a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ae34a-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ae34a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae34a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ae34a-110">Attributes</span></span>  
 <span data-ttu-id="ae34a-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae34a-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ae34a-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ae34a-112">Child Elements</span></span>  
  
|<span data-ttu-id="ae34a-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="ae34a-113">Attribute</span></span>|<span data-ttu-id="ae34a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ae34a-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="ae34a-115">@no__t – element > 1smtp (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="ae34a-115">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="ae34a-116">Nakonfiguruje možnosti jednoduchého poštovního transportního protokolu.</span><span class="sxs-lookup"><span data-stu-id="ae34a-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae34a-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ae34a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ae34a-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="ae34a-118">**Element**</span></span>|<span data-ttu-id="ae34a-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="ae34a-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ae34a-120">@no__t – element .NET > 1System (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="ae34a-120">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="ae34a-121">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="ae34a-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ae34a-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae34a-122">Example</span></span>  
 <span data-ttu-id="ae34a-123">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="ae34a-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae34a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae34a-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="ae34a-125">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="ae34a-125">Network Settings Schema</span></span>](index.md)
