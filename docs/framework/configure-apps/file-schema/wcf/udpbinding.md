---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 95ce89aabb400c01002799fd8251383a2e5dd4c2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732706"
---
# <a name="udpbinding"></a><span data-ttu-id="50e51-101">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="50e51-101">\<udpBinding></span></span>
<span data-ttu-id="50e51-102">Prvek konfigurace, který slouží ke konfiguraci vazby <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="50e51-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
<span data-ttu-id="50e51-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="50e51-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="50e51-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="50e51-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="50e51-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="50e51-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="50e51-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpBinding >**</span><span class="sxs-lookup"><span data-stu-id="50e51-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e51-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50e51-107">Syntax</span></span>  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50e51-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="50e51-108">Attributes and Elements</span></span>  
 <span data-ttu-id="50e51-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="50e51-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50e51-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="50e51-110">Attributes</span></span>  
  
|<span data-ttu-id="50e51-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="50e51-111">Attribute</span></span>|<span data-ttu-id="50e51-112">Popis</span><span class="sxs-lookup"><span data-stu-id="50e51-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="50e51-113">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="50e51-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="50e51-114">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="50e51-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="50e51-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="50e51-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="50e51-116">Celočíselná hodnota, která určuje duplicitní délku historie zprávy.</span><span class="sxs-lookup"><span data-stu-id="50e51-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="50e51-117">Celočíselná hodnota, která určuje maximální velikost paměti, která je přidělena pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z kanálu.</span><span class="sxs-lookup"><span data-stu-id="50e51-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="50e51-118">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="50e51-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="50e51-119">Celočíselná hodnota, která určuje maximální velikost vyrovnávací paměti v bajtech, která ukládá zprávy, když jsou zpracovávány pro koncový bod nakonfigurovaný pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="50e51-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="50e51-120">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="50e51-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="50e51-121">Celočíselná hodnota, která určuje maximální počet zpráv, které byly přijaty, ale nebyly dosud odebrány ze vstupní fronty pro jednotlivou instanci kanálu.</span><span class="sxs-lookup"><span data-stu-id="50e51-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="50e51-122">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlaviček, pro zprávu, která se dá přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="50e51-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="50e51-123">Odesilatel obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká.</span><span class="sxs-lookup"><span data-stu-id="50e51-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="50e51-124">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="50e51-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="50e51-125">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="50e51-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="50e51-126">Celočíselná hodnota, která určuje maximální počet znovu odeslaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="50e51-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="50e51-127">Celočíselná hodnota, která určuje ID rozhraní vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="50e51-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="50e51-128">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="50e51-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="50e51-129">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="50e51-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="50e51-130">Každá vazba má atribut `name` a `namespace`, který ji společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="50e51-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="50e51-131">Kromě toho je tento název jedinečný mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="50e51-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="50e51-132">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="50e51-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="50e51-133">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="50e51-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="50e51-134">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="50e51-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="50e51-135">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="50e51-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="50e51-136">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="50e51-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="50e51-137">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="50e51-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="50e51-138">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="50e51-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="50e51-139">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="50e51-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="50e51-140">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="50e51-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="50e51-141">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="50e51-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="50e51-142">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="50e51-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="50e51-143">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="50e51-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="50e51-144">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="50e51-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="50e51-145">-BigEndianUnicode: kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="50e51-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="50e51-146">-Unicode: 16 bitů kódování.</span><span class="sxs-lookup"><span data-stu-id="50e51-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="50e51-147">-UTF8:8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="50e51-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="50e51-148">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="50e51-148">The default is UTF8.</span></span> <span data-ttu-id="50e51-149">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="50e51-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="50e51-150">Hodnota TimeSpan, která určuje dobu, po kterou má být tato vazba živá.</span><span class="sxs-lookup"><span data-stu-id="50e51-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50e51-151">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="50e51-151">Child Elements</span></span>  
  
|<span data-ttu-id="50e51-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="50e51-152">Element</span></span>|<span data-ttu-id="50e51-153">Popis</span><span class="sxs-lookup"><span data-stu-id="50e51-153">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50e51-154">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="50e51-154">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="50e51-155">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="50e51-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="50e51-156">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="50e51-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="50e51-157">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="50e51-157">Parent Elements</span></span>  
  
|<span data-ttu-id="50e51-158">Prvek</span><span class="sxs-lookup"><span data-stu-id="50e51-158">Element</span></span>|<span data-ttu-id="50e51-159">Popis</span><span class="sxs-lookup"><span data-stu-id="50e51-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50e51-160">vazby\<</span><span class="sxs-lookup"><span data-stu-id="50e51-160">\<bindings></span></span>](bindings.md)|<span data-ttu-id="50e51-161">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="50e51-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e51-162">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50e51-162">Remarks</span></span>  
 <span data-ttu-id="50e51-163">UdpBinding umožňuje službám WCF komunikovat přes přenos UDP.</span><span class="sxs-lookup"><span data-stu-id="50e51-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="50e51-164">Umožňuje výměnu zpráv typu "oheň a zapomenout", kde klient odesílá zprávu službě a neočekává zpětnou odezvu.</span><span class="sxs-lookup"><span data-stu-id="50e51-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50e51-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="50e51-165">Example</span></span>  
 <span data-ttu-id="50e51-166">Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.UdpBinding> pomocí elementu <`udpBinding`>.</span><span class="sxs-lookup"><span data-stu-id="50e51-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="50e51-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50e51-167">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="50e51-168">Vazby</span><span class="sxs-lookup"><span data-stu-id="50e51-168">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="50e51-169">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="50e51-169">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="50e51-170">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="50e51-170">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="50e51-171">vazba \<</span><span class="sxs-lookup"><span data-stu-id="50e51-171">\<binding></span></span>](bindings.md)
